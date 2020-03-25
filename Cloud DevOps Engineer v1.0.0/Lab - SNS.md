# # SNS
In this hands-on exercise, you will learn how to send alerts via SNS by creating a topic, subscribing to a topic, and publishing an alert message to a topic.
## Prerequisites:
  - AWS Account
## Topics Covered:
  By the end of this lab, you will be able to:
  - Create a topic
  - Subscribe to a topic
  - Publish a message to a topic
## Steps:
1. **Create a Topic**
  - On the AWS Management Console page, type `sns` in the `Find Services` box and then select `Simple Notification Service`. The SNS Dashboard appears.
  - On the left-hand menu, click on `Topics`.
  - Click on `Create topic`.
  - Enter a name for your topic in the Name field.
  - In the `Access policy – optional` section, for the `Define who can publish messages to the topic` section, ensure `Everyone` is selected allowing anyone to publish to the topic. For the `Define who can subscribe to this topic` section, ensure `Everyone` is selected.
  - Click `Create Topic`. The topic screen will display.
2. **Subscribe to a Topic**
  - Click `Create subscription` from the `Subscriptions` section.
  - For the `Protocol` field, select `Email`.
  - For the `Endpoint`, enter the email that should receive the notifications.
  - Click `Create subscription`.
  - The subscription page will display and the status will be `Pending confirmation`. After your subscription is created, you must confirm it.
  - In your email client, check the email address that you provided for the `Endpoint` and choose Confirm subscription in the email from Amazon SNS.
  - In your web browser, a subscription confirmation screen appears.
 
3. **Publish a Message to a Topic**
  - From the menu on the left-hand side, click on `Topics`.
  - Select the topic you created earlier and then click `Publish message`.
  - Enter a subject in the `Subject` field.
  - Enter a value in the `Message body to send to the endpoint` box in the `Message body` section.
  - Scroll down and click `Publish message`.
  - In your email client, read the email from Amazon SNS.
 
 
 
