# # Elastic Beanstalk
In this hands-on exercise, you will use Elastic Beanstalk to deploy a web application to the cloud. 
## Pre-requisites:
- AWS Account
- **DOWNLOAD THIS**: [WAR file](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/June/5d0296f8_udacity/udacity.war) containing the web application code
## Topics Covered:
By the end of this lab, you will be able to:
- Deploy a web application to the cloud using Elastic Beanstalk

# Steps:
1. **Access Elastic Beanstalk service from AWS Management Console**
  - On the AWS Management Console page, type `elastic beanstalk` in the `Find Services` box and then select `Elastic Beanstalk`.
  - If this is your first time accessing Elastic Beanstalk, click the `Get started` button.
  - Enter an `Application name`.
  - Under `Platform`, click the dropdown for `Choose a platform`. Select `Tomcat`.
  - Under `Application code`, select `Upload your code`. Click the `Upload` button.
  - Under `Upload your code`, make sure `Local file` is selected for `Source code origin`.
  - Click Choose File and upload the downloaded WAR file (link above in pre-requisites), `udacity.war`.
  - Click the `Upload` button.
  - Click the `Create application` button.
  
    **Important:** It will take about 10 minutes for your application to be created. There are several resources that need to be spun up to support your application. Your application is created once you see a green check mark and the `Health` of your application is `Ok`.
  - After the application is created, copy the application’s URL.
  - Important: The URL can be found on the top of the page, to the right of your application’s name. 
  
2. **Test the deployed web application in a browser**
  Navigate to a web browser like Chrome or Safari. 
  Paste the application URL and append `/message` on the end of the URL.
  Upon successfully accessing that URL, you will see the text `Hello World` in your browser window.
  
3. **Inspect the EC2 instance created for you**
  - Navigate to the EC2 console and inspect the instance that was created for you. The instance has the same name as your application. You can administer and manage this EC2 as if you created it yourself.
4. Cleanup and delete resources
  - To clean up the resources to avoid recurring charges, navigate back to the Elastic Beankstalk console.
  - Select your application.
  - Select the `Actions` button in the upper-right hand corner.
  - Select `Terminate environment`.
  - Enter the name of the application to be deleted.
  - Click the `Terminate` button.
  - After the application is terminated, you will be brought to the main page for the application.
  - Click on the `Actions` button in the upper right-hand corner.
  - Select `Delete application`.
  - Enter the name of your application.
  - Click the `Delete` button.  
  
