# SAP on AWS - Rise with SAP Connectivity
The following diagrams provide an overview of options for connectivity to RISE with SAP VPC.

Reference: https://docs.aws.amazon.com/sap/latest/general/connectivity-rise.html#rise-connection-peering

## Connectivity between AWS Accounts
The following two options are available to connect your AWS account with AWS account managed by SAP on the third layer.
Option 1 - Amazon VPC Peering
Option 2 - AWS Transit Gateway

### Amazon VPC Peering

VPC peering is one-on-one connection between VPCs, and is not transitive. Traffic cannot transit from one VPC to another via an intermediary VPC. You must setup multiple peering connections to establish direct communication between RISE with SAP VPC and multiple VPCs. 

VPC peering works across AWS Regions. All inter-Region traffic is encrypted with no single point of failure or bandwidth bottleneck. Traffic stays on AWS Global Network and never traverses the public internet, reducing threats of common exploits and DDos attacks. Traffic is encrypted using AES-256 encryption at the virtual network layer.

Data transfer for VPC peering within an Availability Zone is free, and for across Availability Zones is charged per-GB.

![VPC Peering](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/e29dd624-93bc-4057-aab5-e41008beb7d9)




