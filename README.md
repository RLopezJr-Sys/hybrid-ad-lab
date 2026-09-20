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
