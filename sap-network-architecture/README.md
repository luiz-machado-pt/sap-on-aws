# SAP Network Architecture
Improve the security of your SAP landscape by implementing a Network Segmentation and Stop opening unnecessary ports and protocols.

## Network Segmentation
Network segmentation is an architecture that divides a computer network into smaller sections or subnets. 
Each network segment acts as its own network, which provides security teams with increased control over the traffic that flows into their systems.

## Basic Checklist
Ensure your firewall is properly configured and all rules are regularly audited and updated.
Secure remote access points and remote users.
Block any unnecessary network ports.
Disable and remove unused or extraneous protocols and services.
Encrypt network traffic.

## SAP Network Diagram
![SAP Network Architecture-SAP Network Ports](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/6460dea3-edd0-4d7a-a22b-8f34c3d9e3ea)

## References
* What is network segmentation? [link](https://www.fortinet.com/resources/cyberglossary/network-segmentation#:~:text=Segmentation%20is%20used%20to%20help,that%20flows%20into%20their%20systems.)
* Network hardening best practices [link](https://www.ninjaone.com/blog/complete-guide-to-systems-hardening/)




## Connectivity between AWS Accounts
The following two options are available to connect your AWS account with AWS account managed by SAP on the third layer.
* Option 1 - Amazon VPC Peering
* Option 2 - AWS Transit Gateway
