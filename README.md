# Linux Lab Report

## Overview

This repository contains the steps and commands used to safeguard file access on a Linux machine and manage controlled file access for government representatives. The lab involves creating user accounts, setting up File Access Control Lists (FACL), and adjusting file permissions.

## 1. Safeguarding Project File Access

### Objective

To comply with directives from Mr. Penny Johnson, CTO, we implemented file access controls to ensure that only Mr. Johnson had access to the `noida.txt` project file.

### Steps

1. **Create a New User Account:**

   ```bash
   sudo adduser pjohnson

2. Move the File to a Designated Directory:

bash
Copy code
sudo mkdir -p /project-directory
sudo mv /path/to/noida.txt /project-directory/
Set Up File Access Control List (FACL):

bash
Copy code
sudo setfacl -m u:pjohnson:rwx /project-directory/noida.txt
sudo setfacl -m other:--- /project-directory/noida.txt
Verify Access:

## Log in as pjohnson and check access:

bash
Copy code
su - pjohnson
cat /project-directory/noida.txt

## Ensure no other users have access:

bash
Copy code
ls -l /project-directory/noida.txt
getfacl /project-directory/noida.txt
Outputs
Output 1: Confirmed that Mr. Johnson had exclusive access, while other users were denied access.
Output 2: Verified that only Mr. Johnson could access the file.

## 2. Controlled File Access for Government Representatives
Objective
As part of the IT Security team, we provided controlled file access to representatives from Goa, Delhi, and Gujarat.

Steps

## Create New Users and Group:

bash
Copy code
sudo adduser stefi
sudo adduser aravind
sudo adduser jignesh
sudo groupadd citizen
sudo usermod -aG citizen stefi
sudo usermod -aG citizen aravind
sudo usermod -aG citizen jignesh
echo "india" | sudo passwd --stdin stefi
echo "india" | sudo passwd --stdin aravind
echo "india" | sudo passwd --stdin jignesh
Extract Files and Set Permissions:

bash
Copy code
sudo unzip government.zip -d /government-files/
sudo chown -R jignesh:citizen /government-files/
sudo chmod 700 /government-files/Gujarat
sudo setfacl -m u:jignesh:rwx /government-files/Gujarat
sudo setfacl -m u:aravind:rx /government-files/Gujarat
sudo setfacl -m u:stefi:--- /government-files/Delhi
sudo setfacl -R -m g:citizen:rwx /government-files/Goa
sudo setfacl -m g:citizen:rwx /government-files/Goa/anjuna.txt
sudo setfacl -m g:citizen:rwx /government-files/Goa/candolim.txt
Verify Permissions:

bash
Copy code
ls -l /government-files/
getfacl /government-files/Gujarat
getfacl /government-files/Delhi
getfacl /government-files/Goa/anjuna.txt
getfacl /government-files/Goa/candolim.txt
