# Migration-Project
# Server Migration using AWS Application Migration Service

## Overview

This project demonstrates a successful server migration using AWS Application Migration Service. The migration process involves migrating an existing server to an Amazon EC2 instance by leveraging the power of AWS services. The migration was carried out in a step-by-step manner, ensuring a smooth and efficient transition to the cloud environment.

## Project Steps

### Step 1: Launching the EC2 Instance

1. Launched an Amazon EC2 instance using the following details:
   - Amazon Machine Image (AMI): Amazon Linux 2
   - Subnet: Public
   - User Data: 
     ```bash
     sudo yum update -y
     sudo amazon-linux-extras install nginx1 -y 
     sudo systemctl enable nginx
     sudo systemctl start nginx
     ```
   - Security Group: Allowed inbound access on ports 80 (HTTP) and 22 (SSH)
   - Launched with a key pair for secure access.

2. Verified the successful deployment of the instance by accessing the Nginx welcome page through the public IP on a web browser.

3. SSH into the server to create a test file and test directory to ensure server functionality.

### Step 2: Creating Replication Settings Template

1. Went to AWS Migration Hub (MGN) and created a Replication Settings template with the following settings:
   - Subnet: Public subnet in the same VPC as the source instance.
   - Instance Type: t2.micro
   - Security Group: Used Application Migration Service security group for enhanced security.

2. For future changes, the template can be edited by going into the settings.

### Step 3: Adding the Source Server

1. Added the Source Server to the Replication Settings template by specifying the operating system.

2. Provided the necessary Secret Access Key and Access Key ID of a user with appropriate permissions for replication.

3. Executed the provided commands on the source server to initiate the replication process.

4. The source server appeared as "Ready for testing" on the console after replication was completed.

### Step 4: Editing Launch Settings

1. Accessed AWS Migration Hub (MGN) and selected the server.

2. Clicked on "Test and Cutover" and then "Edit Launch Settings" to modify the Networking and Security Groups.

3. Created a new version of the launch template and set it as the default version.

### Step 5: The Test Phase

1. Selected the server and clicked on "Test and Cutover."

2. Launched the test instance and marked it as "Ready for cutover."

3. Checked the Launch History to review job logs for verification.

### Step 6: Verification and Validation

1. Accessed the EC2 console to see the launched server.

2. Verified the Nginx test page by accessing the public IP through a web browser.

3. Logged into the server through SSH and verified the presence of the test file and test directory to confirm data transfer success.

### Step 7: Final Migration

1. Launched the cutover instances to complete the migration process.

## Conclusion

The successful completion of this project demonstrates the effectiveness of AWS Application Migration Service in simplifying server migration to the cloud. The step-by-step guide provides a clear roadmap for future migrations, enabling seamless transitions to AWS EC2 instances. The project is now available on GitHub, empowering others to replicate the migration process and further explore the capabilities of AWS cloud services.