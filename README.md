# AWS Project- Highly-Available-Storage-Solution-using-Amazon-EFS

## Overview

ABC, an India-based entertainment production company focusing on Northeast and East Indian cinema, required a highly available and reliable storage solution for their on-premises data. The goal was to ensure data reliability, availability, security, and accessibility across all servers.

## Problem Statement

The existing infrastructure faced several issues:

1. **Scalability**: The NAS storage being used had limitations in scalability.
2. **Cloud Transition**: The client needed a complete application running in AWS cloud with centralized storage to keep files in sync with servers.
3. **Security**: There were no encryption mechanisms for data at rest or in transit.
4. **Manual Management**: Storage type changes and file transfers to infrequent storage required manual intervention.
5. **Cost**: High capital costs for new hardware hindered infrastructure scaling.
6. **Storage Options**: There was a need for low-cost storage options for both frequent and infrequent data.
7. **High Availability**: Required a highly available, secure, and persistent shared file system in AWS cloud.

## Solution: Amazon EFS

Amazon Elastic File System (EFS) was chosen for its ability to meet ABC's storage needs effectively:

1. **Scalability**: EFS automatically scales with usage, unlike NAS.
2. **Centralized Cloud Storage**: Accessible by multiple servers, ensuring data consistency.
3. **Security**: Provides built-in encryption at rest and in transit.
4. **Automated Storage Management**: Automatically transitions files to cost-effective storage tiers.
5. **Cost-Efficiency**: Eliminates hardware costs with a pay-as-you-go model.
6. **Low-Cost Options**: Offers tiered storage for frequent and infrequent data.
7. **High Availability**: Stores data across multiple Availability Zones for reliability.

## Project Implementation Steps

### Step 1: Create EFS
- Created KMS (Key Management Service) to ensure data security and compliance by managing encryption keys.
- Set up Amazon EFS using AWS Management Console with built-in encryption.

### Step 2: Create Security Group and Configure EC2
- Created security groups to control inbound and outbound traffic.
- Added specific inbound rules for protocols, ports, and source IPs.

### Step 3: Configure EC2 Instances
- Created two EC2 instances with Amazon Linux image and T2.micro instance type.
- Generated a key pair for secure instance access.
- Configured security groups during the creation of EC2 instances.

### Step 4: Mount EFS on EC2 Instances
- Installed EFS client using `amazon-efs-utils`.
- Created directories on both EC2 instances.
- Mounted the file system using EFS mount helper via DNS.
- Verified encryption at rest using appropriate AWS CLI commands.

### Step 5: Test File Sharing and Synchronization
- Created a file "File2" on the first EC2 instance in the EFS directory.
- Verified the presence of "File2" on the second EC2 instance, confirming successful file sharing and synchronization.

### Step 6: Clean Up Resources
- Terminated both EC2 instances.
- Deleted the EFS file system.
- Scheduled key deletion in the KMS Dashboard.

## Conclusion

By leveraging Amazon EFS, this project successfully provided ABC with a scalable, secure, and highly available storage solution. The integration of EFS with AWS services ensured data integrity, accessibility, and cost-efficiency, addressing the limitations of their previous infrastructure. ABC now benefits from a cloud-native storage solution that supports their growing storage needs while enhancing operational efficiency and security.

