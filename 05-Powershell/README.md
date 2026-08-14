# PowerShell Automation

## Overview

This section documents PowerShell automation used to perform operational and security checks against the Azure environment.

The objective is to reduce repetitive manual checks and provide a consistent method for retrieving and evaluating Azure resource configurations.

## Automation Approach

The PowerShell implementation follows a read-first approach.

Scripts initially retrieve and evaluate configuration information before introducing automated remediation.

## Scripts

### Get-StorageSecurityStatus.ps1

Retrieves relevant security configuration information from the Azure Storage Account.

The script checks information such as:

* Storage Account name
* Resource group
* Location
* SKU
* Minimum TLS version
* Secure transfer configuration
* Anonymous Blob access
* Authentication configuration

### Test-StorageCompliance.ps1

Evaluates selected Storage Account security configurations against defined requirements.

Example checks include:

* TLS version
* Secure transfer
* Anonymous access
* Security configuration

The script reports each check as:

**PASS / FAIL / REVIEW**

## Automation Process

The scripts follow:

**Retrieve → Evaluate → Report**

The results can then be used to support:

* Security assessments
* Compliance checks
* Operational reviews
* Vulnerability management
* Documentation

## Future Improvements

Future automation can include:

* Exporting results to CSV
* Generating compliance reports
* Scheduling recurring checks
* Integrating results with monitoring
* Automating approved remediation actions

## Outcome

The PowerShell implementation demonstrates the use of scripting to improve consistency, reduce manual operational work, and support Azure security and compliance activities.

