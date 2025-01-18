# Grant Read-Only Access to an S3 Bucket

This guide explains how to grant read-only access to a specific IAM user for an S3 bucket by creating a bucket policy.

## Step 1: Open the AWS Management Console
1. Log in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to the **S3** service.

## Step 2: Identify the Bucket
1. Find and select the bucket to which you want to grant read-only access.
2. Note the bucket name (e.g., `example-bucket`) as you’ll need it for the policy.

## Step 3: Go to Bucket Permissions
1. Click on the bucket name.
2. Navigate to the **Permissions** tab.

## Step 4: Open the Bucket Policy Editor
1. Scroll down to the **Bucket Policy** section.
2. Click **Edit** or **Create bucket policy** if no policy exists.

## Step 5: Create the Bucket Policy
Use the following JSON policy for read-only access to the bucket:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::ACCOUNT_ID:user/USERNAME"
      },
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```
![Image](https://github.com/user-attachments/assets/ec4045fa-2190-403d-877c-f82e5dba155c)

It Can Be accesed by an IAM user With AWS CLI and if this Is need To be accesed By AWS Console Then YOU have to Create an INLINE Policy for user or give console access to user
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListAllMyBuckets",
      "Resource": "*"
    }
  ]
}
```
![Image](https://github.com/user-attachments/assets/8cfb6dc3-2f6f-417c-81bd-fd754e815af5)
