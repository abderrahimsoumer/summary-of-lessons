# # Security in the Cloud
In this hands-on exercise, you will create an IAM policy and review the generated JSON.
## Prerequisites:
  - AWS account
## Topics Covered:
By the end of this lab, you will be able to:
  - Create an IAM policy using the visual editor.

# Steps:

1. **Create a Policy **
  - On the AWS Management Console page, type `IAM` in the `Find Services` box and then select `IAM`.
  - Click on `Policies` on the left-hand side.
  - Click `Create policy`.
  - Next to `Service`, click `Choose a service`.
  - In the selection box, type `S3`.
  - Select `S3`.
  - Specify the actions allowed in S3 by clicking on `List`.
  - Expand the `Read` action by clicking on the arrow next to it, then select `GetObject`.
  - Next in the `Resources` section, ensure `Specific` is selected, and select the `Any` checkboxes next to `bucket` and `object`.
  - Then click on `Review policy`.
  - Enter a name for your policy in the `Name` box.
  - Then click on `Create policy`.
  
2. **Review Policy**
  - After your policy is created, enter the name of the policy you just created in the `Filter policies` text box.
  - Click on the name of your policy.
  - Review the JSON for the policy you just created on the `Permissions` tab.
  - Click on the `Policy usage` tab to see if this policy is in use. Notice this policy is not attached to any resources yet.



