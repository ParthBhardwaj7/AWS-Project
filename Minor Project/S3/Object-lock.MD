# Amazon S3 Object Lock & Legal Hold

This guide explains **Amazon S3 Object Lock** and **Legal Hold**, their modes, and how to use them for protecting data from accidental or malicious deletions. Both features are crucial for implementing **Write Once, Read Many (WORM)** policies and meeting regulatory or compliance requirements.

---

## **What is Object Lock?**

**Object Lock** allows you to enforce **write-once-read-many (WORM)** policies on Amazon S3 objects. This ensures that data cannot be modified or deleted during a specified retention period, providing strong protection against accidental or malicious actions.

### **Modes of Object Lock**

1. **Governance Mode**:  
   - Allows authorized users (e.g., IAM Admins) to override or remove the lock.
   - Permissions required: `s3:BypassGovernanceRetention`.
   - Suitable for environments where some level of administrative control is needed.

2. **Compliance Mode**:  
   - Strictly enforces the retention policy.
   - Even the root user or administrators cannot modify or delete objects during the retention period.
   - Ideal for meeting regulatory compliance (e.g., SEC Rule 17a-4).

---

## **What is Legal Hold?**

**Legal Hold** is a feature of Object Lock that provides **indefinite protection** to an object, regardless of its retention period. It ensures that the object cannot be deleted or modified until the Legal Hold is explicitly removed.

### **Key Features of Legal Hold**
1. **No Expiration Date**: Legal Hold doesn’t expire, unlike retention periods.
2. **Overrides Retention Settings**: Even after the retention period ends, objects with Legal Hold cannot be deleted or modified.
3. **Use Case**: Ideal for legal or regulatory compliance where indefinite protection is required.


---

## **Step 1: Prerequisites**
1. **Object Lock must be enabled when creating the bucket.**  
   ⚠️ Object Lock can also be enabled for existing buckets .
2. **Versioning** must also be enabled for the bucket.
![Image](https://github.com/user-attachments/assets/6f002711-1f6e-479b-a499-1ea4fad56ed1)


---

## **Step 2: Create a Bucket with Object Lock**
1. Log in to the [AWS Management Console](https://aws.amazon.com/console/).
2. Navigate to the **S3** service and click the **"Create bucket"** button.
3. Enter a **Bucket name** (e.g., `example-bucket`) and choose the desired **AWS region**.
4. Under the **Object Lock** section:
   - Check **"Enable Object Lock"**.
   - Acknowledge the warning that enabling Object Lock cannot be undone by checking the confirmation box.
5. Ensure that **Versioning** is also enabled (it is automatically enabled with Object Lock).
6. Click **Create bucket**.
![Image](https://github.com/user-attachments/assets/d6cb4eb8-9333-4771-9b04-bcb4d6ad6df9)


---

## **Step 3: Open the Bucket Settings**
1. Go to the S3 Management Console and select the bucket you created with Object Lock enabled.
2. Navigate to the **Object Lock** tab in the bucket’s settings.

---

## **Step 4: Configure Default Retention Settings**
1. On the **Object Lock** tab, click **Edit** under **Default retention settings**.
2. Choose the **Default retention mode**:
   - **Governance**: Allows users with special permissions to delete objects before the retention period ends.
   - **Compliance**: Strictly prevents deletion or modification of objects, even by the root account.
3. Set the **Default retention period**:
   - Enter the number of **days** or **years** for which objects should be retained.
4. Click **Save changes**.
![Image](https://github.com/user-attachments/assets/c2f840ce-774b-4e2f-9cb8-b9c16c861da5)

![Image](https://github.com/user-attachments/assets/1710692f-3f5d-4322-8d3b-7c40a57a5e64)

---

## **Step 5: Enable Object Lock for Individual Objects**
You can apply Object Lock to individual objects during upload or via the AWS CLI.

### **Option 1: Console**
1. Upload a new object to the bucket.
2. During the upload process, go to the **Properties** section and enable **Object Lock** for the object.
3. Select the **Retention mode**:
   - **Governance**
   - **Compliance**
4. Specify the **Retention period** (e.g., 30 days).

### **Option 2: AWS CLI**
Use the following command to upload an object and enable Object Lock:

```bash
aws s3api put-object --bucket example-bucket --key file.txt --body file.txt \
--object-lock-mode Governance --object-lock-retain-until-date YYYY-MM-DD
```
# Enabling Legal Hold on an S3 Object

This guide provides step-by-step instructions on how to enable Legal Hold for an object in an Amazon S3 bucket using the AWS Management Console and AWS CLI.

## Option 1: AWS Management Console

1. **Select the Object:**
   - Navigate to the Amazon S3 console.
   - Select the bucket containing the object.
   - Select the object for which you want to enable Legal Hold.
   - Legal Hold is Object specified.

2. **Go to the Properties Tab:**
   - Click on the `Properties` tab.

3. **Scroll to the Legal Hold Section:**
   - Scroll down to the `Legal Hold` section.

4. **Toggle the Legal Hold Option:**
   - Toggle the `Legal hold` option to `ON`.

5. **Save Changes:**
   - Click `Save changes`.

## Option 2: AWS CLI

To enable Legal Hold using the AWS CLI, use the following command:

```bash
aws s3api put-object-legal-hold --bucket example-bucket --key file.txt --legal-hold-status ENABLED
