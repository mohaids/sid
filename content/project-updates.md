+++
date = '2025-06-21T11:45:17-04:00'
draft = false
title = 'Project Updates'
+++

### 7.25
Studied more of SAA - went through S3

### 7.24
Project still on a bit of a haitus - studying for SAA.

### 7.21
Worked on school work and did some AWS-SAA studying

### 7.20
Took a day break to focus on Linux+ work

### 7.19
Need to create architecture diagram + study for Linux+

### 7.18
Uploaded image to ECR, stored cookies in S3, and created container instance on ECS - everythings working round the clock. Left it on since yesterday evening, checked it today noon, and it still functions!!

### 7.7
Apparently you can include secrets in Docker @ runtime. How do you do this?

### 7.5
Okay, big breakthrough - headless mode IS possible. Trying to use Docker since this is the case.

### 6.27
Insane that t3.micro isn't enough to even run the chrome installation process

### 6.22
1. Stopped most of the VMs - its actually SO expensive to have like 6 VMs running for a month.
    - [] Action Item: Currently trying to replicate the whole project in a fresh t3.micro VM
    - [] Also need to try to fix the requirements.txt question about the WebDriver.
2. Created a rough draft of the AWS-Console Documentation on how to create the VM
    - [] Need to finalize draft on 6.23 ideally.

### 6.21
Review of current status of the project: 
- The technical implementation works - however since I have a lot of VMs on at the moment, I have no clue which one hosts the working implementation.
    - [X] Action Item: Clean up VMs and ensure only one stable machine remains

- There has been some scope creep with trying to use Terraform + CloudFormation as methods to use to set up this project
    - [X] Action Item: Delay this for a bit

- Immedeate items that need to be addressed are:
    - [] The need to clean up documentation
    - [X] Clean up the main readme (read: go through your checkboxes and organize them)
    - [ ] also note that need to not use the raspberry pi ("earlier in the project i was convinced that a raspberry pi was needed to get around being blocked by services, ...")
        - [ ] probably should create a new diagram without the pi