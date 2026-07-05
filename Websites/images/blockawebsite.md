# How to Block a Wesite on FortiGate Firewall

## Overview

This project demonstrates how to configure website filtering on a FortiGate firewall by creating a custom Web Filter profile, blocking Facebook using a Static URL Filter, applying the profile to a firewall policy, and validating that access to the website is successfully denied.

## Objective

Configure FortiGate to block access to Facebook while allowing normal internet connectivity for users.

---

## Technologies Used

- FortiGate Firewall v7.0
- Web Filter
- Static URL Filter
- Firewall Policies
- HTTPS Inspection
- DNS Filtering
- Web Browser for Testing

---

## Network Environment

- Firewall: FortiGate VM
- Internal Network: LAN
- WAN Connection: ISP1
- Test Website: Facebook

---

# Step 1: Navigate to Web Filter

Go to:

```
Security Profiles
    └── Web Filter
```

Click **Create New** to build a custom Web Filter profile.

![Step 1](images/website1.png)

---

# Step 2: Create a New Web Filter Profile

Configure:

Name

```
Block Facebook
```

Comments

```
Block Facebook
```

Feature Set

```
Flow-Based
```

Since this FortiGate is running without a FortiGuard subscription, the Static URL Filter will be used instead of FortiGuard Category Filtering.

![Step 2](images/website2.png)

---

# Step 3: Configure the Static URL Filter

Scroll down to **Static URL Filter**.

Enable

```
URL Filter
```

Click

```
Create New
```

Configure:

URL

```
*facebook.com
```

Type

```
Wildcard
```

Action

```
Block
```

Status

```
Enable
```

This blocks every Facebook subdomain.

Example:

```
facebook.com
www.facebook.com
m.facebook.com
business.facebook.com
```

![Step 3](images/website3.png)

---

# Step 4: Verify the URL Filter

After saving, verify that the Static URL Filter contains:

```
*facebook.com
```

Action:

```
Block
```

Status:

```
Enabled
```

![Step 4](images/website4.png)

---

# Step 5: Apply the Web Filter to a Firewall Policy

Navigate to

```
Policy & Objects
    └── Firewall Policy
```

Edit the LAN to WAN policy.

Enable

```
Web Filter
```

Select

```
Block Facebook
```

Save the policy.

This ensures every client matching this policy will use the custom Web Filter.

![Step 5](images/website9.png)

---

# Step 6: Test Website Blocking

Open a browser from a client machine.

Browse to

```
https://www.facebook.com
```

The connection should be blocked by the FortiGate firewall.

![Step 6](images/website10.png)

---

# Step 7: Verify the Blocked Certificate

Inspect the certificate presented by the blocked page.

The certificate shows:

Organization

```
Fortinet
```

Common Name

```
FortiGuard SDNS Blocked Page
```

This confirms the request was intercepted and blocked by the FortiGate security policy.

![Step 7](images/website11.png)

---

# DNS Configuration

The FortiGate is configured to use FortiGuard DNS servers.

```
208.91.112.53
208.91.112.52
```

FortiDDNS is also configured for the firewall.

![DNS Configuration](images/website12.png)

---

# Skills Demonstrated

- FortiGate Administration
- Web Filtering
- Static URL Filtering
- Firewall Policy Configuration
- HTTPS Traffic Inspection
- Enterprise Network Security
- DNS Configuration
- Security Validation
- Network Troubleshooting

---

# What I Learned

Through this lab I learned how FortiGate enforces website restrictions using Web Filter profiles and firewall policies. I also gained experience configuring Static URL Filters to block specific websites, applying security profiles to firewall rules, and validating that traffic was successfully denied. This project reinforced how firewalls provide centralized control over web access and help protect enterprise environments from unauthorized or unwanted web traffic.

