# AWS Agentless Discovery Connector<a name="discovery-connector"></a>

Agentless discovery uses the AWS Discovery Connector\. The AWS Discovery Connector is a VMware appliance that can collect information only about VMware virtual machines \(VMs\)\. You install the Discovery Connector as a VM in your VMware vCenter Server environment using an Open Virtualization Archive \(OVA\) file\. Because the Discovery Connector relies on VMware metadata to gather server information regardless of operating system, it minimizes the time required for initial on\-premises infrastructure assessment\.

Before you deploy the Discovery Connector, you must choose a [Migration Hub home region](https://docs.aws.amazon.com/migrationhub/latest/ug/home-region.html)\. You must register your connector in your home region\. After you deploy and configure the Discovery Connector, it registers with the Application Discovery Service endpoint, and pings the service at regular intervals, approximately every 60 minutes, for configuration information\.
+ If US West \(Oregon\) is your home region, it registers with ` https://arsenal.us-west-2.amazonaws.com/`\.
+ If Europe \(Frankfurt\) is your home region, it registers with `https://arsenal-discovery.eu-central-1.amazonaws.com`\.

**How it works**

When you start the connector's data collecting process, it connects to VMware vCenter Server where it collects information about all the VMs and hosts managed by this specific vCenter\. The collected data is sent to the Application Discovery Service using Secure Sockets Layer \(SSL\) encryption\. The connector is configured to upgrade automatically when new versions of the connector become available\. You can change this configuration setting at any time\. 

**Topics**
+ [Data Collected by the Discovery Connector](agentless-data-collected.md)
+ [Download the Discovery Connector](setting-up-agentless.md)
+ [Deploy the Discovery Connector](deploy-connector-appliance.md)
+ [Configure the AWS Discovery Connector](configure-connector.md)
+ [Start Discovery Connector Data Collection](start-connector-data-collection.md)
+ [Troubleshooting the Discovery Connector](agentless-troubleshooting.md)