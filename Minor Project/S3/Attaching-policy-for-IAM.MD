# Attaching Policy for IAm
## Step 1: Create or Identify an S3 Bucket
* Log in to the AWS Management Console.
* Navigate to S3 under the "Storage" section.
* Create a new bucket or identify an existing bucket you want the user to access.
* If creating a bucket, ensure to configure the bucket name and region.
![Image](https://github.com/user-attachments/assets/b78e72e7-ef43-4232-abb7-4eae6e787dc5)

## Step 2: Create or Identify an IAM User
* Navigate to the IAM (Identity and Access Management) service.
* Go to the Users section.
* Click Add Users (if creating a new user) or select an existing user.
* For a new user, provide a User name and select Access key - Programmatic access if the user will access the bucket via CLI or API.
![Image](https://github.com/user-attachments/assets/9a663387-aa77-497f-88ca-15f44d40981f)

## Step 3: Attach a Policy to the User
* You need to attach a policy that grants read-only access or write-only access or full access to the specific S3 bucket.
* Option 1: Attach an AWS Managed Policy
* On the user’s permissions page, click Add Permissions → Attach policies directly.
* Search for the AmazonS3ReadOnlyAccess or AmazonS3WriteOnlyAccess or AmazonS3FullAccess managed policy and select it.
* Click Next → Review → Add permissions.

![Image](https://github.com/user-attachments/assets/9d43f4a3-1286-45ba-a719-37e492dbbf9a)
