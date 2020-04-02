# RDS Databases
### Persisting Data
  - Most applications need their data to persist and not be lost, which requires a database.
  - We don't want a database to be a single point of failure, so we'll use resources that are designed for reliability. For example, RDS for the database, and S3 for the filestore.
  - Relational Database Service (RDS): AWS service for creating databases.
### Choosing a database
  - AWS Aurora and MySQL have no additional licensing costs. Microsoft SQL Server will have additional licensing costs.
### Mult-AZ deployment
  - If you are using a database in a development environment, you can save money by using a single Availability Zone.
  - For production databases, use multiple AZs for reliability. If one AZ fails, the other one will still be available.
### A single RDS Server can host multiple databases
  - Note that you can use a single RDS database that hosts multiple applications, each with different logins and users for those applications. In other words, you don’t need to create a separate RDS service for each application.
### Network and Security
  - Subnet groups are needed for deploying in multiple AZs. 
  - We want to place our RDS in more than one Availability Zone (data center). We can place the RDS in two AZs to eliminate single point of failure and to have high availability. 
  - We created 4 subnets (2 private and 2 public), so the RDS can potentially be duplicated in all four subnets. 
  - However, keep in mind that we usually prefer to put databases in a private subnet, for security. There may be use cases where you put a database in a public subnet, but generally put it in the private subnets.
### Usually, don't make a database public
  - We'll choose "No" for public accessibility" to keep a database private. 
  - We'd normally use a private IP address to access a database.
### AZ
  - Let AWS choose the availability zone. Choose "no preference."
### VPC Security Groups
**Default** means every resource in the VPC can talk to any other resource that is within that same VPC. We'll keep this default, to allow resources in the VPC to reach the database.
### Encryption
  - We can use encryption for sensitive production workloads. We can disable encryption for our database here.
### Using CloudFormation
  - Note that since setting up a database is usually a one-time event, you can just use the console (point and click) to create the database server instead of writing CloudFormation code. Using CloudFormation is still an option if you choose.
### CloudFormation retention policy
  - You'll want your data to persist even if your stack of resources is updated or deleted.
  - [Retention policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-attribute-deletionpolicy.html): keeps a service even if the entire stack of infrastructure is marked for removal. In CloudFormation, the syntax is `DeletionPolicy: retain`. This is very useful to assign to your data storage (database, file storage), to make sure that your data is saved even when the stack is updated or deleted.  
### When to use Filestores
  - Use filestores instead of databases for large files, such as videos and text documents.
  - Configuration files and sensitive encrypted data are best stored in specific filestores rather than inside the servers. Autoscaling groups may create or destroy servers, so keep data that you want to persist in separate resources such as a filestore.
### S3 bucket
  - Choose a DNS compliant name for the S3 bucket.
### Command line arguments
`aws s3 ls <link to S3 bucket>`


This line above lists files in the S3 bucket.

`aws s3 cp <file name> <link to S3 bucket>`

This line above copies a file from your local machine to the S3 bucket.
### Versioning
  - You can keep past versions of your S3 bucket, which means that deleted files will still exist in prior versions of your S3 bucket.
## Key Points
  - S3 can be used to store your config files, media or log files.
  - Your servers don't need credentials to access S3 provided they have a role assigned.
  - We recommend you choose RDS as opposed to installing a database in your own servers that you have to manage and back up yourself.  
  
  
