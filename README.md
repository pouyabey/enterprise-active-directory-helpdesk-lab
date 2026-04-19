# Enterprise Active Directory Helpdesk Lab

## Project Overview

This project is a Windows Server and Active Directory home lab designed to simulate common entry-level Help Desk and IT Support tasks in a small business environment.

The lab includes setting up a domain controller, creating Active Directory users and security groups, organizing resources with OUs, and configuring department-based shared folders with Share and NTFS permissions.

---

## Lab Environment

- VMware Workstation
- Windows Server 2025
- Active Directory Domain Services
- DNS
- File Sharing
- NTFS Permissions

---

## Network Design

| Device | Role | Hostname | Status |
|---|---|---|---|
| Windows Server | Domain Controller | DC01 | Completed |
| Windows Client | Domain Client | CLIENT01 | planned |

- Domain: `pouyabey.local`
- Domain Controller: `DC01`
- Shared folder path: `C:\Shares`

---

## Completed Work

| Step | Task | Status |
|---|---|---|
| 1 | Created `DC01` virtual machine in VMware Workstation | Completed |
| 2 | Attached Windows Server ISO | Completed |
| 3 | Downloaded Windows 11 ISO for CLIENT01 | planned |
| 4 | Configured static IP on `DC01` | Completed |
| 5 | Installed Active Directory Domain Services | Completed |
| 6 | Promoted `DC01` to Domain Controller | Completed |
| 7 | Created domain `pouyabey.local` | Completed |
| 8 | Created OU structure for users, groups, and computers | Completed |
| 9 | Created department-based user accounts | Completed |
| 10 | Created department-based security groups | Completed |
| 11 | Created shared folders for each department | Completed |
| 12 | Configured Share and NTFS permissions | Completed |
| 13 | Verified network shares from `\\DC01` | Completed |

---

## Active Directory Structure

```text
pouyabey.local
|
├── Computers
├── Departments
|   ├── HR
|   ├── Finance
|   ├── IT
|   ├── Operations
|   └── Sales
├── Groups
└── Users
```

## Users and Groups

| Department | Security Group | Shared Folder |
|---|---|---|
| HR | `HR_Users` | `\\DC01\HR` |
| Finance | `Finance_Users` | `\\DC01\Finance` |
| IT | `IT_Users` | `\\DC01\IT` |
| Operations | `Operation_Users` | `\\DC01\Operations` |
| Sales | `Sales_Users` | `\\DC01\Sales` |

Each department user was added to the matching department security group.

---

## Shared Folder Permission Model

For this lab, I used Share permissions and NTFS permissions together:

- Share Permission: `Everyone = Full Control`
- NTFS Permission: `Department Group = Modify`

This allows the shares to be reachable over the network while NTFS permissions control the actual folder access.

| Shared Folder | Allowed Group | NTFS Permission |
|---|---|---|
| `\\DC01\HR` | `HR_Users` | Modify |
| `\\DC01\Finance` | `Finance_Users` | Modify |
| `\\DC01\IT` | `IT_Users` | Modify |
| `\\DC01\Operations` | `Operation_Users` | Modify |
| `\\DC01\Sales` | `Sales_Users` | Modify |

---

## CLIENT01 Virtual Machine

I created a Windows client virtual machine named `CLIENT01` in VMware Workstation. This machine will be used to test domain joining, domain user login, and shared folder access.

Configuration:

- Hostname: `CLIENT01`
- Operating System: Windows 10/11 Pro
- Network Adapter: Same virtual network as `DC01`
- Purpose: Domain-joined client workstation for Help Desk testing
---

## CLIENT01 DNS Configuration

Configured the DNS settings on `CLIENT01` to point to the domain controller `DC01`. This allows the client machine to locate the Active Directory domain and prepare for domain join.

- CLIENT01 IP Address: `192.168.56.20`
- Preferred DNS Server: `192.168.56.10`
- DNS Server: `DC01`

---

## CLIENT01 Domain Join

Joined the `CLIENT01` Windows client machine to the `pouyabey.local` Active Directory domain.

Before joining the domain, I configured the client DNS settings to point to the domain controller `DC01`. After the domain join, the client machine was restarted and verified as a domain-joined workstation.

- Client hostname: `CLIENT01`
- Domain: `pouyabey.local`
- Domain Controller / DNS Server: `DC01`
- DNS Server IP: `192.168.56.10`

---

## Domain Login Test

Tested domain user login on `CLIENT01` after joining the workstation to the `pouyabey.local` domain.

A domain user account was used to sign in to the client machine. The login was verified using Command Prompt.

- Client: `CLIENT01`
- Domain: `pouyabey.local`
- Domain User: `pouya.beyranvand`
- Verified with: `whoami`, `%USERDOMAIN%`, and `%USERNAME%`
---




## Screenshots

### VMware Lab Setup

![VMware Lab Overview](./screenshots/01-vmware-lab-overview.png)

### Static IP Configuration

![Static IP Configuration](./screenshots/03-dc01-static-ip.png)

### Active Directory Domain Services

![AD DS Installed](./screenshots/04-ad-ds-role-installed.png)

### Organizational Unit Structure

![OU Structure](./screenshots/06-ou-structure.png)

### Users and  Groups

![Users Created](./screenshots/07-users-created.png)

![Security Groups Created](./screenshots/08-groups-created.png)

### Shared Folders and Permissions

![Shared Folders Structure](./screenshots/09-shares-folder-structure.png)

![HR NTFS Permissions](./screenshots/10-hr-ntfs-permissions.png)

### Network Shares Verification

![Network Shares Visible](./screenshots/11-network-shares-visible.png)

### CLIENT01 Virtual Machine Setup

![CLIENT01 VM Created](./screenshots/12-client01-vm-created.png)


### CLIENT01 DNS Settings

![CLIENT01 DNS Settings](./screenshots/13-client01-dns-settings.png)

![CLIENT01 DNS Settings](./screenshots/14-client01-dns-settings.png)

### CLIENT01 Domain Membership Verification

![CLIENT01 Domain Membership](./screenshots/15-client01-domain-membership.png)

### Domain Login Verification

![Domain Login Verification](./screenshots/16-domain-login-verification.png)





---

## Current Status

This phase of the lab is complete through shared folder creation and permissions.

Next phase:

- Create `CLIENT01`
- Configure DNS on `CLIENT01`
- Join `CLIENT01` to `pouyabey.local`
- Test domain login
- Test shared folder access
- Practice Help Desk scenarios such as password reset, account unlock, and folder access troubleshooting


