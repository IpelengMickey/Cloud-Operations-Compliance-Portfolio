# Azure Monitoring

## Overview

This section documents the implementation of monitoring and alerting for the Azure environment.

The objective is to establish visibility into resource activity, identify operational events, and generate alerts when defined conditions occur.

## Implementation

The monitoring implementation uses Azure Monitor to provide visibility into the Azure Storage environment.

### Components

* Azure Monitor
* Azure Activity Log
* Storage Account metrics
* Alert rules
* Action Groups

## Activities

### Activity 1 — Configure Monitoring

Configure monitoring for the Azure Storage Account and review available metrics and activity logs.

### Activity 2 — Create Metric Alerts

Create an alert rule based on a relevant Storage Account metric.

The alert includes:

* Target resource
* Monitoring signal
* Threshold
* Evaluation period
* Severity
* Action Group

### Activity 3 — Create Activity Log Alert

Configure an Activity Log alert to detect relevant administrative activity affecting the Azure environment.

### Activity 4 — Configure Notification

Create an Action Group and configure email notification for triggered alerts.

### Activity 5 — Test Alert

Perform the monitored activity or generate the required condition.

Verify:

1. The alert condition is detected.
2. Azure Monitor generates the alert.
3. The Action Group is triggered.
4. The notification is received.
5. The event can be investigated.

## Evidence

Evidence for this section includes:

* Monitoring configuration screenshots
* Metric alert configuration
* Activity Log alert configuration
* Triggered alert
* Notification received
* Alert investigation results

## Outcome

The monitoring implementation provides operational visibility into the Azure environment and demonstrates the process of detecting, investigating, and responding to cloud events.

