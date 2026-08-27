# Azure Environment Limitations and Workarounds

## 1. Overview

This project was implemented using an Azure for Students subscription. The student environment introduced limitations that affected some authentication and network access configurations during the implementation of the Azure Storage monitoring project.

Rather than changing the project scope or introducing additional resources, the implementation was adapted to the capabilities available within the student subscription.

---

## 2. Authentication Limitation

### Issue

During testing, uploading files to the Azure Blob container returned the following error:

> This request is not authorized to perform this operation.

The Storage Account had the following configuration:

- Storage Account: `stcloudopsportfolio`
- Container access: Private
- Storage account key access: Enabled
- Storage Blob Data Contributor: Available as an eligible assignment

The Microsoft Entra ID/PIM functionality required to activate the eligible data-plane role was not available in the student environment.

### Impact

The lack of usable Microsoft Entra/PIM functionality prevented the intended role-based Blob upload workflow from being used for the test.

---

## 3. Network Access Configuration

To continue testing the Storage Account without making the Blob container anonymously accessible, network access was restricted to the client IP address used for the project.

The Storage Account was configured to allow access from the selected IP address.

The Blob container remained:

**Private — no anonymous access**

Azure Storage supports restricting access to a public endpoint using specific IP address rules. Requests from sources outside the configured network boundary are denied. 

### Configuration

- Public network access: Enabled
- Network access: Restricted
- Allowed source: Project user's public IP address
- Blob container access: Private
- Anonymous public Blob access: Not used

This configuration allowed Blob operations from the authorized IP address while maintaining private container access.

---

## 4. Result

After the network restriction was configured, Blob uploads were successfully performed.

Test files were uploaded to the container to generate legitimate Storage Account activity for the monitoring test.

---

## 5. Monitoring Observation

During troubleshooting and testing, multiple interactions with the Blob Storage service generated transactions.

The Azure Monitor `Transactions` metric measures requests made to the Storage service and includes both successful and failed requests.

The repeated interactions therefore increased the transaction count and eventually exceeded the configured monitoring threshold.

The monitoring sequence was:

**Blob Storage activity**
→ **Transactions increased**
→ **Threshold exceeded**
→ **Azure Monitor alert triggered**
→ **Action Group notification received**

After the test files were deleted and activity decreased, the alert condition cleared.

Azure Monitor subsequently generated a resolution notification.

---

## 6. Alert Testing Result

The monitoring alert successfully demonstrated the complete alert lifecycle:

1. Storage Account activity was generated.
2. Transactions increased above the configured threshold.
3. Azure Monitor detected the condition.
4. The alert entered a fired state.
5. The configured Action Group sent an email notification.
6. Storage activity decreased.
7. The alert condition cleared.
8. A resolution email was received.

This confirmed that the monitoring and notification configuration was functioning as expected.

---

## 7. Lessons Learned

The implementation highlighted several operational considerations:

- Azure resource management permissions and Blob data permissions are separate.
- Storage Account network restrictions can affect data-plane operations.
- A private Blob container does not mean that the Storage Account must be inaccessible; network access can be restricted to approved sources.
- Azure Monitor's Transactions metric measures requests rather than simply successful file uploads.
- Troubleshooting activity can itself generate monitored transactions.
- Alert thresholds should be based on the expected workload and normal baseline activity.
- Testing an alert should account for all operations that may contribute to the monitored metric.

---

## 8. Project Limitation

The configuration implemented in this project reflects the capabilities of the Azure for Students environment.

The solution was selected to allow practical testing while maintaining a private Blob container and restricting network access to an approved source.

In a production environment, additional controls such as Microsoft Entra-based authorization, private endpoints, managed identities, and more granular network architecture could be considered based on organizational requirements.
