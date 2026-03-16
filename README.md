\# AWS Manual VPC + EC2 Web Server Lab



\## Overview

This project demonstrates building AWS network infrastructure manually without automation tools. The goal was to understand how the core networking components of AWS interact to allow a public web server to run inside a Virtual Private Cloud (VPC).



All infrastructure components were created manually in the AWS console to better understand how networking works within AWS.



\---



\## Architecture Components



The following AWS services were used:



\- Amazon VPC (Virtual Private Cloud)

\- Public Subnet

\- Private Subnet

\- Internet Gateway

\- Route Table

\- Security Group

\- EC2 Instance

\- Apache Web Server



The EC2 instance was deployed inside a public subnet with routing configured through an Internet Gateway to allow internet access.



\---



\## Network Design



\### VPC Configuration

CIDR Block: 10.0.0.0/16



\### Subnet Configuration

Public Subnet: 10.0.1.0/24  

Private Subnet: 10.0.2.0/24



The public subnet allows internet access through the Internet Gateway while the private subnet is designed for internal resources.



\---



\## Route Table Configuration



Route Table Entry:



0.0.0.0/0 → Internet Gateway



This route allows instances inside the public subnet to communicate with the internet.



\---



\## Security Group Configuration



Inbound Security Group Rules



| Type | Protocol | Port | Source |

|-----|-----|-----|-----|

| SSH | TCP | 22 | My IP |

| HTTP | TCP | 80 | 0.0.0.0/0 |



These rules allow SSH access for administration and HTTP access so the web server can be accessed publicly.



\---



\## EC2 Instance Configuration



Instance Name: BellHVAC-Web-Server  

Instance Type: t2.micro  

AMI: Amazon Linux 2023  

Subnet: BellHVAC-Public-Subnet



The instance was launched with an SSH key pair for secure access.



Public IP Address used for testing:



http://100.52.215.167



\---



\## Installing the Web Server



After connecting to the instance, Apache was installed and configured.



Commands executed on the EC2 instance:



sudo dnf update -y  

sudo dnf install httpd -y  

sudo systemctl start httpd  

sudo systemctl enable httpd  

echo "BellHVAC Web Server Running" | sudo tee /var/www/html/index.html



\---



\## Testing the Web Server



After installation, the web server was verified by opening the instance's public IP address in a web browser:



http://100.52.215.167



The browser successfully returned the web page confirming the server was reachable through the internet.



\---



\## Screenshots



\### EC2 Instance Launched

!\[EC2 Instance Launch](images/06-ec2-instance-launched.png)



\### Instance Running

!\[EC2 Instance Running](images/07-ec2-instance-running.png)



\### Web Server Running

!\[Web Server Running](images/08-web-server-running.png)



\---



\## Outcome



This lab demonstrates the complete process of manually deploying a public web server within AWS using core networking components.



Skills demonstrated:



\- VPC design and configuration

\- Subnet creation

\- Internet Gateway configuration

\- Route table management

\- Security group configuration

\- EC2 instance deployment

\- Linux server administration

\- Apache web server installation

\- Public internet connectivity verification

