# FRONTEND DEPLOYMENT
## Steps
1. Create IAM Roles
   - EC2 role to access S3 (*EC2RoleforS3*)
   - CodeDeploy Role to attach to codedeploy(to allow it to call AWS services on your behalf)
2. Create an EC2 to deploy application
3. Attach EC2 role to EC2
4. Connect to the EC2 instance using **EC2 Instance Connect**.
5. Add an EC2 user using the command: `sudo adduser ec2-user`
6. Install code deploy agent in the EC2 to ensure there is communication between the EC2 and CodeDeploy.
   - `sudo apt update`
   - `sudo apt install ruby-full`
   - `sudo apt intall wget`
   - `cd /home/ubuntu`
   - `wget https://bucket-name.s3.region-identifier.amazonaws.com/latest/install` where you replace the **bucket-name** with the name of the bucket with the CodeDeploy Resource kit files for your region and **region-identifier** with the identifier of your region. e.g. `wget https://aws-codedeploy-us-east-1.s3.us-east-1.amazonaws.com/latest/install`
   - `chmod +x ./install`
   - To install the latest version of the CodeDeploy agent on Ubuntu server except version 20.04:
   `sudo ./install auto`
   - 
   Ensure it is running.
Create Codepipeline (CodeBuild, CodeDeploy)
Test if the deployment was a success by accessing http://ip-address
Test the pipeline by pushing some changes.