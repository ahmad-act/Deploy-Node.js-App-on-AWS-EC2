# Deploy Node.js App on AWS EC2
[![Outlook](https://img.shields.io/badge/Outlook-0078D4?style=for-the-badge&logo=microsoft-outlook&logoColor=white)](mailto:engzaman2020@outlook.com) [![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ahmad-awsaf-uz-zaman/)

## Launch an EC2 Instance

1. **Log in to AWS Management Console:**

	- Go to the AWS Management Console.
	- Log in with your AWS credentials.

2. **Launch an Instance:**

	- Navigate to the EC2 Dashboard and click "Launch Instance."
	- Choose an Amazon Machine Image (AMI). Select "Amazon Linux 2 AMI" or "Ubuntu Server."
	- Choose an Instance Type. Select t2.micro if you are using the free tier.
	- Configure Instance Details, then click "Next: Add Storage."
	- Add Storage (default is fine), then click "Next: Add Tags."
	- Add Tags (optional), then click "Next: Configure Security Group."
	- Configure Security Group. Add rules to allow SSH (port 22) and HTTP (port 80) access.
	- Review and Launch the instance. Download the key pair (.pem file) and save it securely.

## Connect to the EC2 instance

1. **Open Terminal/Command Prompt:**

Navigate to the directory where your .pem file is located.

2. **Change Permissions of the Key Pair File:**

```bash
chmod 400 your-key-pair.pem
```

3. **Connect to the Instance:**

```bash
ssh -i "your-key-pair.pem" ec2-user@your-ec2-instance-public-dns
```

## Deply the Node.js App

1. **Update system**
```bash
sudo apt update
```

2. **Install Git**
```bash
sudo apt install git
```

3. **Install Node.js**
```bash
sudo apt install nodejs
```

4. **Install NPM**
```bash
sudo apt install npm
```

5. **Git colon**
```bash
git clone https://github.com/awsaf-utm/Deploy-Node.js-App-on-AWS-EC2.git
```

6. **Enter to the project folder**
```bash
cd  Deploy-Node.js-App-on-AWS-EC2
```

7. **Install application packages**
```bash
npm install
```

8. **Run the Node.js app**
```bash
npm run start
```

9. **Add the Port Number 3000 to the AWS Security Group**

	1. Open the AWS Management Console:

		- Go to the AWS Management Console.
		- Log in with your AWS credentials.

	2. Navigate to EC2 Dashboard:

		- In the AWS Management Console, click on "Services" and then select "EC2" under "Compute."

	3. Select Your Instance:

		- In the EC2 Dashboard, click on "Instances" in the left-hand menu.
		- Select the instance you are using to deploy your Node.js app.

	4. Edit Security Group:

		- Scroll down to the "Security groups" section under "Security" tab and click on the security group associated with your instance.

	5. Add Inbound Rule:

		- In the security group settings, go to the "Inbound rules" tab.
		- Click "Edit inbound rules."
		- Click "Add rule."
		- Set the type to "Custom TCP."
		- Set the port range to "3000."
		- Set the source to "Anywhere" (or a specific IP range if you prefer more security).
		- Click "Save rules."

10. **Now Ready to Access from Anywhere Through the Link**

	- After adding the inbound rule for port 3000, you can access your Node.js application from anywhere using the public DNS or IP address of your EC2 instance.

	1. Find Your Public DNS/IP:
		- In the EC2 Dashboard, select your instance and locate the "Public DNS (IPv4)" or "IPv4 Public IP" in the instance details.

	2. Access Your Application:

		- Open a web browser and go to http://your-ec2-instance-public-dns:3000 or http://your-ec2-instance-public-ip:3000.
		- Replace your-ec2-instance-public-dns or your-ec2-instance-public-ip with the actual public DNS or IP address of your EC2 instance.

 