# SAP on AWS - Rise with SAP Connectivity
The following diagrams provide an overview of options for connectivity to RISE with SAP VPC.

Reference: https://docs.aws.amazon.com/sap/latest/general/connectivity-rise.html#rise-connection-peering

## Connectivity between AWS Accounts
The following two options are available to connect your AWS account with AWS account managed by SAP on the third layer.
* Option 1 - Amazon VPC Peering
* Option 2 - AWS Transit Gateway

### Amazon VPC Peering

VPC peering is one-on-one connection between VPCs, and is not transitive. Traffic cannot transit from one VPC to another via an intermediary VPC. You must setup multiple peering connections to establish direct communication between RISE with SAP VPC and multiple VPCs. 

VPC peering works across AWS Regions. All inter-Region traffic is encrypted with no single point of failure or bandwidth bottleneck. Traffic stays on AWS Global Network and never traverses the public internet, reducing threats of common exploits and DDos attacks. Traffic is encrypted using AES-256 encryption at the virtual network layer.

Data transfer for VPC peering within an Availability Zone is free, and for across Availability Zones is charged per-GB.

![SAP on AWS - RISE with SAP Connectivity-VPC Peering drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/c960d73c-ed4a-47c0-a1fb-528cad957390)


### AWS Transit Gateway

AWS Transit Gateway is a network transit hub to interconnect Amazon VPCs. It acts as a cloud router, resolving complex peering setup issues by acting as the central communication hub. You need to establish this connection with AWS account managed by SAP only once.

To establish connection with AWS account managed by SAP, create and share AWS Transit Gateway in your AWS account. SAP then creates an attachment to enable traffic flow through an entry in route table. As AWS Transit Gateway resides in your AWS account, you can retain control over traffic routing.

For cross-Region peering, connect AWS Transit Gateway in AWS account managed by SAP with AWS Transit Gateway in a different Region in your AWS account.

![SAP on AWS - RISE with SAP Connectivity-AWS Transit Gateway drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/ce88f8ca-7be1-4e32-90ae-a4b6ddcf21ce)








