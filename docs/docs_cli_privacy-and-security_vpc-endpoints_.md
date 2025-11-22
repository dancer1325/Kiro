# Kiro and interface endpoints (AWS PrivateLink) - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/privacy-and-security/vpc-endpoints/

---

You can establish a private connection between your VPC and Kiro by creating an interface VPC endpoint. Interface endpoints are powered by AWS PrivateLink, a technology that enables you to privately access Kiro APIs without an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection. Instances in your VPC don't need public IP addresses to communicate with Kiro APIs. Traffic between your VPC and Kiro does not leave the Amazon network.
Each interface endpoint is represented by one or more Elastic Network Interfaces in your subnets.
For more information, see Interface VPC endpoints (AWS PrivateLink) in the Amazon VPC User Guide.
Considerations for Kiro VPC endpoints
Before you set up an interface VPC endpoint for Kiro, ensure that you review Interface endpoint properties and limitations in the Amazon VPC User Guide.
Kiro supports making calls to all of its API actions from your VPC, in the context of services that are configured to work with Kiro.
Prerequisites
Before you begin any of the procedures below, ensure that you have the following:
An AWS account with appropriate permissions to create and configure resources.
A VPC already created in your AWS account.
Familiarity with AWS services, especially Amazon VPC and Kiro.
Creating an interface VPC endpoint for Kiro
You can create a VPC endpoint for Kiro using either the Amazon VPC console or the AWS Command Line Interface (AWS CLI). For more information, see Creating an interface endpoint in the Amazon VPC User Guide.
Create the following VPC endpoints for Kiro using the following service names:
com.amazonaws.us-east-1.q
com.amazonaws.us-east-1.codewhisperer
InfoKiro only supports Amazon Q Developer profiles in the US East (N. Virginia) Region.
Also, the Amazon CodeWhisperer endpoint (com.amazonaws.us-east-1.codewhisperer) is only supported in the US East (N. Virginia) Region.
If you enable private DNS for the endpoint, you can make API requests to Kiro using its default DNS name for the Region, for example, q.us-east-1.amazonaws.com.
For more information, see Accessing a service through an interface endpoint in the Amazon VPC User Guide.
Using an on-premises computer to connect to a Kiro endpoint
This section describes the process of using an on-premises computer to connect to Kiro through a AWS PrivateLink endpoint in your AWS VPC.
Create a VPN connection between your on-premises device and your VPC.
Create an interface VPC endpoint for Kiro.
Set up an inbound Amazon Route 53 endpoint. This will enable you to use the DNS name of your Kiro endpoint from your on-premises device.
Page updated: November 12, 2025Firewalls, proxies, and data perimetersCLI commands