# Getting Started with CloudFormation
## Issues that DevOps tries to solve:
  - Unpredictable deployments
  - Mismatched environments (development doesn’t match production)
  - Configuration Drift
## DevOps gives best practices and tools for solving these problems:
  - DevOps Tools: DevOp tools deploy and manage configuration changes to servers.
    - [Stackexchange](https://softwareengineering.stackexchange.com/questions/130850/difference-between-devops-and-software-configuration-management) has a discussion post detailing the difference between DevOps tools vs. Software Configuration Tools
  - Allows for predictable deployments, because it’s an automated script.
  - Enables **Continuous Integration Continuous Deployment (CI/CD)** so that new features are automatically deployed with all the required dependencies.
  
## Glossary
  - **Continuous Integration Continuous Deployment (CI/CD):** Tracks the development workflow from testing through production. Continuous integration is process flow of testing any change made to your development flow, while continuous deployment tracks those changes through to staging and production systems.
    - Check out this article by [Atlassian.com](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment) that describes these in detail.
    - This article by [Florian Matlik](https://css-tricks.com/continuous-integration-continuous-deployment/) describes the differences between continuous integration and continuous deployment. 
  - **CloudFormation:** CloudFormation is a tool in AWS for managing, configuring and deploying infrastructure (push code along with the necessary server configurations).
  
## Deciding Access Privileges within AWS
### Programmatic Access
In the AWS console, choose "**programmatic access.**" This allows us to use code to interact with AWS, instead of relying on mouse clicking in the console web pages.
### Administrator Access
For IAM access, choose “**administrator access.**” This is just for initial setup of your account. Afterwards, you’ll want to limit access to only what you need.
### Dev and Prod user accounts
In practice, Dev and DevOps members may have separate user accounts for the dev environment as opposed to the production environment. This makes it easier for developers by giving them wider privileges in the dev environment that would normally only be reserved for DevOps members in the production environment.
### Access Key ID and Secret Access Keys
Remember not to save these in your code or to check into any repositories. Keep these private to you.

## Configuring the AWS Command Line Interface (CLI)
  - Download and install the AWS CLI tool.
  - In the terminal, type `aws --version`: this verifies that you have the AWS CLI tool.
  - To set up your AWS CLI, type `aws configure` in the terminal. Next when prompted for the AWS Access Key ID, paste in your `Secret access key`.
  - Region: Please use `us-west-2`, even if you’re living closer to another available region.
## Verifying your Setup
  - One way to check if your AWS CLI is set up properly is to try a command. You can try listing your S3 buckets:`aws s3 ls` . **This will be blank if you have no S3 buckets**. However, if you have no error message, then you’ve verified that your user has API access to communicate with AWS.
  - Note that each user can have up to 2 access keys at the same time.
### Why Making Keys Inactive is a Better Choice
You may make your access key temporarily inactive rather than destroying it and creating a new one. This may be helpful if you want to stop an automated process that uses that key (for example, a CI/CD process).

## CloudFormation
  - CloudFormation is a declarative language, not an imperative language. 
  - CloudFormation handles resource dependencies, so that you don’t have to specify which resource to start up before another. There are cases where you can specify that a resource depends on another resource, but ideally, you’ll let CloudFormation take care of dependencies.
  - VPC is the smallest unit of resource.
## Glossary
**Declarative languages:** These languages specify what you want, without requiring you to specify how to get it. An example of a popular declarative language is SQL.

**Imperative languages:** These languages use statements to change the state of the program.

*Additional resources:*
  - Here is the [Wikipedia](https://en.wikipedia.org/wiki/Imperative_programming) page describing the differences between the two.
  - Here is a [Stack Overflow](https://stackoverflow.com/questions/17826380/what-is-difference-between-functional-and-imperative-programming-languages) thread describing imperative languages.
  
## YAML and JSON
  - YAML and JSON file formats are both supported in CloudFormation, but YAML is the industry preferred version that’s used for AWS and other cloud providers (Azure, Google Cloud Platform).
  - An important note about YAML files: the whitespace indentation matters!  We recommend that you use **four white spaces for each indentation**.
## Glossary in CloudFormation scripts
**Name**: A name you want to give to the resource (does this have to be unique across all resource types?)


**Type**: Specifies the actual hardware resource that you’re deploying.


**Properties**: Specifies configuration options for your resource.  Think of these as all the drop down menus and checkbox options that you would see in the AWS console if you were to request the resource manually.


**Stack**: A stack is a group of resources.  These are the resources that you want to deploy, and that are specified in the YAML file.
## Best practices
**Coding best practice:** Create separate files to organize your code.  You can either create separate files for similar resources, or create files for each developer who uses those resources.
## Documentation for CloudFormation syntax
You don't need to memorize the code that you need for each resource.  You can find sample code in the [documentation for CloudFormation](https://docs.aws.amazon.com/index.html) for examples of how to write your CloudFormation scripts.

## How to run CloudFormation
  - For this example, we’ll assume your CloudFormation file name is called `testcfn.yml`, and you’re giving your stack the name `myfirsttest`.
  - In the terminal, to use your yml code to request the resources, type the following in the same directory as your yml file:
```
aws cloudformation create-stack 
--stack-name myfirsttest 
--region us-west-2 
--template-body testcfn.yml
```
  - You may also want to use `update-stack` when you want to update an existing stack instead of destroying your stack and creating a new one.
  
  
  
  
