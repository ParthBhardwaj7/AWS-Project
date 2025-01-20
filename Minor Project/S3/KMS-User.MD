# KMS Tutorial
## Step 1: Create a KMS Key
* Go to the AWS Management Console.
* Navigate to the AWS Key Management Service (KMS).
* Click Create key.
* Key type: Symmetric.
* Key usage: Encrypt and decrypt.
* Add a description (e.g., S3 Encryption Key).
* Set permissions:
* Add your IAM admin user (or yourself) as a key administrator.
* Add the specific IAM user(s) who will need access to this key under Other AWS accounts or Key users.
* Finish creating the key and copy its Key ID for later use.
## Step 2: Create an S3 Bucket and Enable KMS Encryption
* Navigate to the S3 service.
* Click Create bucket and give it a name (e.g., kms-encrypted-bucket).
* In the Bucket settings, go to Default encryption:
* Select Server-side encryption.
* Choose AWS KMS key.
* Select the KMS key you created earlier.
* Finish creating the bucket.
## Step 3: Create Two IAM Users
* User 1: Has KMS Permissions
* Go to the IAM Console and click Add users.
* Enter the name (e.g., UserWithKMS).
* Give Permission of S3ReadOnlyAccess

* User 2: Has No KMS Permissions
* Go to the IAM Console and click Add users.
* Enter the name (e.g., UserWithNoKMS).
* Give Permission of S3ReadOnlyAccess

## Step 4: Test Access for Each User
* UserWithKMS:
* Log in as UserWithKMS
* Check If you Can Open the file
## Step 4: Test Access for Each User
* UserWithNoKMS:
* Log in as UserWithNoKMS
* Check If you Can Open the file
![Image](https://github.com/user-attachments/assets/62458b48-b34a-4042-b506-947c60327813)

![Image](https://github.com/user-attachments/assets/a2fd71ca-fa8f-4fe2-b656-27ff048fd500)

![Image](https://github.com/user-attachments/assets/65026b06-970f-405b-b43a-0dc1e3b00856)

![Image](https://github.com/user-attachments/assets/8f4d7f2e-1390-456a-8bb3-1ea7455f7891)

![Image](https://github.com/user-attachments/assets/52a7eeb9-114a-453d-83cb-d7c54e574c69)
