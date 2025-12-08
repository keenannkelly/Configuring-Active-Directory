# Configuring Active Directory Domain Services on Windows Server

A comprehensive guide demonstrating the installation and configuration of Active Directory Domain Services (AD DS) on Windows Server, including domain controller promotion and forest creation.

## 🎯 Project Overview

This project showcases the complete process of transforming a Windows Server into an Active Directory Domain Controller, demonstrating enterprise-level identity and access management skills essential for IT infrastructure administration.

## 🎥 Video Walkthrough

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

## 📋 Configuration Process

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

**What this does**: Launches the wizard to install server roles and features.

### Step 3: Select Installation Type
- Chose **"Role-based or feature-based installation"**
- Selected target server from server pool
- Clicked **"Next"** to proceed
- Confirmed server selection

**Installation Types**:
- **Role-based**: Install roles and features on a single server
- **Remote Desktop Services**: Configure RDS deployment
- **VHD-based**: Install on virtual hard disk

### Step 4: Choose Active Directory Domain Services
- From the **Server Roles** list, selected **"Active Directory Domain Services"**
- System prompted to add required features
- Clicked **"Add Features"** to include management tools
- Confirmed AD DS role selection

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

## 🔧 Technical Specifications

### Active Directory Configuration
```
Forest Name:              keenan.local
Domain Name:              keenan.local
NetBIOS Name:             KEENAN
Forest Functional Level:  Windows Server 2016+
Domain Functional Level:  Windows Server 2016+
Domain Controller:        Primary DC
DNS Server:               Integrated
Global Catalog:           Yes
```

### Server Roles Installed
- **Active Directory Domain Services** - Core AD functionality
- **DNS Server** - Name resolution for domain
- **File Replication Service** - SYSVOL replication
- **Kerberos Key Distribution Center** - Authentication

### Default Organizational Units Created
```
- Domain Controllers
- Users
- Computers
- Builtin
- ForeignSecurityPrincipals
- Managed Service Accounts
- Program Data
```

## 🔐 Security Configuration

### DSRM Password
- **Purpose**: Restore Mode administrator password
- **Usage**: Disaster recovery and offline maintenance
- **Best Practice**: Store securely, document separately
- **Requirement**: Strong, complex password

### Administrator Account
- **Username**: Administrator@keenan.local
- **Domain**: KEENAN\Administrator
- **Purpose**: Domain administrative access
- **Security**: Change default password immediately

### Default Security Groups Created
```
- Domain Admins
- Enterprise Admins
- Schema Admins
- Domain Users
- Domain Computers
- Group Policy Creator Owners
```

## 🛠️ Post-Installation Tasks

### Immediate Actions
```
1. ✅ Verify DNS configuration
2. ✅ Create Organizational Units (OUs)
3. ✅ Create user accounts
4. ✅ Configure Group Policy Objects (GPOs)
5. ✅ Set up backup strategy
6. ✅ Configure time synchronization
7. ✅ Document DSRM password securely
```

### DNS Verification
```powershell
# Check DNS server status
Get-DnsServer

# Verify DNS zones
Get-DnsServerZone

# Test DNS resolution
nslookup keenan.local
```

### Active Directory Verification
```powershell
# Check domain controller status
Get-ADDomainController

# Verify domain information
Get-ADDomain

# Check forest information
Get-ADForest

# List domain users
Get-ADUser -Filter *

# Verify SYSVOL replication
Get-SmbShare
```

## 📊 Active Directory Components

### Domain Services
- **Authentication** - Kerberos and NTLM
- **Authorization** - Access control and permissions
- **Directory Services** - Centralized object management
- **Group Policy** - Centralized configuration management
- **Replication** - Multi-master replication between DCs

### Integrated DNS
- **Forward Lookup Zones** - Name to IP resolution
- **Reverse Lookup Zones** - IP to name resolution
- **Dynamic Updates** - Automatic DNS record updates
- **Secure Updates** - Only domain members can update

## 🎓 Skills Demonstrated

### Windows Server Administration
- ✅ Server Manager proficiency
- ✅ Role and feature installation
- ✅ Active Directory deployment
- ✅ Domain controller configuration
- ✅ DNS integration

### Active Directory Expertise
- ✅ Forest and domain creation
- ✅ Domain controller promotion
- ✅ Functional level selection
- ✅ DSRM configuration
- ✅ DNS integration

### Enterprise IT Skills
- ✅ Identity and access management
- ✅ Directory services architecture
- ✅ Security best practices
- ✅ Disaster recovery planning
- ✅ Infrastructure documentation

## 🔄 Common Administrative Tasks

### Creating Organizational Units
```powershell
# Create OU structure
New-ADOrganizationalUnit -Name "Employees" -Path "DC=keenan,DC=local"
New-ADOrganizationalUnit -Name "IT" -Path "OU=Employees,DC=keenan,DC=local"
New-ADOrganizationalUnit -Name "HR" -Path "OU=Employees,DC=keenan,DC=local"
```

### Creating User Accounts
```powershell
# Create new user
New-ADUser -Name "John Doe" `
           -GivenName "John" `
           -Surname "Doe" `
           -SamAccountName "jdoe" `
           -UserPrincipalName "jdoe@keenan.local" `
           -Path "OU=IT,OU=Employees,DC=keenan,DC=local" `
           -AccountPassword (ConvertTo-SecureString "P@ssw0rd123!" -AsPlainText -Force) `
           -Enabled $true
```

### Creating Security Groups
```powershell
# Create security group
New-ADGroup -Name "IT Admins" `
            -GroupScope Global `
            -GroupCategory Security `
            -Path "OU=IT,OU=Employees,DC=keenan,DC=local"

# Add user to group
Add-ADGroupMember -Identity "IT Admins" -Members "jdoe"
```

## 🚨 Troubleshooting Guide

### DNS Issues
**Problem**: DNS not resolving domain names

**Solutions**:
```powershell
# Restart DNS service
Restart-Service DNS

# Check DNS forwarders
Get-DnsServerForwarder

# Verify DNS zones
Get-DnsServerZone
```

### Replication Issues
**Problem**: SYSVOL or AD replication failures

**Solutions**:
```powershell
# Check replication status
repadmin /replsummary

# Force replication
repadmin /syncall

# Check SYSVOL replication
dfsrdiag ReplicationState
```

### Authentication Issues
**Problem**: Users cannot log in to domain

**Solutions**:
```powershell
# Verify domain controller
dcdiag /v

# Check time synchronization
w32tm /query /status

# Verify Kerberos
klist tickets
```

## 📈 Best Practices

### Security Hardening
- ✅ Implement least privilege access
- ✅ Use separate admin accounts
- ✅ Enable audit logging
- ✅ Configure account lockout policies
- ✅ Implement password complexity requirements
- ✅ Regular security updates

### Backup Strategy
- ✅ System State backups (includes AD database)
- ✅ Regular backup schedule
- ✅ Test restore procedures
- ✅ Document DSRM password
- ✅ Offsite backup storage

### Monitoring
- ✅ Event log monitoring
- ✅ Replication health checks
- ✅ DNS health monitoring
- ✅ Performance monitoring
- ✅ Security audit reviews

## 🌐 Integration Possibilities

### Services That Can Integrate
- **Microsoft Exchange Server** - Email services
- **Microsoft SharePoint** - Collaboration platform
- **Microsoft SQL Server** - Database authentication
- **File Servers** - Centralized access control
- **VPN Solutions** - Remote access authentication
- **Cloud Services** - Azure AD Connect

## 💰 Enterprise Value

### Business Benefits
- **Centralized Management** - Single point of user/computer management
- **Security** - Unified authentication and authorization
- **Scalability** - Supports thousands of users and computers
- **Group Policy** - Automated configuration management
- **Single Sign-On** - One credential for multiple resources

## 📚 Additional Resources

- [Active Directory Domain Services Overview](https://docs.microsoft.com/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview)
- [Install Active Directory Domain Services](https://docs.microsoft.com/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)
- [Active Directory Best Practices](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/security-best-practices/best-practices-for-securing-active-directory)
- [PowerShell Active Directory Module](https://docs.microsoft.com/powershell/module/activedirectory/)

## 👨‍💻 Author

**Keenan Kelly**

This project demonstrates enterprise-level Windows Server and Active Directory administration skills essential for IT infrastructure management.

## 📄 Related Projects

- [Creating a VM on AWS](https://github.com/keenannkelly/Creating-VM-on-AWS) - EC2 Windows Server deployment
- [EC2 RDP Connection](https://github.com/keenannkelly/EC2-RDP-Connection) - Secure remote access guide

---

*Demonstrating enterprise identity and access management with Active Directory Domain Services*