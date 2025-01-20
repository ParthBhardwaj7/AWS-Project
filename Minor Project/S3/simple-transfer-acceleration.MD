# S3 bucket using simple upload and Transfer Acceleration
# Step 1: Create an S3 Bucket
* Log in to the AWS Management Console.
* Navigate to the S3 service.
* Click Create bucket.
* Enter the bucket name (e.g., my-website-bucket).
* Select a region.
* Click Create.
## Step 2: Upload Files Using Simple Upload
### Step 2.1: Uploading Files to S3 (Simple Upload)
* Install and Configure AWS CLI (if not done already):

* If you don't have AWS CLI installed, follow the official guide: Install AWS CLI.
* Once installed, configure it:
```
aws configure
```
* Enter your AWS Access Key ID, Secret Access Key, region, and output format.
* Upload a File Using Simple Upload (AWS CLI):

Open a terminal/command prompt.
Use the following command to upload a file:
```
aws s3 cp /path/to/your/file.txt s3://your-bucket-name/your-file.txt
```
* Replace /path/to/your/file.txt with the path to the file you want to upload.
* Replace your-bucket-name with your actual bucket name.
* Example:

```
aws s3 cp /home/user/myfile.txt s3://my-website-bucket/myfile.txt
```
## Step 2.2: Verifying the Upload
* Go to the S3 Management Console.
* Open your bucket and check for the uploaded file (your-file.txt).
* Alternatively, you can verify using the AWS CLI:
```
aws s3 ls s3://your-bucket-name/your-file.txt
```
![Image](https://github.com/user-attachments/assets/cf308177-9445-4bf4-ab9b-f0996dd36e06)
## Step 3: Enable Transfer Acceleration for Your S3 Bucket
### Step 3.1: Enable S3 Transfer Acceleration
* Log in to AWS Console and navigate to the S3 service.
* Select your bucket (e.g., my-website-bucket).
* Go to the Properties tab.
* Scroll down to Transfer Acceleration and click Edit.
* Select Enable, and then click Save changes.
* After enabling, the accelerated endpoint URL will look like this:
```
<bucket-name>.s3-accelerate.amazonaws.com
```
* For example, if your bucket name is my-website-bucket, the URL will be:
```
my-website-bucket.s3-accelerate.amazonaws.com
```
## Step 4: Upload Files Using Transfer Acceleration
### Step 4.1: Uploading Files Using S3 Transfer Acceleration
* Now that you've enabled Transfer Acceleration for your bucket, you can use the accelerated endpoint for faster uploads.

* Upload Using AWS CLI with Transfer Acceleration:

* Use the --endpoint-url parameter to upload the file via the accelerated endpoint:
```
aws s3 cp /path/to/your/file.txt s3://your-bucket-name/your-file.txt --endpoint-url https://your-bucket-name.s3-accelerate.amazonaws.com
```
![Image](https://github.com/user-attachments/assets/57f99a1c-633c-4047-8363-fb939c16ed30)
Example:
```
aws s3 cp /home/user/myfile.txt s3://my-website-bucket/myfile.txt --endpoint-url https://my-website-bucket.s3-accelerate.amazonaws.com
```
* This command uploads the file using the transfer acceleration endpoint, which should result in faster upload speeds, especially for large files.

### Step 4.2: Verifying the Upload with Transfer Acceleration
* Go to the S3 Management Console and check for the uploaded file under your bucket.
* Alternatively, you can verify via AWS CLI:
```
aws s3 ls s3://your-bucket-name/your-file.txt
```
