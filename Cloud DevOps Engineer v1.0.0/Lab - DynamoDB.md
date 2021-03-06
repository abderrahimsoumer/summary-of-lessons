# # DynamoDB
In this hands-on exercise, you will create a NoSQL database in the cloud. 
## Prerequisites:
- AWS Account
## Topics Covered:
By the end of this lab, you will be able to:
- Create a table
- Add data to a table
- Query data in a table

# Steps:
1. **Access the DynamoDB service from AWS Management Console**
  - On the AWS Management Console page, type "dynamo" in the `Find Services` box and then select `DynamoDB`.
  - On the DynamoDB Console, click `Create table`.
  - Enter `Course` as the `Table name`.
  - Enter `Name` in for the `Partition key` and ensure `String` is selected.
  
    **Note:** The partition key spreads data against partitions for scalability. 
  - Keep the remainder of the defaults, and click the “Create” button.
2. Add Data to the Table
  - Once the table is created, click on the `Items tab`.
  - Click `Create item`.
    - In the data entry window, type the following:
      - For `name`, enter, `Course 1` and click `Save`
      - Click the `+`icon to add additional fields:
        - Select `Insert`
        - Select `String`
        - For the field `name`, enter `Teacher`
        - For the `value`, enter `Kesha Williams`
        - Click `Save`
    Follow the same process to add 5 more documents.
3. **Query Data in a Table**
  - In the dropdown that contains `Scan`, change it to `Query`.
  - Where it says `Enter value`, in the row next to the `name` Partition key, enter `Course 1` and click `Start Search`.
  - You should see your search results appear in the window.
4. **Cleanup and delete resources**
  - To clean up the resources to avoid recurring charges, ensure the table name is selected.
  - Click on the `Delete table` button.
  - Ensure `Delete all CloudWatch alarms for this table` is selected and click `Delete`.
