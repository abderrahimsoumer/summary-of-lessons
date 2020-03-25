# Messaging in the Cloud
There are often times that users of your applications need to be notified when certain events happen. Notifications, such as text messages or emails can be sent through services in the cloud. The use of the cloud offers benefits like lowered costs, increased storage, and flexibility.

# Simple Notification Service
Amazon Simple Notification Service (or SNS) is a cloud service that allows you to send notifications to the users of your applications. SNS allows you to decouple the notification logic from being embedded in your applications and allows notifications to be published to a large number of subscribers. 
## Features
  - SNS uses a publish/subscribe model.
  - SNS can publish messages to Amazon SQS queues, AWS Lambda functions, and HTTP/S webhooks.
## Tips
  - SNS is found under the Application Integration section on the AWS Management Console.
  - SNS Topic names are limited to 256 characters.
  - A notification can contain only one message.

# Queues
A queue is a data structure that holds requests called messages. Messages in a queue are commonly processed in order, first in, first out (or FIFO). 

Messaging queues improve:
  - performance
  - scalability
  - user experience
  
# Simple Queue Service
Amazon Simple Queue Service (SQS) is a fully managed message queuing service that allows you to integrate queuing functionality in your application. SQS offers two types of message queues: standard and FIFO.
## Features
  - send messages
  - store messages
  - receive messages
## Tips
  - The Simple Queue Service (SQS) is found under the Application Integration on the AWS Management Console.
  - FIFO queues support up to 300 messages per second.
  - FIFO queues guarantee the ordering of messages.
  - Standard queues offer best-effort ordering but no guarantees.
  - Standard queues deliver a message at least once, but occasionally more than one copy of a message is delivered.
  
# Containers in the Cloud
Enterprises are adopting container technology at an explosive rate. A container consists of everything an application needs to run: the application itself and its dependencies (e.g. libraries, utilities, configuration files), all bundled into one package. 

Each container is an independent component that can run on its own and be moved from environment to environment.

** We will be going more in-depth on the topic of Microservices in Course 4: Microservices at Scale using AWS & Kubernetes**
  - [General overview about Docker containers](https://docs.docker.com/engine/docker-overview/)
  - [Documentation on Docker Containers](https://www.docker.com/resources/what-container)
# Elastic Container Service (ECS)
ECS is an orchestration service used for automating deployment, scaling, and managing of your containerized applications. ECS works well with Docker containers by:
  - launching and stopping Docker containers
  - scaling your applications
  - querying the state of your applications
## Tips
  - ECS is under the Compute section on the AWS Management Console.
  - You can schedule long-running applications, services, and batch processeses using ECS.
  - Docker is the only container platform supported by Amazon ECS.



