# Hybrid Active Directory Lab

## Overview
Documenting the deployment and configuration of a hybrid Active Directory environment on Azure for enterprise identity management and portfolio demonstration.

## 1. Cloud Infrastructure & VM Deployment
- **Cloud Provider:** Microsoft Azure
- **VM Size:** Standard_D2ads_v7 (AMD-based, cost-optimized)
- **OS:** Windows Server Datacenter

## 2. Active Directory Domain Services (AD DS) Installation
Configured server roles and features to prepare the virtual machine as a primary domain controller.

* Installed **Active Directory Domain Services** and **DNS Server** roles via Server Manager.
  <img width="463" height="282" alt="downloading AD" src="https://github.com/user-attachments/assets/4abc031f-0064-4fec-ad10-efa0e4671547" />
<img width="977" height="695" alt="adding features" src="https://github.com/user-attachments/assets/7c058476-b094-4d0f-9b38-917b0bbefe0d" />
<img width="977" height="696" alt="adding more features" src="https://github.com/user-attachments/assets/27e160b2-b491-4b4d-9ba4-e93bac005cd5" />
<img width="976" height="696" alt="waiting for installation" src="https://github.com/user-attachments/assets/a4d74a40-59f2-46e6-adbb-c7f87a601b24" />
<img width="972" height="693" alt="AD and features completed" src="https://github.com/user-attachments/assets/f9d78aa0-a6be-4841-a5f8-837b231be1e2" />

## 3. Server Roles and Features Installation
Successfully installed and verified the core server roles required for the lab environment.

- **Active Directory Domain Services (AD DS)**
- **DNS Server**
- **DHCP Server**
- **Print and Document Services**
- **Web Server (IIS)**
- **Group Policy Management**

## 4. Administrative Tools Verification
Verified that core Windows Server administrative tools are installed and accessible following the role deployment.

- **Active Directory Users and Computers (ADUC)**
- **DNS Manager**
- **DHCP Console**
- <img width="942" height="661" alt="AD Up and ready to go" src="https://github.com/user-attachments/assets/61082fc1-b78b-409b-9b55-21a73ce740d6" />

## 5. Active Directory Domain Controller Promotion
Promoted the Windows Server instance to a Domain Controller for the lab environment.

- **Deployment Type:** Added a new forest
- **Root Domain Name:** `lab.local`
- **Configured DSRM Password and completed prerequisite checks**
- <img width="948" height="701" alt="AD domain controller promotion" src="https://github.com/user-attachments/assets/f1ddb236-8cda-4103-8482-d8fc826a33d6" />

## 6. Organizational Unit (OU) Structure
Created a custom top-level Organizational Unit named `branch1` under the `lab.local` domain to organize future network objects and support hybrid cloud synchronization.
<img width="937" height="662" alt="created a new OU and named it branch1" src="https://github.com/user-attachments/assets/b59a3d8c-afb7-4cb5-abc9-96a426dd5ca3" />

## 7. Configuring Organizational Units (OUs)
To establish a structured and realistic directory hierarchy, custom Organizational Units were created beneath the root domain (`lab.local`).

* Created a top-level OU named `branch1` to segregate branch-specific resources.
* Added sub-OUs inside `branch1` including `users`, `computers`, and `groups` with accidental deletion protection enabled.
* <img width="536" height="466" alt="created new OU under branch1 called users" src="https://github.com/user-attachments/assets/0b15ef06-371d-4930-98ae-4dd109186f42" />
<img width="242" height="167" alt="created other OU&#39;s under branch1" src="https://github.com/user-attachments/assets/7e1d64b1-38a0-4c83-bfa8-74114831a33f" />

## 8. Creating Test Users
To populate the directory and test object management, a new test user account was created within the `users` sub-OU.

* Configured the user object properties and user logon name within the designated OU path (`lab.local/branch1/users`).
![New User Wizard Setup]
<img width="537" height="468" alt="creating a new user under the users OU" src="https://github.com/user-attachments/assets/0824fdcf-a8a9-46be-92d0-a0b5dfeb8ff8" />


* Verified the successfully created user account active within the container.
![Populated Users OU List]
<img width="707" height="335" alt="user is created" src="https://github.com/user-attachments/assets/05c4502d-1082-42fd-bd50-8481d8711823" />







