# SAP Web Dispatcher Architecture Patterns

Source: https://www.linkedin.com/pulse/sap-web-dispatcher-aws-architecture-patterns-luiz-machado-/?trackingId=AL0fRm0jTS201xfvoNZHiA%3D%3D

## Pattern 1 - SAP Web Dispatcher Architecture for Internal (Corporate Network) Requests
This diagram illustrates the architecture of a customer network connected to an AWS VPC through AWS Direct Connect. 

Request Flow:
An end-user sends an HTTP(s) request from the internal corporate network, which is connected to the AWS VPC via AWS Direct Connect.
The internal Application Load Balancer (ALB) receives the request and sends it to the respective Target Group.
The Target Group distributes the load among all SAP Web Dispatchers available (02 servers in this example).
The SAP Web Dispatcher which received the request forwards it to the SAP backend system by using Logon Groups for load balancing purposes in the SAP application layer.

## Pattern 2 - SAP Web Dispatcher Architecture for External (Public) Requests
This diagram illustrates an external request coming from the public internet.

Request Flow:
An end-user sends an HTTP(s) request from the public internet, and a DNS manager redirects the request to your external Application Load Balancer (ALB).
The external Application Load Balancer (ALB) receives the request and sends it to the respective Target Group.
The Target Group distributes the load among all SAP Web Dispatchers available (02 servers in this example).
The SAP Web Dispatcher which received the request forwards it to the SAP backend system by using Logon Groups for load balancing purposes in the SAP application layer.

## Pattern 3 - SAP Web Dispatcher Architecture for Internal and External Requests
This diagram illustrates the usage of the two previous first patterns together, where the customer receives requests from the corporate network and from the public internet.

## Pattern 4 - How Can I Optimize Resources and Costs (Without Neglecting Security)?
This diagram illustrates the usage of 02 Web Dispatchers in an additional private subnet called Web Layer and both, the internal and external Application Load Balancers, are forwarding the requests to the same Web Dispatchers, which are called hybrid (just because they receive different types of connections - internal and external).

## Pattern 5 - Using a Web Application Firewall to Handle External (Public) Requests
This diagram illustrates the usage of pattern 1 (internal requests) and pattern 2 (external requests) but now we include an additional security layer for the public requests: a Web Application Firewall.
