# # Relational Database Service (RDS)
In this hands-on exercise, you will create a MySQL database instance using RDS.
## Prerequisites:
  - AWS Account
## Topics Covered:
  By the end of this lab, you will be able to:
  - Launch a MySQL database

# Steps:
1. **Launch MySQL Database**
  - On the AWS Management Console page, type `rds` in the `Find Services` box and then select `RDS`.
  - On the left-hand side, click `Databases`.
  - Click `Create database`.
  - Under engines option, select `MySQL` and click the `Next` button
  - Under `Instance specifications`, leave the defaults.
  - Under the `Settings` section:
    - Enter a name for the `instance under DB instance` 
  
  Note: This will not be the database name.
  - Enter a `Master username`
  - Enter a `Master password` and confirm the password.
  - Click Next
  - For `Virtual Private Cloud (VPC)`, select `Create new VPC`.
  - Ensure `Create new DB Subnet Group` is selected. 
  - Leave the defaults for `Subnet group`, `Public accessibility`, `Availability zone`, and `VPC security groups`.
  - Under `Database options`, enter a `Database name` and leave the rest as defaults.
  - Under `Deletion protection`, uncheck `Enable deletion protection`.
  
    **Important:** In a real production scenario, you would leave this option checked.
  - Click Create database`.
  
2. **View Instance Details**
  - Once your database is created, open it by clicking on `View DB Instance details`.
  - Make sure the `DB instance` status shows `available`.
  - Scroll through and observe how the instance is configured.
3. Delete Database Instance
  Clean up the resources to avoid recurring charges.
  - From the RDS Dashboard homepage, select `Databases` from the left-hand navigation pane.
  - Select your newly created database by clicking on the name radio button next to the name.
  - From the `Actions` menu, select `Delete`.
  - In the confirmation popup:
     - Uncheck `Create final snapshot`
     - Select `I acknowledge that upon instance deletion, automated backups, including system snapshots and point-in-time recovery, will no longer be available.
     - Enter the requested confirmation for deletion`.
     - Click the `Delete` button
     
