# SAP Web Dispatcher Architecture Patterns

Source: https://www.linkedin.com/pulse/sap-web-dispatcher-aws-architecture-patterns-luiz-machado-/?trackingId=AL0fRm0jTS201xfvoNZHiA%3D%3D

## Pattern 1 - SAP Web Dispatcher Architecture for Internal (Corporate Network) Requests
This diagram illustrates the architecture of a customer network connected to an AWS VPC through AWS Direct Connect. 

![SAP on AWS - Webdispatcher Architecture Patterns-001 Only Int Webdisps drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/7ca64391-234f-4e22-9e20-37d320915caa)

Request Flow:
An end-user sends an HTTP(s) request from the internal corporate network, which is connected to the AWS VPC via AWS Direct Connect.
The internal Application Load Balancer (ALB) receives the request and sends it to the respective Target Group.
The Target Group distributes the load among all SAP Web Dispatchers available (02 servers in this example).
The SAP Web Dispatcher which received the request forwards it to the SAP backend system by using Logon Groups for load balancing purposes in the SAP application layer.

## Pattern 2 - SAP Web Dispatcher Architecture for External (Public) Requests
This diagram illustrates an external request coming from the public internet.

![SAP on AWS - Webdispatcher Architecture Patterns-002 Only Ext Webdisps drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/33412129-331a-4df6-bfde-2479a9acb097)

Request Flow:
An end-user sends an HTTP(s) request from the public internet, and a DNS manager redirects the request to your external Application Load Balancer (ALB).
The external Application Load Balancer (ALB) receives the request and sends it to the respective Target Group.
The Target Group distributes the load among all SAP Web Dispatchers available (02 servers in this example).
The SAP Web Dispatcher which received the request forwards it to the SAP backend system by using Logon Groups for load balancing purposes in the SAP application layer.

## Pattern 3 - SAP Web Dispatcher Architecture for Internal and External Requests
This diagram illustrates the usage of the two previous patterns together, where the customer receives requests from the corporate network and from the public internet.

![SAP on AWS - Webdispatcher Architecture Patterns-003 Int+Ext 04 Webdisps drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/a0861121-62c0-48a5-89d5-923dd4c38490)

## Pattern 4 - How Can I Optimize Resources and Costs (Without Neglecting Security)?
This diagram illustrates the usage of 02 Web Dispatchers in an additional private subnet called Web Layer and both, the internal and external Application Load Balancers, are forwarding the requests to the same Web Dispatchers, which are called hybrid (just because they receive different types of connections - internal and external).

![SAP on AWS - Webdispatcher Architecture Patterns-004 Int-Ext 02 Webdisps drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/4d1446d0-e8a9-410b-bb65-1ddf06611daa)

## Pattern 5 - Using a Web Application Firewall to Handle External (Public) Requests
This diagram illustrates the usage of pattern 1 (internal requests) and pattern 2 (external requests) but now we include an additional security layer for the public requests: a Web Application Firewall.

![SAP on AWS - Webdispatcher Architecture Patterns-005 Int+Ext 04 Webdisps + WAF drawio](https://github.com/luiz-machado-pt/sap-on-aws/assets/170890096/4bde5d78-200a-408c-9942-a11f4bd7793c)
