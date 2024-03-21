# AWS_Cloud_Home_Lab

# The following project goes through the creation of a secure lab in the club, comprising of a single public-facing subnet, with 2 EC2 instances running Kali Linux and Windows 11.
- VPC IP Address Block: 10.0.0.0/16 (Default)
- Public Subnet: 10.0.1.0/24
- Route table: Default
- Internet Gateway: Default
-
1. Log into the AWS Console and search for, and select "VPC":

<img width="1030" alt="Screenshot 2024-03-21 at 11 37 17" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/4320ac01-09b8-436d-9bf2-d633128d3c72">

2. On the next screen, select "VPCs" and you'll be taken to the VPC section. You will see the default VPC here, which is created for every AWS account:

<img width="1030" alt="Screenshot 2024-03-21 at 12 05 44" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/053bde20-db56-402f-88a5-cec112dc0d43">


3. Click on "Create VPC":

<img width="1031" alt="Screenshot 2024-03-21 at 12 06 36" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/811f2c9c-3466-42b5-a143-a8c5b0a0684a">


4. On the next screen, select "VPC and more". This will allow you to specify the parameters for the VPC and its component and have AWS automatically create them:

<img width="1031" alt="Screenshot 2024-03-21 at 12 07 10" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/4c7c0fc9-bd16-4742-a5e0-fd160927b0d4">


5. From here, select a name for the VPC and continue to specify the rest of the parameters, per the VPC specifications above, and the network topology, then click "Create VPC":

<img width="1029" alt="Screenshot 2024-03-21 at 12 09 52" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/5d68f408-842e-4394-bd6e-177b5069fa1e">


<img width="1027" alt="Screenshot 2024-03-21 at 12 11 04" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/fab14acc-caeb-44db-8dab-6d630d394865">


<img width="1028" alt="Screenshot 2024-03-21 at 12 11 58" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/334ad012-e063-413e-8dea-99a84762422c">


6.  The VPC and all its associated components per the selection, will be created, showing the below screen during the creation process:


<img width="1029" alt="Screenshot 2024-03-21 at 12 14 17" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/6e0f7a8c-b4c6-4205-8fad-8e512436a884">

7.  Once the process completes, select "View VPC":
  

<img width="1028" alt="Screenshot 2024-03-21 at 12 40 53" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/7c7d9196-306b-4bab-9197-72f8be5faf80">


8.  Select "Security groups", and then click on "Create security group":


<img width="1030" alt="Screenshot 2024-03-21 at 12 42 34" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/15c090c6-0895-4bd9-8597-b33471c8c171">


<img width="1031" alt="Screenshot 2024-03-21 at 12 44 12" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/f7089ce3-6255-4f30-bef7-2cf3a5ce2b4c">



9.    Give the security group a name and then select the VPC newly created on the drop-down under "VPC:


<img width="1031" alt="Screenshot 2024-03-21 at 12 45 53" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/c9091410-7792-4576-9b98-62e152cb0afd">


10.  Under "Inbound Rules", select "Add rule" and add the "SSH" and "RDP" rules per the below screen capture. Add a description for the security group:


<img width="1030" alt="Screenshot 2024-03-21 at 12 49 02" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/eb4ed1dd-3ff1-48a9-b674-cf2b0ba20093">


11.  Leave the "Outbound Rules" section with the default values and select "Create Security group":


<img width="956" alt="Screenshot 2024-03-21 at 12 51 37" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/ba9cd7b9-da4c-4aa5-ad2c-a556be57d7d9">


Note that for corporate network, the source should not be set to "Any". It is recommended to set it to "my IP", as you more than likely will be assigned a static IP by your ISP. Setting the inboud rules as above ALLOWS FOR TRAFFIC FROM ALL AND ANY SOURCES, which is not good practice. This lab is created for the purposes of learning practical skills, and is not running any production environments. Please keep this in mind when creating inbound rules for your resources; follow the principle of least privilege.


# In the next section, we will be creating the instances (virtual machines). One key pair will be created for use on both machines. Please note that good practice dictates each EC2 instance has its own unique key pair


12.  Search for, and select EC2 from the console:


<img width="952" alt="Screenshot 2024-03-21 at 12 56 56" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/277639c0-aa25-4557-a656-64eab49be25e">


13.  Select "Key pairs" and then "Create key pair":


<img width="952" alt="Screenshot 2024-03-21 at 12 58 39" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/5f98f410-c21c-4e13-bbcc-45692cb8fcb8">


<img width="953" alt="Screenshot 2024-03-21 at 12 59 10" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/97c2ba90-6f3b-4eed-88d4-a6de98a2bde1">


14.  Provide a name for the key pair, leave all other defaults, and then click on "create key pair":


<img width="953" alt="Screenshot 2024-03-21 at 13 00 49" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/a44b981a-11f2-4869-b377-a0b85961b83f">


<img width="956" alt="Screenshot 2024-03-21 at 13 01 34" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/145fdaeb-b469-4327-9d27-d52d33a4df0a">


15.  The key pay will be created and automatically downloaded by the browser. Store it in a safe place:


<img width="953" alt="Screenshot 2024-03-21 at 13 02 52" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/f827f70b-196a-44ab-b249-3dfec064384f">


16.  Back in the EC2 Dashboard, click on "Instances" and then "Launch instances":


<img width="951" alt="Screenshot 2024-03-21 at 13 05 16" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/36bea4c1-31e8-47b3-9c61-c8133ed3078e">


<img width="953" alt="Screenshot 2024-03-21 at 13 05 48" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/8d6014da-ef59-4f24-ae1a-1c2915b88d03">


17.  In the "Launch instance" section, give a name to the instance, select "Browse more AMIs" and select "AWS Marketplace". Search for, and select the "Kali linux" image and then select "Subscribe":

<img width="952" alt="Screenshot 2024-03-21 at 13 10 22" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/73c091a9-665f-419e-bc45-8299847e66ff">


<img width="953" alt="Screenshot 2024-03-21 at 13 10 53" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/ea290b5b-7a2d-4e13-8ad9-5c06ffcf6c11">


18.  Select the "Free tier eligible" instance type, and select the key pair created in the previous steps:


<img width="956" alt="Screenshot 2024-03-21 at 13 12 47" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/52cde180-e37c-46a0-a2e0-6b6a4329e65a">


19.  Select "Edit" in the "Network settings" sections. Specify the correct VPN, and then click no "Select existing security group". Make sure that "Auto assign public IP" is enabled:


<img width="950" alt="Screenshot 2024-03-21 at 13 15 42" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/06b9c20d-14f2-4546-a88f-389c961a0d67">



20.  Select the previously created security group and then click on "Launch instance":


<img width="952" alt="Screenshot 2024-03-21 at 13 17 38" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/d303e5c8-58ca-4fc2-b26b-023c7608600d">


<img width="953" alt="Screenshot 2024-03-21 at 13 18 06" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/9945810e-9ba5-46bd-99a6-cb37a86a153d">



21.  Go back to the instances portal and should the instance that was just created not appear, click on the "refresh" button and the instance should appear, per the below screens:


<img width="954" alt="Screenshot 2024-03-21 at 13 20 16" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/16ca6e89-693b-4a5b-885d-408b334bad3a">


<img width="954" alt="Screenshot 2024-03-21 at 13 20 39" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/34ffaab9-e7d4-45f4-9119-a4c39205c0ab">


<img width="953" alt="Screenshot 2024-03-21 at 13 21 03" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/71eb4e8e-f5ef-47b3-8166-c8b59ba1a26a">


22.  Click on "Launch instances" again and follow the same steps as before. Only, this time, select the "Windows" AMI, and give it a name that reflects this:


<img width="954" alt="Screenshot 2024-03-21 at 13 22 51" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/77ccad45-6f93-449d-a835-47a053aae339">


23.  You will now have 2 instances created and running, in the same subnet:


<img width="951" alt="Screenshot 2024-03-21 at 13 25 35" src="https://github.com/cyberkels/AWS_Cloud_Home_Lab/assets/147159632/ca4b952b-64db-406a-bd37-034cbd7fb1e4">



# In the next steps, we will be setting up connections to the instances, to allow access through RDP for the Windows instance, and VNC for the Linux instance


24.  







