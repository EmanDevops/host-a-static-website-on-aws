![Alt text](Host_a_Static_Website_on_AWS.png)


# Host a Static Website on AWS

This project demonstrates how to host a static HTML web application on AWS using various AWS resources. The project setup includes configuring a Virtual Private Cloud (VPC) with public and private subnets, deploying an Internet Gateway, establishing security groups, and more. Below is a detailed guide on how the project was implemented and how you can replicate it.

## Project Overview

This project utilizes the following AWS services and components:
1. Configured a Virtual Private Cloud (VPC) with both public and private subnets across two different availability zones.
2. Deployed an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.
3. Established Security Groups as a network firewall mechanism.
4. Leveraged two Availability Zones to enhance system reliability and fault tolerance.
5. Utilized Public Subnets for infrastructure components like the NAT Gateway and Application Load Balancer.
6. Implemented EC2 Instance Connect Endpoint for secure connections to assets within both public and private subnets.
7. Positioned web servers (EC2 instances) within Private Subnets for enhanced security.
8. Enabled instances in both the private Application and Data subnets to access the Internet via the NAT Gateway.
9. Hosted the website on EC2 Instances.
10. Employed an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
11. Utilized an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.
12. Stored web files on GitHub for version control and collaboration.
13. Secured application communications using a Certificate Manager.
14. Configured Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.
15. Registered the domain name and set up a DNS record using Route 53.

## Prerequisites

Before you begin, ensure you have the following:
- An AWS account with necessary permissions.
- A registered domain name.
- Access to the project repository on GitHub.

## Deployment Instructions

Follow the steps below to deploy the static website:

### Step 1: Set Up the VPC and Subnets

1. Configure a Virtual Private Cloud (VPC) with both public and private subnets across two different availability zones.
2. Deploy an Internet Gateway to facilitate connectivity between VPC instances and the wider Internet.
3. Establish Security Groups as a network firewall mechanism.

### Step 2: Configure the EC2 Instances

1. Launch EC2 instances within the Private Subnets.
2. Ensure instances in the private Application and Data subnets can access the Internet via the NAT Gateway.

### Step 3: Deploy the Web Application

1. SSH into the EC2 instance and switch to the root user:
    ```bash
    sudo su
    ```
2. Update all installed packages to their latest versions:
    ```bash
    yum update -y
    ```
3. Install Apache HTTP Server:
    ```bash
    yum install -y httpd
    ```
4. Change the current working directory to the Apache web root:
    ```bash
    cd /var/www/html
    ```
5. Install Git:
    ```bash
    yum install git -y
    ```
6. Clone the project GitHub repository to the current directory:
    ```bash
    git clone https://github.com/EmanDevops/host-a-static-website-on-aws.git
    ```
7. Copy all files, including hidden ones, from the cloned repository to the Apache web root:
    ```bash
    cp -R /host-a-static-website-on-aws.git/. /var/www/html/
    ```
8. Remove the cloned repository directory to clean up unnecessary files:
    ```bash
    rm -rf /host-a-static-website-on-aws.git
    ```
9. Enable the Apache HTTP Server to start automatically at system boot:
    ```bash
    systemctl enable httpd
    ```
10. Start the Apache HTTP Server to serve web content:
    ```bash
    systemctl start httpd
    ```

### Step 4: Configure Load Balancer and Auto Scaling

1. Employ an Application Load Balancer and a target group for evenly distributing web traffic to an Auto Scaling Group of EC2 instances across multiple Availability Zones.
2. Utilize an Auto Scaling Group to automatically manage EC2 instances, ensuring website availability, scalability, fault tolerance, and elasticity.

### Step 5: Final Configurations

1. Secure application communications using a Certificate Manager.
2. Configure Simple Notification Service (SNS) to alert about activities within the Auto Scaling Group.
3. Register the domain name and set up a DNS record using Route 53.

## Repository

All reference diagrams and deployment scripts can be found in the [GitHub repository](https://github.com/EmanDevops/host-a-static-website-on-aws).

