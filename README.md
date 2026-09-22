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
<img width="537" height="468" alt="creating a new user under the users OU" src="https://github.com/user-attachments/assets/0824fdcf-a8a9-46be-92d0-a0b5dfeb8ff8" />


* Verified the successfully created user account active within the container.
<img width="707" height="335" alt="user is created" src="https://github.com/user-attachments/assets/05c4502d-1082-42fd-bd50-8481d8711823" />

## 9. Account Management & Support Tasks
As part of routine Tier 1 help desk operations, user account troubleshooting and maintenance tasks were practiced within Active Directory.

* **Password Resets:** Demonstrated handling user password assistance by right-clicking a user object, selecting **Reset Password**, and enforcing security best practices by requiring the user to change their password at next logon.
* **Account Unlocks:** Reviewed account lockout status attributes to identify locked accounts on the domain controller and performed manual account unlocks when necessary.
* **Account Disabling / Enabling:** Examined how disabled accounts appear with specific icons in the directory container and practiced identifying purposeful status changes versus accidental changes.

* ## 10. Security Group Management
To follow best practices for access control and permissions scaling, Active Directory security groups were established rather than assigning direct permissions to individual user accounts.

* **Group Creation:** Created a dedicated security group named **IT Workers** under the organizational unit structure to manage departmental access.
* **Member Assignment:** Assigned test user accounts (such as `mike smith`) as members of the security group to demonstrate granular permission control and group-based policy management.
<img width="1082" height="696" alt="created groups" src="https://github.com/user-attachments/assets/2b34eaba-8864-4859-aaa6-d7c1eff2a22d" />

## 11. User Properties & Attribute Management
To understand how enterprise applications (such as Microsoft Teams and email routing systems) pull metadata from directory services, user object attributes and raw schema properties were explored.

* **Profile & Organization Metadata:** Configured user telephone numbers, job titles, department descriptions, and reporting managers to support directory integration and organizational hierarchies.
* **Attribute Editor & Proxy Addresses:** Utilized the advanced **Attribute Editor** tab to view and modify raw directory properties, including setting capital and lowercase proxy addresses (SMTP/smtp) to manage alternate email alias routing.
* **Object Tracking:** Practiced using global directory search features to locate user objects across multiple branch organizational units regardless of their current placement.

## 12. Network Configuration & Static IP Assignment
Configured dedicated static private IP addresses for both virtual machines to ensure stable internal DNS resolution, prevent domain controller communication drops, and avoid IP conflicts.

- **VM1 (Domain Controller):** Configured with a static private IP (`172.16.0.4`).
  <img width="702" height="238" alt="static ip for vm1" src="https://github.com/user-attachments/assets/5d784319-a68c-4c63-bacf-fdeefeee9c37" />
- **VM2 (Client Machine):** Configured with a unique static private IP (`172.16.0.5`) to eliminate subnet conflicts.
  <img width="708" height="224" alt="static ip for vm2" src="https://github.com/user-attachments/assets/de358f7b-b9c1-4fa6-8e17-18b3337ef4f8" />

  ## 13. Domain Controller Promotion & Forest Configuration
Configured VM1 as the primary domain controller by deploying a new Active Directory forest with the root domain name `lab.local`.

- **Deployment Configuration:** Selected "Add a new forest" and specified the root domain `lab.local`.
  <img width="946" height="578" alt="adding a new forest into the new vm1" src="https://github.com/user-attachments/assets/352938d5-100c-4f47-8ea6-1841428d7539" />

  ## 14. Organizational Unit & User Account Creation
Created a structured directory hierarchy inside the `lab.local` domain to organize department users and prepare for Group Policy deployment.

- **OU Hierarchy:** Established a root organizational unit named `Corp` containing department sub-OUs for **IT**, **HR**, and **Sales**.
- **Test Accounts:** Created individual user accounts within their respective department OUs for testing authentication and RBAC policies.
  <img width="940" height="555" alt="OUs and new users" src="https://github.com/user-attachments/assets/8db8959f-b5e2-447b-9bce-550f17deec20" />

**Client Network Configuration (VM2):** Configured custom DNS settings on VM2's network interface within Azure, pointing the preferred DNS server to the Domain Controller (`172.16.0.4`) to ensure proper `lab.local` name resolution.
<img width="1163" height="583" alt="adding vm1s static ip dns settings into vm2" src="https://github.com/user-attachments/assets/855156d2-1d26-4b48-acee-00bc003aa457" />


### Step 15: Joining Client Machine (VM2) to the Domain
- Navigated to **System Properties** > **Computer Name** on VM2 and selected **Change**.
- Changed domain membership to `lab.local` and authenticated using Domain Admin credentials.
- Received the *"Welcome to the lab.local domain"* confirmation prompt and restarted the virtual machine to finalize domain enrollment.
-
# Azure Active Directory Lab: VNet Isolation & Domain Join Troubleshooting

## Overview
This project documents the deployment and configuration of an Active Directory lab environment in Microsoft Azure, focusing on overcoming cloud-specific networking boundaries, DNS routing challenges, and successfully executing a Windows client domain join.

---

### Troubleshooting: VNet Isolation & DNS Name Resolution

* **Symptom:** Initial domain join attempts from VM2 to `lab.local` (`172.16.0.4`) failed with "Destination host unreachable" and DNS request timeouts.
* **Diagnosis:** 
  1. **Layer-3 VNet Isolation:** Auditing the Azure infrastructure revealed that VM1 and VM2 were initially deployed across isolated Virtual Networks (`vnet-eastus-1` and `vnet-eastus-2`). Because Azure enforces hard layer-3 boundaries between VNets by default, inter-VM traffic was dropped before ever reaching the OS firewall.
  2. **DNS Resolver Misconfiguration:** After redeploying VM2 into the shared VNet (`vnet-eastus-1`) to restore IP reachability, `nslookup lab.local` still failed because the client machine defaulted to Azure's internal virtual DNS resolver (`168.63.129.16`) instead of querying the Domain Controller directly.
* **Resolution:** 
  1. **Network Alignment:** Re-deployed VM2 into `vnet-eastus-1` and the shared subnet (`snet-eastus-1`) to establish successful base IP reachability.
  2. **Static DNS & Cache Reset:** Configured VM2's IPv4 adapter properties to explicitly point the **Preferred DNS server** to `172.16.0.4` and flushed the local resolver cache via `ipconfig /flushdns`.

**Verification Output:**
text
C:\Users\PClabadmin>nslookup lab.local
Server: UnKnown
Address: 172.16.0.4

Name: lab.local
Address: 172.16.0.4
<img width="607" height="248" alt="resolved issue" src="https://github.com/user-attachments/assets/24b24626-d7cb-4eb4-ab99-0c3ca0aa9d1d"/>

### Phase Final: Successful Domain Join & Verification

#### Authentication & Handshake
With layer-3 routing established and DNS name resolution successfully pointing to the Domain Controller (`172.16.0.4`), VM2 successfully initiated contact with the Active Directory domain controller. 

* **Credential Prompt:** Entering the domain administrative credentials (`lab\Administrator`) successfully authenticated against `lab.local`.
* **Result:** VM2 successfully dropped its workgroup membership, joined the Active Directory domain, and returned the confirmation prompt.

<img width="562" height="454" alt="login promt to join domain" src="https://github.com/user-attachments/assets/8ee913b7-f3b7-4393-aa12-1127653aaffa" />
<img width="329" height="185" alt="login successful" src="https://github.com/user-attachments/assets/149159db-3188-4f53-9303-98ad9da769dc" />

---

### Phase Final: Post-Join System Verification

#### Verification & Confirmation
Following the post-restart login using domain credentials, opening **System Properties** confirms that VM2 has successfully dropped its workgroup status and established full Active Directory membership.

* **Domain Status:** The system explicitly registers under `lab.local`.
* **Computer Identity:** The full computer name reflects the domain suffix (`rg-test-machine.lab.local`), proving successful integration.

<img width="501" height="580" alt="confirmed changes" src="https://github.com/user-attachments/assets/f81756b2-4fdb-48a9-b7bb-cb5599086a7c" />
