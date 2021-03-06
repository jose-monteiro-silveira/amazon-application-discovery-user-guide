# Troubleshooting the Discovery Connector<a name="agentless-troubleshooting"></a>

This section contains topics that can help you troubleshoot known issues with Application Discovery Service\.

## Fixing Unhealthy Connectors<a name="fixing-unhealthy-connectors"></a>

Health information for every Discovery Connector can be found in the [Data Collectors](https://console.aws.amazon.com/migrationhub/discover/datacollectors?type=connector) page of the Migration Hub console\. You can identify connectors with problems by finding any connectors with a **Health** status of **Unhealthy**\. The following procedure outlines how to access the connector console to identify health issues\.

**Access a connector console**

1. Open the Migration Hub console in a web browser, and choose **Data Collectors** from the left hand navigation\.

1. From the **Connectors** tab, make a note of the **IP address** for each connector that has a health status of **Unhealthy**\.

1. Open a browser on any computer that can connect to the connector VM, and enter the URL of the connector console, `https://ip_address_of_connector`, where `ip_address_of_connector` is the IP address of an unhealthy connector\.

1. Enter the connector management console password, which was set up when the connector was configured\.

Once you've accessed the connector console, you can take actions to resolve an unhealthy status\. Here you can choose **View Info** for **vCenter connectivity**, and you'll get a dialog box with a diagnostic message\. The **View Info** link is only available on connectors that are version 1\.0\.3\.12 or later\.

After correcting the health issues, the connector will re\-establish connectivity with vCenter server, and the connector's status will change to the **HEALTHY** state\. If the issues persist, contact [AWS Support](https://aws.amazon.com/contact-us/)\.

The most common causes for unhealthy connectors are IP address issues and credentials issues\. The following sections can help you resolve these issues and return a connector to a healthy state\. 

**Topics**
+ [IP Address Issues](#vcenter-ip-issues)
+ [Credentials Issues](#vcenter-credentials-issues)

### IP Address Issues<a name="vcenter-ip-issues"></a>

A connector can go into an unhealthy state if the vCenter endpoint provided during connector setup is malformed, invalid, or if the vCenter server is currently down and not reachable\. In this case, when you choose **View Info** for **vCenter connectivity** you'll get a dialog box with the message "Confirm the operational status of your vCenter server, or choose Edit Settings to update the vCenter endpoint\."

The following procedure can help you resolve IP address issues\.

1. From the connector console \(`https://ip_address_of_connector`\), choose **Edit Settings**\.

1. From the left\-side navigation, choose **Step 5: Discovery Connector Set Up**\. 

1. From **Configure vCenter credentials**, make a note of the **vCenter Host** IP address\.

1. Using a separate commandline tool like `ping` or `traceroute`, validate that the associated vCenter server is active and the IP is reachable from the connector VM\.
   + If the IP address is incorrect and the vCenter service is active, then update the IP address in the connector console, and choose **Next**\.
   + If the IP address is correct but the vCenter server is inactive, activate it\.
   + If the IP address is correct and the vCenter server is active, check if it is blocking ingress network connections due to firewall issues\. If yes, update your firewall settings to allow incoming connections from the connector VM\.

### Credentials Issues<a name="vcenter-credentials-issues"></a>

Connectors can go into an unhealthy state if the vCenter user credentials provided during connector setup, are invalid, or do not have vCenter read and view account privileges\. In this case, when you choose **View Info** for **vCenter connectivity** you'll get a dialog box with the message "Choose Edit Settings to update your vCenter username and password for your account with read and view privileges\."

The following procedure can help you resolve credentials issues\. As a prerequisite, ensure that you have created a vCenter user that has read and view account permissions on vCenter server\.

1. From the connector console \(`https://ip_address_of_connector`\), choose **Edit Settings**\.

1. From the left\-side navigation, choose **Step 5: Discovery Connector Set Up**\. 

1. From **Configure vCenter credentials**, update the **vCenter Username** and **vCenter Password** by providing the credentials for a vCenter user with read and view permissions\.

1. Choose **Next** to complete setup\.

## Standalone ESX Host Support<a name="standalone-esx-host"></a>

The Discovery Connector does not support a standalone ESX host\. The ESX host must be part of the vCenter Server instance\.

## Getting Additional Support for Connector Issues<a name="additional-connector-support"></a>

If you encounter problems and need help, contact [AWS Support](https://aws.amazon.com/contact-us/)\. You will be contacted and may be asked to send the connector logs\. To obtain the logs, do the following:
+ Log back in to the AWS Agentless Discovery Connector console \(as you did during [configuration](configure-connector.md)\) and choose **Download log bundle**\.
+ Once the log bundle has finished downloading, send it as instructed by AWS Support\.