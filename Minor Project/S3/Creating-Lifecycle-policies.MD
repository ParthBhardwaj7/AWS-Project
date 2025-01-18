# Creating Lifecycle Policies
## Step 1: Select Your Bucket
* From the list of S3 buckets, click on the name of the bucket where you want to set up a lifecycle policy.
* This will open the bucket's settings.
## Step 2: Go to the Management Tab
* Click on the Management tab from the menu at the top of the bucket settings page.
* Scroll down to the Lifecycle rules section.
## Step 3: Create a Lifecycle Rule
* Click the "Create lifecycle rule" button.
## Step 4: Name the Rule
* Provide a name for your lifecycle rule (e.g., ManageStorage).
![Image](https://github.com/user-attachments/assets/864bcb70-4604-4566-aa24-e493430d8b5d)
* Check the "Limit the scope of this rule using one or more filters" option if you want the rule to apply only to specific objects (e.g., objects with a specific prefix or tag).
* For example, if you want the rule to apply to all objects in a folder, enter the folder name in the Prefix field.

![Image](https://github.com/user-attachments/assets/78cd9872-e61d-4de5-a0cc-889feb3b933e)

![Image](https://github.com/user-attachments/assets/509efa0e-2fbb-4484-b834-48207b88dc83)

![Image](https://github.com/user-attachments/assets/b1c8d7ab-ccff-4e5b-8b00-c17f9af9aa25)

![Image](https://github.com/user-attachments/assets/6e9308ce-2c5c-427e-99c7-db926d8c404e)
## Step 6: Define Lifecycle Rule Actions
* Add a Transition Action
* Check the "Current version" option to apply the rule to the current version of objects.
* Add transition actions by selecting:
* Days after object creation: Specify the number of days after object creation when the transition should occur.
* Storage class: Choose the target storage class (e.g., INTELLIGENT_TIERING, GLACIER).
* You can add multiple transitions by clicking "Add transition" (e.g., transition to INTELLIGENT_TIERING after 30 days, then GLACIER after 90 days).
![Image](https://github.com/user-attachments/assets/ed9162a6-fcf7-4034-a761-f8863cc189f2)
* Add an Expiration Action

![Image](https://github.com/user-attachments/assets/7b6b8699-358c-4e20-a2c8-d52a7ec9fd0f)
* Check the "Expire current version of objects" option.
* Specify the number of days after object creation when objects should expire and be deleted.
![Image](https://github.com/user-attachments/assets/543ff2ed-97a4-4c87-8e0e-2829e7d9d252)

* Add a Cleanup Action for Incomplete Uploads
* Check the "Delete incomplete multipart uploads" option.
* Specify the number of days after the initiation of a multipart upload when incomplete uploads should be deleted (e.g., 7 days).
## Step 7: Review the Rule
 Review the settings you configured for transitions, expiration, and cleanup.
* Ensure the rule is set to Enabled.

![Image](https://github.com/user-attachments/assets/75280d5f-937d-428e-bc4b-908c01920362)
