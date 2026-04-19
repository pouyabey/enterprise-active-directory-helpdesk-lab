# Enterprise Active Directory Helpdesk Lab

## Project Overview

This project is a hands-on Windows Server and Active Directory home lab designed to simulate common entry-level Help Desk and IT Support tasks in a small enterprise environment.

The goal of this lab is to practice building a Windows domain environment, creating Active Directory users and groups, organizing resources with OUs, and configuring shared folders with department-based permissions.

This lab is built for practicing real-world Help Desk tasks such as user management, group-based access control, and Windows file sharing.

---

## Lab Environment

- VMware Workstation / VirtualBox
- Windows Server 2025
- Windows 11 Pro
- Active Directory Domain Services
- DNS
- File Sharing
- NTFS Permissions

---

## Lab Network Design

| Device | Role | Hostname | Notes |
|---|---|---|---|
| Windows Server | Domain Controller | DC01 | Hosts Active Directory, DNS, and shared folders |
| Windows 11 Client | Domain Client | CLIENT01 | Will be joined to the domain in the next phase |

Domain name:

`pouyabey.local`

Domain Controller:

`DC01`

Shared folders location:

`C:\Shares`

---

## 1. Installed VMware / VirtualBox

I used virtualization software to create an isolated lab environment for Windows Server and Windows client machines. This allows me to safely practice system administration and Help Desk tasks without affecting a real production environment.


![VMware-overview](screenshots01-vmware-lab-overview.png)


---

## 2. Downloaded Windows Server ISO

I downloaded the Windows Server ISO to install the server operating system for the domain controller.

The Windows Server VM will be used to host:

- Active Directory Domain Services
- DNS
- Domain user accounts
- Security groups
- Shared folders

**Screenshot to add:**

`screenshots01-vmware-lab-overview.png`

Suggested screenshot: Windows Server ISO file or VM setup screen showing the ISO selected.

---

## 3. Downloaded Windows 10/11 ISO

I also downloaded a Windows 10/11 ISO to create a client workstation. This client machine will later be joined to the domain and used to test domain login and shared folder access.

**Screenshot to add:**

`/screenshots/03-windows-client-iso.png`

Suggested screenshot: Windows 10/11 ISO file or VM setup screen showing the ISO selected.

---

## 4. Created the DC01 Virtual Machine

I created a Windows Server virtual machine and named it:

`DC01`

This server will act as the main domain controller for the lab environment.

**Screenshot to add:**

`/screenshots/04-dc01-vm-created.png`

Suggested screenshot: VMware/VirtualBox showing the `DC01` virtual machine.

---

## 5. Configured Static IP on DC01

I configured a static IP address on the domain controller. A domain controller should have a static IP address because client machines need to consistently locate it for DNS and Active Directory services.

Example configuration:

- IP Address: `192.168.10.10`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.10.1`
- Preferred DNS: `192.168.10.10`

**Screenshot to add:**

`/screenshots/05-dc01-static-ip.png`

Suggested screenshot: IPv4 properties page showing the static IP configuration.

---

## 6. Installed Active Directory Domain Services

I installed the Active Directory Domain Services role on `DC01` using Server Manager.

This role allows the server to manage domain users, computers, groups, and policies.

**Screenshot to add:**

`/screenshots/06-ad-ds-role-installed.png`

Suggested screenshot: Server Manager showing Active Directory Domain Services installed.

---

## 7. Promoted DC01 to Domain Controller

After installing AD DS, I promoted `DC01` to a domain controller.

This step converts the Windows Server machine into the main server responsible for managing the domain.

**Screenshot to add:**

`/screenshots/07-dc01-promoted-domain-controller.png`

Suggested screenshot: Server Manager or promotion wizard completion screen.

---

## 8. Created the Domain: retailcorp.local

I created a new Active Directory forest with the domain name:

`retailcorp.local`

This domain simulates a small business environment called RetailCorp.

**Screenshot to add:**

`/screenshots/08-domain-retailcorp-created.png`

Suggested screenshot: Active Directory Users and Computers showing `retailcorp.local`.

---

## 9. Created Organizational Units

I created Organizational Units to organize users, groups, and computers in a structured way.

The OU structure helps simulate how companies separate departments and resources in Active Directory.

Example OU structure:

```text
retailcorp.local
│
├── RetailCorp
│   ├── Users
│   ├── Groups
│   └── Computers
