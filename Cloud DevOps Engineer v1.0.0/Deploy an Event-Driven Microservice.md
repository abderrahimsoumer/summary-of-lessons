# Functions as a Service (FaaS)

## What is AWS Lambda?
From the [documentation](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html):

AWS Lambda is a compute service that lets you run code without provisioning or managing servers. 
  - AWS Lambda executes your code only when needed and scales automatically, from a few requests per day to thousands per second. 
  - You pay only for the compute time you consume - there is no charge when your code is not running.
You can use AWS Lambda to run your code in response to events, such as HTTP requests.
## SQS Queue
Amazon Simple Queue Service (Amazon SQS) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components.
  - A queue is just a type of list that orders data in a particular way; typically in a first-item-in = first-item-out order (FIFO)
Learn more about SQS in the [documentation](https://aws.amazon.com/sqs/).
## MXNet and Lambda
  - Learn more about deploying models using MXNet and AWS Lambda in this [AWS blog post](https://aws.amazon.com/blogs/compute/seamlessly-scale-predictions-with-aws-lambda-and-mxnet/), where they link to a repository of example code!
## Models for Serverless
Though we'll be using AWS cloud tools, there are a number of other providers that you can use to build serverless applications with auto-scaling capabilities. The skills you learn in this lesson will be widely applicable to these other platforms. Some of the larger, cloud providers include: 
  - Amazon Web Services [ [Chalice](https://github.com/aws/chalice) & [Cloud Formation](https://aws.amazon.com/cloudformation/)]
  - Terraform
  - Google Cloud Platform
  - Microsoft Azure
And you are welcome to check these out, especially if you have a platform that you already prefer.
## Lesson Outline
In this lesson, you'll learn to deploy serverless applications, using **AWS Lambda**. This lesson breaks up the topic of serverless applications into smaller concepts:
  - What are Functions as a Service (FaaS)?
  - Characteristics of cloud-native applications
  - Creating an AWS Lambda function using Cloud9
  - Responding to events, such as HTTP **requests**
  - Creating a JSON **response**
![request-response cycle](./img/screen-shot-2019-05-26-at-9.08.33-pm.png)  
## Request-Response
Much of this lesson will rely on creating and understanding the **request-response** method of computer communication. From the Wikipedia page:

**Request–response** is one of the basic methods computers use to communicate with each other, in which the first computer sends a request for some data and the second responds to the request. Usually, there is a series of such interchanges until the complete message is sent; browsing a web page is an example of request–response communication. 

**Request–response can be seen as a telephone call, in which someone is called and they answer the call.**

In this lesson, requests are typically HTTP requests with some input data, and a response will be a JSON-formatted set of output values. 
## Reflect
### QUESTION: 
What is the main benefit of FaaS? (There are multiple ways to answer this question; think about the features that FaaS have.)
### ANSWER:
There are a few main benefits of FaaS. You may have thought about one of the following attributes:
  - Complete abstraction of servers away from the developer.
  - Cost-effective. There is billing on-demand; based on consumption and executions.
  - Services that are event-driven and instantaneously scalable.
## Relational Database
A [relational database](https://en.wikipedia.org/wiki/Relational_database) is a tabular system that stores a finite amount of information. You can think of a relational database as a spreadsheet of values/data, where each row in the spreadsheet has a unique ID. 
## What is Fault-Tolerance?
**Fault tolerance** - the property that enables a system to continue operating properly in the event of the failure of one or more of its components. 
  - An example is a typical car, which is designed so it will continue to be drivable if one of the tires is punctured or damaged.
  - In computer systems, a fault-tolerant design enables a system to continue its intended operation, possibly at a reduced level, rather than failing completely, when some part of the system fails.
  
  
  
