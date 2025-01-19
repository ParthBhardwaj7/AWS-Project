# Symmetric Key Encryption
## What is Symmetric Key Encryption?
* A type of encryption where the same key is used for both encrypting and decrypting data.
* It is fast and efficient, making it suitable for encrypting large amounts of data.
###Key Features:
* Single Key: Shared between sender and receiver.
* Speed: Much faster compared to asymmetric encryption.
* Security Risk: If the key is exposed, the data is compromised.
* Examples of Algorithms:
* AES (Advanced Encryption Standard)
* DES (Data Encryption Standard)
* Triple DES (3DES)
* AWS and Symmetric Key Encryption:
* AWS KMS (Key Management Service):
* Manages and secures symmetric encryption keys.
* Allows you to create and manage Customer Master Keys (CMKs).
* Example: Encrypt data using AES-256 (symmetric encryption) with CMKs.
## Common Use Cases in AWS:
### S3 Server-Side Encryption:
* Encrypts objects stored in S3 buckets using a symmetric key.
* Options: AWS-managed keys (SSE-S3) or customer-managed keys (SSE-KMS).
### RDS Encryption:
* Data stored in Amazon RDS databases can be encrypted using KMS-managed symmetric keys.
### EBS Encryption:
* Amazon EBS volumes can be encrypted using symmetric keys managed by KMS.

# Server-Side Encryption (SSE)
* What is SSE?
Server-Side Encryption is when AWS encrypts data on your behalf before storing it on its servers and automatically decrypts it when accessed by authorized users.

#### Key Features:
* Managed by AWS: Encryption and decryption are handled on the server.
* Easy to Use: No need to manage encryption keys on the client side.
* Transparent to Users: Data is automatically encrypted when stored and decrypted when retrieved.
## SSE Options in AWS:

![Image](https://github.com/user-attachments/assets/133966a5-30b5-49d2-9f9e-a60129d29e24)

### SSE-S3 (AWS-Managed Keys):

* AWS manages both the encryption and the keys.
* Data is encrypted using AES-256.
* Requires minimal configuration.
* Specify this when uploading to S3 using:
```
aws s3 cp file.txt s3://my-bucket-name/ --sse AES256
```
### SSE-KMS (AWS Key Management Service):

* AWS encrypts your data using customer-managed keys (CMKs) in AWS KMS.
* Provides fine-grained access control and auditing of key usage.
Example upload:
```
aws s3 cp file.txt s3://my-bucket-name/ --sse aws:kms --sse-kms-key-id <key-id>
```
### SSE-C (Customer-Provided Keys):

* You provide the encryption key, but AWS performs the encryption and decryption.
* AWS does not store your key; you must supply it with every request.
* Example upload with a customer-provided key:
```
aws s3 cp file.txt s3://my-bucket-name/ \
    --sse-c \
    --sse-c-key <base64-encoded-key>
```
