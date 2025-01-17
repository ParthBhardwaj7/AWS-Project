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

```aws configure
