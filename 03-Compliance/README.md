# Azure Compliance

## Overview

This section documents the implementation of Azure Policy to monitor compliance with defined security and configuration requirements.

The objective is to identify non-compliant resources, investigate the cause, remediate the configuration, and verify compliance.

## Implementation

Azure Policy is used to evaluate the Azure environment against selected security controls.

The initial controls focus on Azure Storage security and configuration.

## Compliance Lifecycle

**Define Control → Assign Policy → Evaluate → Identify Non-Compliance → Remediate → Re-evaluate → Document**

## Activities

### Activity 1 — Define Compliance Controls

Identify security configurations that should be enforced or monitored.

Examples include:

* Secure transfer
* TLS configuration
* Anonymous access
* Authentication configuration
* Storage security settings

### Activity 2 — Assign Azure Policy

Assign relevant built-in Azure Policies to the appropriate resource group or subscription scope.

Initial policies should use **Audit** where appropriate so that compliance can first be assessed without blocking resources.

### Activity 3 — Review Compliance

Navigate to:

**Azure Policy → Compliance**

Review:

* Compliant resources
* Non-compliant resources
* Policy assignments
* Compliance percentage
* Policy evaluation details

### Activity 4 — Investigate Non-Compliance

Select a non-compliant resource and determine which configuration caused the failure.

### Activity 5 — Remediate

Update the Azure resource configuration to satisfy the required control.

### Activity 6 — Verify

Allow the policy to reevaluate the resource and confirm that the compliance status changes to compliant.

### Activity 7 — Document

Record:

* Policy
* Resource
* Compliance status
* Finding
* Remediation
* Verification result
* Evidence

## Outcome

The implementation demonstrates how Azure Policy can be used to continuously evaluate cloud resources against defined security and compliance requirements.

