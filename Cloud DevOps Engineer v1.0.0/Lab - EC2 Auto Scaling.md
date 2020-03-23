# # EC2 Auto Scaling
In this hands-on exercise, you will use Auto Scaling to automatically launch Amazon EC2 instances in response to conditions you specify. You will also see auto scaling in action as it automatically provisions a replacement instance. 
## Prerequisites:
  - AWS Account
## Topics Covered:
  By the end of this lab, you will be able to:
  - Use auto scaling to launch EC2 instances
  - Create an auto scaling group
  - Test auto scaling

# Steps:
1. **Create a Launch Configuration**
  - On the AWS Management Console page, type `EC2` in the `Find Services` box and then select `EC2`.
  - Scroll down to the `Auto Scaling` section on the left-hand menu and click `Auto Scaling Groups`.
  - Click the `Create Auto Scaling group` button.
  - Review the steps and click on `Get started`.
  - Create a launch configuration by first selecting an Amazon Machine Image (AMI). In the row for `Amazon Linux 2 AMI (HVM), SSD Volume Type`, click the `Select` button.
  
  **Note:** An AMI is a template for an instance that indicates the operating system, an application server, and applications.
  - Confirm that `t2.micro` is selected.
  - Click Next: `Configure details.`
  - Enter a `name` of your choosing in the Name field.
  - Expand the `Advanced Details` section.
  - Next to `IP Address Type`, click on `Assign a public IP address to every instance`.
  - Click `Next: Add Storage`. Review the screen.
  - Click `Next: Configure Security Group`. 
  - Ensure `Create a new security group` is selected.
  - Click `Review`.
  - Click on `Create launch configuration`.
  - On the `Select an existing key pair or create a new key pair`, select `Create a new key pair`, enter a `key pair name` in the Key pair name field, and click `Download Key Pair`.
  - Click on `Create launch configuration`.

2. **Create an Auto Scaling Group**
  - On the `Create Auto Scaling Group` page, enter a group name of your choosing in the `Group name` field, ensure the `Group size` is set to `1`, for `Network` leave the default value. If no default value is shown, click on `Create new VPC`, and select the first `Subnet` by clicking in the `Subnet` field.
  - Click `Next: Configure scaling policies`.
  - Ensure that `Keep this group at its initial size` is selected.
  - Click `Review`.
  - Review the selected options and click `Create Auto Scaling group`.
  - Click `Close`.
3. **Verify your Auto Scaling Group**
  - Verify that the group has launched your EC2 instance by first ensuring the auto scaling group you just created is selected and examining the `Details` tab shown on the bottom of the screen.
  -Click the ``Activity History` tab. The status of your instance should be `Successful`, which means the instance is launched.
  - Click on the `Instances` tab. Notice the `Lifecycle` column states `InService`. 
4. **Test Auto Scaling**
  - Click on the `Instances` tab.
  - Under the `Instance ID` column, click on the blue Instance ID link.
  - You will be taken to the Amazon EC2 console Instances page.
  - Your instance should be selected.
  - Click the `Actions` button, scroll down to `Instance State`, and select `Terminate`. Then select `Yes, Terminate`.
  - In the left-hand navigation pane, click `Auto Scaling Groups`.
  - Click the `Instances` tab. You will eventually see a new instance appear. If the new instance doesn’t appear, click refresh occasionally to update the list. 
  - Click on the `Activity History` tab to review the history for the Instance.
5. **Delete Auto Scaling Resources** 
  - At the top of the screen, click the `Actions` button next to the `Create Auto Scaling group`.
  - Click the `Delete` option.  
  
  
  
