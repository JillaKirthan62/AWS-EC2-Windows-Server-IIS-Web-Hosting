# AWS EC2 Windows Server & IIS Web Hosting 

## 📌 Project Overview

This project demonstrates how to deploy a **Windows Server 2019 EC2 instance on AWS**, configure secure remote and web access, install **IIS (Internet Information Services)**, and host a custom static HTML webpage.

The project covers the basic AWS architecture and configuration required to make a Windows-based web server publicly accessible through an EC2 public IP address.

## 🛠️ Technologies & Services

- **Amazon EC2**
- **Windows Server 2019**
- **Amazon VPC**
- **Public Subnet**
- **Internet Gateway**
- **Security Groups**
- **Key Pair**
- **Amazon EBS**
- **RDP (Remote Desktop Protocol)**
- **IIS Web Server**
- **HTML**

## 🏗️ Architecture

The architecture consists of:

```text
User / Internet
       |
       v
Internet Gateway
       |
       v
AWS VPC
       |
       v
Public Subnet
       |
       v
Windows Server 2019 EC2
       |
       +---- EBS Root Volume
       |
       +---- IIS Web Server
       |
       v
Custom Static HTML Page
       |
       v
Public IP (HTTP)
```

## 🚀 Project Workflow

### 1. Launch EC2 Instance

- Launch an EC2 instance using a **Windows Server 2019** base image.
- Place the instance inside a VPC and public subnet.
- Assign a public IP address.
- Configure the required EBS root volume.

### 2. Create Key Pair

A key pair is created during instance configuration for Windows server login and secure access.

### 3. Configure Security Group

The Security Group is configured to allow the required traffic:

| Protocol | Port | Purpose |
|---|---:|---|
| RDP | 3389 | Remote Windows Server access |
| HTTP | 80 | Public web access |

> For production deployments, access to RDP should be restricted to trusted IP addresses rather than allowing unrestricted internet access.

### 4. Connect Using RDP

The Windows EC2 instance is accessed remotely using **Remote Desktop Protocol (RDP)** from a local computer.

The EC2 public IP address is used to establish the remote connection.

### 5. Install IIS Web Server

Inside the Windows Server:

1. Open **Server Manager**.
2. Select **Add Roles and Features**.
3. Select the **Web Server (IIS)** role.
4. Complete the installation.
5. Verify that IIS is running.

### 6. Host Static HTML Page

A custom HTML page is created and placed in the IIS default website directory.

The page can contain a custom message such as:

```html
I gave in website file index.html
```

### 7. Test Public Web Access

After IIS and the Security Group are configured, open a browser and access:

```text
http://<EC2-PUBLIC-IP>
```

The custom static HTML page should be displayed through the IIS web server.

## 🔐 Security Configuration

The project uses AWS Security Groups to control inbound network traffic.

- **RDP (3389):** Used for remote administration of the Windows server.
- **HTTP (80):** Used to make the hosted website publicly accessible.
- **Key Pair:** Used as part of the Windows EC2 login process.
- **Public Subnet:** Allows the EC2 instance to communicate with the internet through the Internet Gateway.

## 📂 Project Contents

```text
AWS-EC2-Windows-IIS/
│
├── README.md
├── index.html
└── architecture/
    └── aws-architecture-diagram.png
```

## 📸 Architecture Diagram

The project architecture documents the following AWS components:

- AWS Region
- VPC
- Public Subnet
- Internet Gateway
- Windows Server 2019 EC2 Instance
- Security Group
- Key Pair
- EBS Root Volume
- IIS Web Server
- Public HTTP Access

## ✅ Result

Successfully deployed a **Windows Server 2019 EC2 instance**, configured RDP and HTTP access, installed IIS, hosted a custom static HTML webpage, and validated access to the webpage using the EC2 public IP.

## 🎯 Learning Outcomes

Through this project, I gained practical experience with:

- Launching and configuring AWS EC2 instances
- Working with Windows Server on AWS
- Configuring VPC and public subnet resources
- Managing Security Group inbound rules
- Connecting to Windows EC2 using RDP
- Installing and configuring IIS
- Hosting static HTML websites
- Understanding basic AWS cloud architecture
- Testing public web access through an EC2 public IP

## 👨‍💻 Author

**Jilla Kirthan**

B.Tech – Computer Science & Engineering  
Specialization: Artificial Intelligence & Machine Learning

MIT License
