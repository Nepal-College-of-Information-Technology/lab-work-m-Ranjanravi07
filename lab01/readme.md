# 🚀 Lab-01: Deploying a Web Server on Cloud Infrastructure using AWS EC2 and Nginx

## 📌 Overview

This lab demonstrates how to deploy a web server on cloud infrastructure using **Amazon Web Services (AWS)** and **Nginx**. The project provides hands-on experience with cloud computing concepts, virtual machine deployment, server configuration, and webpage hosting.

The lab focuses on launching an EC2 instance, configuring networking and security settings, installing Nginx, and deploying a sample HTML webpage accessible through a public IP address.

---

# 🎯 Objectives

The main objectives of this lab are:

* Sign in to the AWS Console using a sandbox environment
* Create and configure an AWS EC2 virtual machine
* Connect securely to the instance using SSH
* Install and configure the Nginx web server
* Deploy and host a sample HTML webpage
* Verify successful deployment through a web browser

---

# ☁️ Background / Theory

## 1. Cloud Computing in IoT

Cloud computing plays a critical role in modern IoT ecosystems by providing scalable infrastructure, centralized data management, and remote accessibility. Since IoT devices continuously generate large volumes of data, cloud platforms help process, store, and analyze information efficiently.

### Key Benefits of Cloud Computing in IoT

* Centralized storage and processing
* Real-time device monitoring
* Elastic scalability
* Backup and disaster recovery
* Improved security and accessibility
* Analytics and visualization support

---

## 2. AWS EC2 (Elastic Compute Cloud)

Amazon EC2 is a cloud-based virtual server service that allows users to launch and manage scalable computing resources on demand.

### Features of EC2

* Resizable virtual machines
* Multiple operating system support
* Pay-as-you-go pricing
* High availability and reliability
* Secure cloud infrastructure

### Common Applications

* Website hosting
* Backend server deployment
* Cloud application hosting
* IoT data processing systems

---

## 3. Nginx Web Server

Nginx is a lightweight and high-performance web server commonly used for serving websites and managing network traffic.

### Features of Nginx

* Fast request processing
* Reverse proxy functionality
* Load balancing support
* SSL/TLS support
* Low memory consumption

### Common Uses

* Static and dynamic website hosting
* API gateway and proxy server
* Traffic distribution
* IoT dashboard hosting

---

# 🛠️ Technologies Used

| Technology   | Purpose               |
| ------------ | --------------------- |
| AWS EC2      | Cloud Virtual Machine |
| Ubuntu Linux | Operating System      |
| Nginx        | Web Server            |
| SSH          | Remote Access         |
| HTML         | Sample Webpage        |

---

# 📋 Procedure

## Step 1: Access AWS Console

1. Open the AWS Sandbox environment
2. Sign in to the AWS Management Console

---

## Step 2: Launch EC2 Instance

1. Navigate to **EC2 Dashboard**
2. Click **Launch Instance**
3. Select **Ubuntu Linux AMI**
4. Choose instance type:

   * `t2.micro`
5. Create or select a key pair
6. Configure security groups:

   * Allow SSH (Port 22)
   * Allow HTTP (Port 80)
7. Launch the instance

---

## Step 3: Connect to EC2 Instance

Use the following SSH command:

```bash
ssh -i key.pem ubuntu@<public-ip>
```

Replace:

* `key.pem` → Your downloaded key pair file
* `<public-ip>` → EC2 public IP address

---

## Step 4: Install Nginx

Update packages and install Nginx:

```bash
sudo apt update
sudo apt install nginx -y
```

Start and enable Nginx service:

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

Check Nginx status:

```bash
sudo systemctl status nginx
```

---

## Step 5: Deploy Sample Webpage

Open the default web page file:

```bash
sudo nano /var/www/html/index.html
```

Insert the following HTML code:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Cloud Web Server</title>
</head>
<body>
    <h1>Welcome to Nginx on AWS EC2</h1>
    <p>Web server deployed successfully on cloud infrastructure.</p>
</body>
</html>
```

Save and exit the editor.

---

## Step 6: Access the Hosted Webpage

1. Copy the EC2 public IP address
2. Open a web browser
3. Visit:

```bash
http://<public-ip>
```

The webpage should load successfully.

---

# ✅ Output

The following results were achieved:

* EC2 instance successfully created and running
* Nginx web server installed and configured
* Sample HTML webpage deployed
* Webpage accessible through public browser access



# 🧾 Conclusion

This lab successfully demonstrated the deployment of a web server on AWS EC2 using Nginx. The exercise provided practical experience in cloud computing, server configuration, and web hosting technologies.

By deploying and accessing a sample webpage, we gained foundational knowledge relevant to IoT systems, cloud infrastructure, DevOps practices, and modern web application deployment.

