# FortiGate Administrator Account Management Lab

## Overview

This lab demonstrates how to create and manage administrator accounts on a FortiGate Firewall using FortiOS 7.x. The objective was to understand how FortiGate implements **Role-Based Access Control (RBAC)** by assigning different administrator profiles with varying permission levels.

Following the Principle of Least Privilege, I created administrator accounts with full administrative access and read-only access to simulate real-world enterprise environments where different IT personnel require different levels of access.

---

## Technologies Used

- FortiGate Firewall
- FortiOS 7.x
- Role-Based Access Control (RBAC)
- Local Administrator Accounts
- Administrator Profiles

---

# Skills Demonstrated

- FortiGate Administration
- User Management
- Administrator Profiles
- Role-Based Access Control (RBAC)
- Security Best Practices
- Least Privilege
- Firewall Administration

---

# Lab Tasks

- Created a Super Administrator account
- Reviewed built-in Administrator Profiles
- Assigned administrator permissions
- Created a Read-Only administrator account
- Verified administrator access levels
- Learned the differences between administrator permission levels

---

# Step 1 – Review Administrator Profiles

FortiGate includes several administrator profiles that determine what an administrator is allowed to configure. The default profiles available include:

- Read-Only
- prof_admin
- super_admin

The **super_admin** profile provides unrestricted Read/Write access to every configuration category within the firewall.

![Administrator Profiles](images/01-admin-profiles.png)

---

# Step 2 – Create a Super Administrator

A new local administrator account named **Joshua** was created.

### Configuration

- Username: Joshua
- Authentication Type: Local User
- Administrator Profile: super_admin

The account was configured with the **super_admin** profile, granting complete administrative control of the FortiGate firewall.

![Create Super Administrator](images/02-create-super-admin.png)

---

# Step 3 – Review Super Administrator Permissions

The **super_admin** administrator profile grants unrestricted Read/Write permissions across all major FortiGate configuration categories.

### Permissions Included

- Security Fabric
- FortiView
- User & Device
- Firewall
- Log & Report
- Network
- System
- Security Profiles
- VPN
- WAN Optimization & Cache
- WiFi & Switch Controller

These permissions allow a Super Administrator to configure every aspect of the firewall including firewall policies, VPNs, routing, interfaces, security profiles, firmware upgrades, and system settings.

![Super Administrator Permissions](images/03-super-admin-permissions.png)

---

# Step 4 – Verify Administrator Accounts

After creating the administrator account, the FortiGate administrator list now contains:

| Username | Profile |
|-----------|----------|
| firewall | super_admin |
| Joshua | super_admin |

Both accounts currently have unrestricted administrative privileges.

![Administrator Accounts](images/04-admin-users.png)

---

# Step 5 – Create a Read-Only Administrator

A second administrator account named **Tara** was created.

### Configuration

- Username: Tara
- Authentication: Local User
- Administrator Profile: Read-Only

This administrator can monitor the firewall but cannot make configuration changes.

Typical responsibilities include:

- Viewing firewall policies
- Monitoring VPN tunnels
- Viewing logs
- Monitoring bandwidth
- Viewing security events

Configuration changes such as editing firewall rules or creating VPNs are not permitted.

![Create Read-Only Administrator](images/05-create-readonly-admin.png)

---

# Step 6 – Verify Final Administrator List

After completing the lab, the FortiGate firewall contained three administrator accounts.

| Username | Profile | Purpose |
|-----------|----------|---------------------------|
| firewall | super_admin | Default FortiGate administrator |
| Joshua | super_admin | Full administrative access |
| Tara | Read-Only | Monitoring and auditing |

![Final Administrator List](images/06-final-admin-list.png)

---

# What I Learned

This lab provided hands-on experience with administrator management within FortiGate.

Key concepts reinforced include:

- Creating Local Administrator accounts
- Assigning Administrator Profiles
- Managing administrative permissions
- Understanding Role-Based Access Control (RBAC)
- Implementing the Principle of Least Privilege
- Securing firewall administrative access
- Differentiating between Super Administrator and Read-Only roles

---

# Security Best Practices

During this lab I learned several security best practices that are commonly used in enterprise environments:

- Create individual administrator accounts instead of sharing credentials.
- Assign the minimum permissions required for each administrator.
- Reserve the **super_admin** profile for trusted senior administrators.
- Use Read-Only accounts for monitoring, auditing, and troubleshooting.
- Regularly review administrator accounts and assigned permissions.

---

# Repository Structure

```
FortiGate-Administrator-Accounts/
│
├── README.md
└── images/
    ├── 01-admin-profiles.png
    ├── 02-create-super-admin.png
    ├── 03-super-admin-permissions.png
    ├── 04-admin-users.png
    ├── 05-create-readonly-admin.png
    └── 06-final-admin-list.png
```

---

# Reference

This project was completed by reproducing the configuration demonstrated in the following tutorial while independently documenting each step and explaining the concepts learned.

**Tutorial**

Managing Administrator User Accounts on FortiGate – Full Access, Read-Only & User-Defined

https://www.youtube.com/watch?v=IiZWnPDtYS4
