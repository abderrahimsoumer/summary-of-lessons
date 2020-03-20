# Servers in the Cloud
Servers in the cloud have revolutionized the IT industry.

- Scale capacity up and down based on demands.
- Storage, more memory, and computing power can be added as needed.
- Obtain servers in minutes.
- No need for onsite hardware or capital expenses.

# Elastic Cloud Compute (EC2)
Elastic Cloud Compute or EC2 is a foundational piece of AWS' cloud computing platform and is a service that provides servers for rent in the cloud.

## Pricing Options
There are several pricing options for EC2.

- On Demand - Pay as you go, no contract.
- Dedicated Hosts - You have your own dedicated hardware and don't share it with others.
- Spot - You place a bid on an instance price. If there is extra capacity that falls below your bid, an EC2 instance is provisioned. If the price goes above your bid while the instance is running, the instance is terminated.
Reserved Instances - You earn huge discounts if you pay up front and sign a 1-year or 3-year contract.
## Tips
- EC2 is found under the Compute section of the AWS Management Console.

- Spot instances can save you up to 90% off the on-demand pricing.

- There are several instance types that provide varying combinations of CPU, memory, storage, and networking capacity.

# Elastic Block Store (EBS)

Elastic Block Store (EBS) is a storage solution for EC2 instances and is a physical hard drive that is attached to the EC2 instance to increase storage.
## Tips
- EBS is found on the EC2 Dashboard.
- There are several EBS volume types that fall under the categories of Solid State Drives (SSD) and Hard Disk Drives (HDD).

# Security
Security in the cloud allows you to have complete control over your virtual networking environment. 
- Configure your virtual network with public or private facing subnets
- Launch your servers in the selected network to secure access

# Virtual Private Cloud (VPC)
Virtual Private Cloud or VPC allows you to create your own private network in the cloud. You can launch services, like EC2, inside of that private network. A VPC spans all the Availability Zones in the region.

VPC allows you to control your virtual networking environment, which includes:
- IP address ranges
- subnets
- route tables
- network gateways
## Tips
- VPC is found under Networking & Content Delivery section of the AWS Management Console.
- The default limit is 5 VPCs per Region. You can request an increase for these limits.
- Your AWS resources are automatically provisioned in a default VPC.
- There are no additional charges for creating and using the VPC.
- You can store data in Amazon S3 and restrict access so that it’s only accessible from instances in your VPC.
