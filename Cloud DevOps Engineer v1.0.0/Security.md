# Security in the Cloud
As adoption of cloud services has increased, so has the need for increased security in the cloud. The great thing about cloud security is that it not only protects data, it also protects applications that access the data. Cloud security even protects the infrastructure (like servers) that applications run on.

The way security is delivered depends on the cloud provider you're using and the cloud security options they offer.

## AWS Shield
AWS Shield is a managed DDoS (or Distributed Denial of Service) protection service that safeguards web applications running on AWS. 

AWS Shield is a service that you get "out of the box", it is always running (automatically) and is a part of the free standard tier. If you want to use some of the more advanced features, you'll have to utilize the paid tier. 

### Tips
  - AWS Shield can be found under the Security, Identity, & Compliance section on the AWS Management Console.
  - AWS Shield Standard is always-on, using techniques to detect malicious traffic.
  - AWS Shield Advanced provides enhanced detection.

## AWS WAF
AWS WAF (or AWS Web Application Firewall) provides a firewall that protects your web applications. 

WAF can stop common web attacks by reviewing the data being sent to your application and stopping well-known attacks.
### Tips
  - WAF is found under the Security, Identity, & Compliance sectin on the AWS Managemen Console.
  - WAF can protect web sites not hosted in AWS through Cloud Front.
  - You can configure CloudFront to present a custom error page when requests are blocked.
  
## Identity & Access Management
Identity & Access Management (IAM) is an AWS service that allows us to configure who can access our AWS account, services, or even applications running in our account. IAM is a global service and is automatically available across ALL regions.
### Security Concepts
  - User
  - IAM Group
  - IAM Role
  - Policy



