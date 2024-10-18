# AWS IAM Learning - User, Policies, and Permissions

Today, I explored AWS Identity and Access Management (IAM). Here’s a step-by-step guide of what I learned:

## 🎯 Goal
Create a new IAM user, manage permissions by assigning policies, and create a group with specific permissions.

---

## 1. Creating a New IAM User

I started by creating a new IAM user in AWS with no permissions. Here are the steps:

- Navigate to the **IAM** section in the AWS Console.
- Click on **Users** and then **Add User**.
- Named the user **`TestUser`** with **programmatic access**.

![1-Create user](https://github.com/user-attachments/assets/f960cf50-cd47-4a87-aaca-71ab171d5089)


![2-csv file](https://github.com/user-attachments/assets/c74a4232-b18f-4556-b08f-ed99864a4ed5)


At this point, the user had no permissions and was unable to create an S3 bucket.

---

## 2. Testing Permissions - No Access to S3

After creating the user, I attempted to create an S3 bucket but encountered a permission error since the user did not have the required permissions.

![4-Default-group](https://github.com/user-attachments/assets/fb4bfd15-842b-4056-8e70-96bec82a95d0)
![5-no-permission-s3 bucket](https://github.com/user-attachments/assets/215f0655-cfaf-4258-b591-ef0f2b2cd0e8)

---

## 3. Assigning "AmazonS3FullAccess" Policy to the User

To give the user permissions to create and manage S3 buckets, I assigned the **AmazonS3FullAccess** policy to the user.

Steps:
- In the IAM console, navigate to **Users**, select **TestUser**, and click **Add Permissions**.
- Select the **AmazonS3FullAccess** policy.
- Attach the policy to the user.

![6-granting s3 full access](https://github.com/user-attachments/assets/3299e5d7-ec6e-47b9-8310-1574cdff50b3)
![6b-granting s3 full access](https://github.com/user-attachments/assets/867a0880-084b-45a0-9844-85f1434e60de)



Now, the user has full access to manage S3 buckets.

![7-s3 bukcet created](https://github.com/user-attachments/assets/d42a553a-7c91-4d8f-a01c-916f6c62efdb)


## 4. Creating a Group with S3 Full Access and EC2 Full Access

Next, I created a new IAM group and assigned both **AmazonS3FullAccess** and **AmazonEC2FullAccess** policies to the group. This will allow any user in this group to have full access to both S3 and EC2 services.

Steps:
- Navigate to **Groups** in the IAM Console and click **Create New Group**.
- Name the group **S3_EC2_Admins**.
- Attach both **AmazonS3FullAccess** and **AmazonEC2FullAccess** policies to the group.

![new-group](https://github.com/user-attachments/assets/2e27c91f-5986-47c1-a6f4-78df351e9760)
![new-group-with permission](https://github.com/user-attachments/assets/f9cd4a19-3ec6-48f5-b909-ed5c564d9937)




Any users added to this group will now have full access to S3 and EC2.

---

## 5. Testing the Group Permissions

Finally, I added **TestUser** to the newly created group, and the user successfully created an S3 bucket and launched an EC2 instance.



## 📝 Conclusion

- **IAM** allows granular control over AWS resources.
- Assigning policies to users and groups simplifies permission management.
- Adding users to groups with predefined permissions streamlines the process of access management.

