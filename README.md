# Lab Report: Linux - Access Control and Permissions Management

## Overview

This report outlines the steps and results of implementing file access control measures on a Linux machine, as well as managing file permissions for a government project. The tasks were executed to meet specific directives and ensure secure access to sensitive files.

---

## Task 1: Safeguarding Access to "noida.txt"

**Objective**: Secure access to the "noida.txt" project file on a Linux machine, adhering to directives from Mr. Penny Johnson, CTO.

### Actions Taken

1. **Created User Account**:
    ```bash
    sudo useradd pjohnson
    sudo passwd pjohnson
    ```

2. **File Relocation**:
    ```bash
    sudo mv /path/to/noida.txt /home/pjohnson/project/
    ```

3. **Implemented FACL**:
    ```bash
    sudo setfacl -m u:pjohnson:rwx /home/pjohnson/project/noida.txt
    sudo setfacl -m other::0 /home/pjohnson/project/noida.txt
    ```

### Results

- **Verification**: Mr. Johnson successfully accessed the file, while other users were denied access.
- **Outcome**: Demonstrated that Mr. Penny Johnson had access, and no other user could access the file, ensuring project confidentiality.

![Access Control Results](https://github.com/user-attachments/assets/verification_results.png)

---

## Task 2: Managing File Permissions for Government Representatives

**Objective**: Set up controlled file access for representatives from Goa, Delhi, and Gujarat as part of a government project.

### Actions Taken

1. **User and Group Setup**:
    ```bash
    sudo useradd stefi
    sudo useradd aravind
    sudo useradd jignesh
    echo "india" | sudo passwd --stdin stefi
    echo "india" | sudo passwd --stdin aravind
    echo "india" | sudo passwd --stdin jignesh
    sudo groupadd citizen
    sudo usermod -a -G citizen stefi
    sudo usermod -a -G citizen aravind
    sudo usermod -a -G citizen jignesh
    ```

2. **File Permissions Adjustment**:
    - **Gujarat**:
        ```bash
        sudo cp government.zip /home/project/
        sudo unzip /home/project/government.zip -d /home/project/
        sudo chown jignesh:citizen /home/project/goa.txt
        sudo chmod 700 /home/project/goa.txt
        sudo chmod 755 /home/project/gujarat.txt
        ```

    - **Delhi**:
        ```bash
        sudo chmod -R 000 /home/project/delhi/
        ```

    - **Goa**:
        ```bash
        sudo chmod 777 /home/project/goa/
        sudo touch /home/project/goa/anjuna.txt
        sudo touch /home/project/goa/candolim.txt
        ```

### Results

- **Verification**: Access integrity was confirmed, and screenshots of permissions and access controls were uploaded.

![Permissions Adjustment Results](https://github.com/user-attachments/assets/permissions_results.png)

---

**Disclaimer**: This project is for educational purposes only. Unauthorized access and exploitation of systems without permission is illegal and unethical.
