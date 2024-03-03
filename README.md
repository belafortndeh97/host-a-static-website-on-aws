# Project README: Hosting a Static Website on AWS

## Overview

This project demonstrates the deployment of a static HTML web application on Amazon Web Services (AWS). The infrastructure is designed for reliability, security, scalability, and efficient management. The project utilizes a variety of AWS services, including Virtual Private Cloud (VPC), EC2 instances, Internet Gateway, Security Groups, NAT Gateway, Application Load Balancer (ALB), Auto Scaling Group, Certificate Manager, Simple Notification Service (SNS), and Route 53.


### Prerequisites

- AWS CLI installed and configured with necessary permissions.
- Git installed on the machine where deployment is executed.

### Deployment Script

```bash
#!/bin/bash

# Switch to the root user to gain full administrative privileges
sudo su

# Update all installed packages to their latest versions
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change the current working directory to the Apache web root
cd /var/www/html

# Install Git
yum install git -y

# Clone the project GitHub repository to the current directory
git clone https://github.com/belafortndeh97/host-a-static-website-on-aws.git

# Copy all files, including hidden ones, from the cloned repository to the Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory to clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable the Apache HTTP Server to start automatically at system boot
systemctl enable httpd 

# Start the Apache HTTP Server to serve web content
systemctl start httpd
```

### Instructions for Deployment

1. Ensure that the AWS CLI is properly configured on the machine where the deployment script will be executed.
2. Execute the provided script to set up the required components for hosting the static website on AWS.

## Project Configuration and Features

1. **Virtual Private Cloud (VPC):** Configured with public and private subnets across two availability zones for enhanced availability and fault tolerance.

2. **Internet Gateway:** Deployed to facilitate connectivity between VPC instances and the wider Internet.

3. **Security Groups:** Implemented as a network firewall mechanism to control inbound and outbound traffic.

4. **Availability Zones:** Utilized two availability zones to enhance system reliability and fault tolerance.

5. **Public Subnets:** Used for infrastructure components like the NAT Gateway and Application Load Balancer.

6. **EC2 Instance Connect Endpoint:** Implemented for secure connections to assets within both public and private subnets.

7. **Private Subnets:** Positioned web servers (EC2 instances) for enhanced security.

8. **NAT Gateway:** Enabled instances in private subnets to access the Internet.

9. **Hosting the Website on EC2 Instances:** Utilized EC2 instances to host the static website.

10. **Application Load Balancer:** Employed for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.

11. **Auto Scaling Group:** Used to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

12. **Version Control and Collaboration:** Web files stored on GitHub for version control and collaboration.

13. **Secure Application Communications:** Implemented SSL/TLS using Certificate Manager for secure application communications.

14. **Simple Notification Service (SNS):** Configured to send notifications about activities within the Auto Scaling Group.

15. **Domain Name and DNS Configuration:** Registered the domain name and set up DNS records using Route 53 for easy access to the hosted website.

## Conclusion

This project provides a robust infrastructure for hosting a static website on AWS, combining various services to achieve high availability, security, and scalability. Users can deploy the provided script to set up the environment and host their static web applications effectively. 
