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

[Download](https://github.com/luiz-machado-pt/sap-on-aws/blob/ad4699861d4979ab5568aaaa984e91b155934aaa/rise-with-sap-connectivity/SAP%20on%20AWS%20-%20RISE%20with%20SAP%20Connectivity-AWS%20Transit%20Gateway.drawio.xml)

## Connecting On-Premise to RISE with SAP using your AWS account
You can establish connectivity between on-premises and RISE with SAP VPC using you AWS account. This method provides you with more control but also requires managing AWS services in your AWS account. You can use any one of the following options:

* AWS Transit Gateway – Share AWS Transit Gateway resource in your AWS account with AWS account managed by SAP.
* AWS VPN with AWS Transit Gateway – Create an IPsec VPN connection between your remote network and transit gateway over the internet.
* Direct Connect gateway – Create a Direct Connect gateway with a transit or virtual private gateway.


The following image shows this option within the same AWS Region.

![SAP on AWS - RISE with SAP Connectivity-On-premise to AWS Transit Gateway - Same Region drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/986fee23-6f6e-43f6-a19c-a9e737d5a40e)

The following image shows this option across different AWS Regions.

![SAP on AWS - RISE with SAP Connectivity-On-premise to AWS Transit Gateway - Different Region drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/a09681a7-291c-4acb-838a-c1361d3d4f55)






