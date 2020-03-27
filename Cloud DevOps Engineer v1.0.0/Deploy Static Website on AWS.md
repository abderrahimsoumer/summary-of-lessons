# Deploy Static Website on AWS
## # Create S3 Bucket
1. Navigate to the “AWS Management Console” page, type “S3” in the “Find Services” box and then select “S3”.
![AWS Console ](./img/aws-console.png)
2. The Amazon S3 dashboard displays. Click “Create bucket”.
![Create s3 bucket ](./img/create-s3bucket.png)
3.Enter a “Bucket name” and click “Next”. Note: Bucket names must be globally unique.
![S3 bucket name](./img/enter-s3bucket-name.png)
4. Click “Next” again to skip over “Step 2: Configure Options”.
5. On “Step 3: Set Permissions”, uncheck “Block all public access”.
![S3 Permissions](./img/s3-permissions.png)
6. Click “Next” and click “Create bucket”.
7. Once the bucket is created, click on the name of the bucket to open the bucket to the contents.
![S3 Done](./img/s3-done.png)

the interface changed in 2020 the interface looks like this
![2020 interface bucket](./img/s3bucket-creation2020.png)

## # Upload files to S3 Bucket
1. Once the bucket is open to its contents, click the “Upload” button.
![Upload files](./img/upload-s3bucket-files.png)

2. Click the “Add Files” button and drag and drop files and folders from your local computer to the S3 bucket and select “Upload”. Note: Upload the downloaded student-ready starter code files.
![Add files](./img/add-files.png)
![Drag files](./img/drag-files.png)
![Upload added files](./img/upload-add-files.png)

## # Secure Bucket via IAM
1. Click on the “Permissions” tab.
![s3 permission pollicy ](./img/s3-permission-pollicy.png)
2. Click on “Bucket Policy” and enter the bucket policy below replacing “your-website” with the name of your bucket and click “Save”.
```JSON
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Sid":"AddPerm",
      "Effect":"Allow",
      "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::your-website/*"]
    }
  ]
}
```
![Bucket pollicy](./bucket-pollicy.png)

You will see warnings about making your bucket public, but this step is required for static website hosting.

![Warning public bucket](./img/warn-public-bucket.png)

## # Configure S3 Bucket
1. Click on the “Properties” tab and then click on “Static website hosting”.
![s3 bucket properties](./img/s3bucket-properties.png)
2. Click on “Use this bucket to host a website”.
![use to Host website](./img/s3bucket-use-to-host-website.png)
3. For both “Index document” and “Error document”, enter “index.html” and click “Save”.
