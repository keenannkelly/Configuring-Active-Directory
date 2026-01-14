# Configuring Active Directory Domain Services on Windows Server

A comprehensive guide demonstrating the installation and configuration of Active Directory Domain Services (AD DS) on Windows Server, including domain controller promotion and forest creation.

## 🎯 Project Overview

This project showcases the complete process of transforming a Windows Server into an Active Directory Domain Controller, demonstrating enterprise-level identity and access management skills essential for IT infrastructure administration.

# 🎥 Watch Me Build This Lab!
Watch the complete Active Directory configuration process:
[![Configuring Active Directory](https://cdn.loom.com/sessions/thumbnails/ffbd7bc08d3c4dc8ba50f72fc4054205-with-play.gif)](https://www.loom.com/share/ffbd7bc08d3c4dc8ba50f72fc4054205)

**[▶️ Watch the Full Configuration Process](https://www.loom.com/share/ffbd7bc08d3c4dc8ba50f72fc4054205)**

*This video demonstrates the complete Active Directory Domain Services installation and domain controller promotion from start to finish.*

## 🏗️ Architecture

**Platform**: Windows Server 2025  
**Service**: Active Directory Domain Services (AD DS)  
**Domain**: keenan.local  
**Forest**: New forest creation  
**Role**: Primary Domain Controller  

# 📋 Steps Performed

### Step 1: Open Server Manager
- Accessed Windows Server virtual machine via RDP
- Launched **Server Manager** application
- Server Manager typically opens automatically on login
- Dashboard provides centralized server management interface

**Purpose**: Server Manager is the central hub for managing Windows Server roles and features.

### Step 2: Add Roles and Features
- Located **"Manage"** menu in Server Manager
- Selected **"Add Roles and Features"**
- Initiated the Add Roles and Features Wizard
- Prepared for Active Directory installation

  <img width="2560" height="1440" alt="image" src="https://github.com/user-attachments/assets/63366d89-18a4-463e-b897-3069c3a88fda" />

**What this does**: Launches the wizard to install server roles and features.

### Step 3: Select Installation Type
- Chose **"Role-based or feature-based installation"**
- Selected target server from server pool
- Clicked **"Next"** to proceed
- Confirmed server selection

### Step 4: Choose Active Directory Domain Services
- From the **Server Roles** list, selected **"Active Directory Domain Services"**
- System prompted to add required features
- Clicked **"Add Features"** to include management tools
- Confirmed AD DS role selection

<img width="2560" height="1440" alt="image" src="https://github.com/user-attachments/assets/73505441-8192-4da1-ac3c-0a38ce714177" />

**Included Components**:
- Active Directory Domain Services
- Group Policy Management
- Active Directory Administrative Center
- DNS Server (automatically added)

### Step 5: Complete the Installation Wizard
- Reviewed **Features** page (default selections)
- Reviewed **AD DS** information page
- Confirmed installation selections
- Clicked **"Next"** through remaining pages
- Reached **"Confirmation"** page
- Clicked **"Install"** to begin installation

**Installation Process**:
- Copies necessary files
- Registers services
- Configures system components
- Prepares for domain controller promotion

### Step 6: Installation Completion
- Monitored installation progress bar
- Waited for "Installation succeeded" message
- Verified successful installation status
- Noted post-deployment configuration notification
- Closed installation wizard

<img width="2560" height="1440" alt="image" src="https://github.com/user-attachments/assets/95bb0089-5489-4d01-99a6-eed9b9d32df5" />


**Status Check**: Installation completes but server is not yet a domain controller.

### Step 7: Promote Server to Domain Controller
- Located **yellow notification flag** in Server Manager
- Clicked on **"Promote this server to a domain controller"** link
- Launched Active Directory Domain Services Configuration Wizard
- Began domain controller promotion process

**Critical Step**: This transforms the server from a member server to a domain controller.

### Step 8: Create a New Forest
- Selected deployment operation: **"Add a new forest"**
- Entered **Root domain name**: `keenan.local`
- Validated domain name format
- Clicked **"Next"** to proceed

**Domain Naming**:
- Used `.local` TLD for internal network
- Format: `[name].local` (e.g., keenan.local)
- Avoid using public domain names for internal AD

### Step 9: Set Domain Controller Options
- **Forest functional level**: Windows Server 2016 (or latest)
- **Domain functional level**: Windows Server 2016 (or latest)
- **Domain Controller capabilities**:
  - ✅ Domain Name System (DNS) server
  - ✅ Global Catalog (GC)
- Created **Directory Services Restore Mode (DSRM) password**
- Entered strong, secure password
- Confirmed password

**DSRM Password**: Critical for disaster recovery - store securely!

### Step 10: DNS Options and NetBIOS
- **DNS Options**: Reviewed DNS delegation warning (expected for new forest)
- **Additional Options**: Verified NetBIOS domain name (auto-generated: KEENAN)
- **Paths**: Accepted default locations for:
  - Database folder: `C:\Windows\NTDS`
  - Log files folder: `C:\Windows\NTDS`
  - SYSVOL folder: `C:\Windows\SYSVOL`

### Step 11: Review Selections
- Reviewed complete configuration summary
- Verified all settings:
  - Forest name: keenan.local
  - Domain name: keenan.local
  - NetBIOS name: KEENAN
  - Functional levels
  - DNS configuration
- Clicked **"Next"** to proceed

**Prerequisites Check**: System automatically validates requirements.

### Step 12: Install Domain Controller
- Reviewed prerequisites check results
- Verified all checks passed (green checkmarks)
- Clicked **"Install"** to begin promotion
- Monitored installation progress
- Waited for completion message

**Installation Actions**:
- Configures Active Directory database
- Creates SYSVOL structure
- Configures DNS zones
- Establishes domain controller role

### Step 13: Restart the Server
- System automatically initiated restart
- Server rebooted to apply changes
- Waited for server to come back online
- Reconnected via RDP after restart

**Post-Restart**: Server is now a fully functional domain controller!

## 🎓 Skills Demonstrated

### Windows Server Administration
- ✅ Server Manager proficiency
- ✅ Role and feature installation
- ✅ Active Directory deployment
- ✅ Domain controller configuration
- ✅ DNS integration

## 👨‍💻 Author

**Keenan Kelly**

This project demonstrates enterprise-level Windows Server and Active Directory administration skills essential for IT infrastructure management.

## 📄 Related Projects

- [Creating a VM on AWS](https://github.com/keenannkelly/Creating-VM-on-AWS) - EC2 Windows Server deployment
- [EC2 RDP Connection](https://github.com/keenannkelly/EC2-RDP-Connection) - Secure remote access guide

---

*Demonstrating enterprise identity and access management with Active Directory Domain Services*
