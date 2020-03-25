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
