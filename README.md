# securex-orch-workflows

The SecureX Orchestration Workflows here templates to provide automated security alerting using Cisco Stealthwatch Cloud, Cisco Webex Teams and orchestrated security remediation using Cisco Defense Orchestrator. 

## External Port Scan Blocklist Workflow

**Prerequisites**
1. Cisco Stealthwatch Cloud (SWC) Account
2. Cisco Defense Orchestrator (CDO) Account
  * Network Object in CDO named **Global_Blocklist**
3. Cisco SecureX Account
4. Optional Cisco Webex Teams Account

**Workflow**

In this workflow we will reach out to SWC for Inbound Port Scan Alerts. Once we have the alert we will query SWC again for all the observations about that alert. We create a SecureX Orchestration Approval Request and a Webex Teams Alerts message. In the Webex Teams alert message there will be a redirect link to the SWC Alert page, SecureX Threat Response Investigation prepopulated with all the SWC observables, and the SecureX Orchestration Approval request. The next step is to automate adding the attacker IP address to a network object in CDO, then merging the network object into the Global_Blocklist network group.

## Stealthwatch Cloud - Webex Teams Alerts

**Prerequisites**
1. Cisco Stealthwatch Cloud (SWC) Account
2. Cisco SecureX Account
3. Cisco Webex Teams Account

**Workflow**

In this workflow we will reach out to SWC for all alerts. If there are any alerts, we will parse the Alert URL and add it to a Webex Teams message.

## SecureX Cloud Analytics Demo Workflow

**Prerequisites**
1. Cisco Stealthwatch Cloud (SWC) Account
2. Cisco SecureX Account
3. Cisco Webex Teams Account

**Workflow**

This workflow is very similar to the "Stealthwatch Cloud - Webex Teams Alerts" workflow. In this workflow we are creating a custom Webex Teams message for the **Inbound Port Scanner** alert, but also creating a generic alert message for all other Alert Types. The idea here is to get started with creating more detailed alerts messages for attacks that mean more to your organization, while still have the generic alerts for all others, until a customized message is needed.
