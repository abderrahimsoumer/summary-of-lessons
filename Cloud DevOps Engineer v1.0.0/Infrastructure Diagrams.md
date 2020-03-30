# Diagrams
Diagrams are a very important starting point for planning your cloud infrastructure. DevOps engineers start with a visual representation of the required cloud infrastructure before they turn it into code. This lesson will show you how to interpret these infrastructure diagrams.

**Resources**

[Learn about architecting at scale](https://lethain.com/introduction-to-architecting-systems-for-scale/)

# Generalizable to AWS, Google Cloud Platform, Microsoft Azure
The diagrams and resources covered in this lesson are generalizable to other cloud providers (such as Azure and Google Cloud Platform).

### Lucidchart
We’ll use [Lucidchart](https://lucidchart.com/) to create cloud diagrams. Other applications that generate diagrams include Visio or Cloudcraft.

**Note to students:** You won’t need to know how to create diagrams for the project. The goal of this lesson is to get you familiar with cloud diagrams so that you can write cloud formation code based on interpreting the diagrams.

## Cloud Container
This represents your AWS account and all resources it can access.
## Region
A local business may be entirely contained in a region.

## Glossary
**Availability Zones (AZ):** An AZ is a data center (physical building). 
### Best Practices
  - Choose to have more than one availability zone to avoid a single point of failure.
  - Include more than one availability zone to design for high availability, . 
  - You may choose to reduce to one AZ, possibly for prototyping and design for low cost. But it is not recommended for production environments.
## Glossary
**Virtual Private Cloud (VPC):** A virtual private cloud is a pool of networked cloud resources. It can span more than one availability zone. 

The equivalent of this would be a data center. However, thanks to availability zones, VPCs can span more than one physical building. This is an amazing feature that protects against real world disasters like electrical failures, fires and similar events.

## Subnets
  - A subnet is a subset of the overall VPC network and it only exists in a single availability zone, unlike its parent network, the VPC. 
  - A subnet contains resources, and can be assigned access rights that apply to all resources within that subnet.
  - Subnets can be public or private. Public subnets are accessible to external users. Private subnets are only accessed internally by other resources within your cloud container.
## Use IP addresses for routing traffic
  - Use IP addresses as the “keys” for routing traffic. We can route traffic to stay within the VPC, or within a particular subnet, for security reasons.
  - For example, a database or any sensitive data will be placed in a private subnet. A public server, like a web server, can be placed in a public subnet. Routing rules applied to a subnet allow us to define access to all resources placed inside that subnet.
  
## Internet Gateway
  - An internet gateway is a resource that enables inbound and outbound traffic from the internet to your VPC. 
  - An internet gateway allows external users access to communicate with parts of your VPC. 
  - If you create a private VPC for an application that is internal to your company, you will not need an internet gateway.
  
Network Address Translation (NAT) Gateway: provides outbound-only internet gateway for private services to access the internet. This keeps the private service protected from inbound connections, but allows it to connect to the internet in order to perform functions such as downloading software updates. The NAT gateway serves as an intermediary to take a private resource’s request, connect to the internet, and then relay the response back to the private resource without exposing that private resource’s IP address to the public.

**Note:** Place NAT Gateways inside the **public** subnets and not the private subnets. NAT gateways need to be in the public subnet so that they can communicate with the public internet, and handle requests from resources that are in a private subnet.
  
## Glossary
**Autoscaling group:** An autoscaling group manages multiple instances of the same resource (for example, servers), based on need. For instance, when there is a lot of internet traffic to a site, the autoscaling group can start more servers. When there is less traffic, the autoscaling group can reduce the number of servers.
### Best Practice
  - It is recommended that an autoscaling group **spans more than one availability zone, for reliability**. 
  - If we set the autoscaling group to run one resource, it will run that one resource in one of the availability zones. 
  - If there is a failure of that resource, the autoscaling group will shut it down in that availability zone and start that same resource in the other availability zone.
  
## Load Balancer
  - A load balancer takes incoming traffic and distributes it to two or more resources. For example, it can take inbound user requests to access your website, and it can distribute the requests evenly among two or more servers.
  - Without a load balancer, having public-facing servers in more than one AZ would mean that users would have to use a different URL to reach each of the AZs. This can be impractical compared to just a single URL.

## Security Groups
  - Security groups manage traffic at the server level (the resource level). Security Groups aren’t for managing higher level groups such as subnets, VPC, or user accounts. 
  - The same security group can be assigned to multiple resources that require the same security access settings defined by that security group.
## S3
  - An S3 bucket is a public service for users to upload or download files. 
  - Place the S3 service **outside of your VPC.**
  
  
  
