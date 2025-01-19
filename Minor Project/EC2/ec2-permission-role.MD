# Give EC2 Instance permissions with IAM Role

## Steps
* Go to IAM Dashboard
* Click on User in the left navigation pane
* Add a user and give him programmatic access
* Click Next and Select the Attach Existing policy directly
* Search and add AmazonS3FullAccess Use the search box to search for those policies and click the checkbox
* Click Next Tags and review and create a user. 
* Click show and save the access key and secret key somewhere. Or download the CSV file if you want as well.
* Launch an Amazon Linux EC2 Instance
* SSH into it
* Let's say you want to work with Amazon S3 from this isntance. Make some buckets and list some buckets. You can use the AWS Command Line interface. Amazon Linux AMI has this installed already.
* Configure the AWS CLI

```
aws configure
```
* Enter the access key and secret access keys you generated earlier
* Enter the name of your region
* Create a S3 bucket from AWS CLI with a random name. If you have proper permissions you will be able to both create and list s3 buckets.
```
aws s3 mb s3://checkss
```
* List your S3 buckets.
```
aws s3 ls
```
* You just used Access keys to connect to S3 from EC2.
* View the credential file. Hardcoded credentials are insecure from a security perspective.
```cat ~/.aws/credentials```
* Delete the file . This will remove the credentials
![Image](https://github.com/user-attachments/assets/8e1adf6a-d694-4d33-a9db-1cea0943018b)

![Image](https://github.com/user-attachments/assets/04eaf3a1-aa23-4e01-878c-b4c35d4d0918)

![Image](https://github.com/user-attachments/assets/72920ca5-c85b-4031-ad50-5b328c5c89b5)

![Image](https://github.com/user-attachments/assets/c526903a-4dac-4ab6-b156-c867c61455d1)

![Image](https://github.com/user-attachments/assets/7991be4a-6957-4b23-889b-9fd18c07e672)

![Image](https://github.com/user-attachments/assets/6829442e-3b14-4371-b48f-40b8fa706179)
