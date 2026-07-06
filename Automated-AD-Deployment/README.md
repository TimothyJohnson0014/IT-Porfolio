# Automated Active Directory Deployment & Domain Architecture

## Project Overview
This project simulates the complete ground up setup and configuration of a corporate network infrastructure using VMware Workstation. 

---

## Step-by-Step Implementation

### Step 1: Configuring Server Static IP Network Settings
To ensure network consistency and reliable local name resolution, I manually configured the network adapter properties on the Windows Server 2022 instance, shifting it away from dynamic addressing to a permanent, static corporate layout matching the local hypervisor subnet gateway.
* **Key Configs:** IP `192.168.150.10`, Gateway `192.168.150.2`, DNS `192.168.150.10`

![Static IP Configuration](ScreenshotsP1/StaticIP-1.png)

![Static IP Configuration](ScreenshotsP1/StaticIP-2.png)

![Static IP Configuration](ScreenshotsP1/StaticIP-3.png)

---

### Step 2: Promoting the Domain Controller & Creating the Forest
I installed the Active Directory Domain Services (AD DS) and DNS Server roles through Server Manager. Once installed, I promoted the instance to a Domain Controller, creating a brand new root-level active directory forest named `corp.local`.

![Domain Controller Promotion](ScreenshotsP1/AD-1.png)

![Domain Controller Promotion](ScreenshotsP1/AD-2.png)

![Domain Controller Promotion](ScreenshotsP1/AD-3.png)

![Domain Controller Promotion](ScreenshotsP1/AD-4.png)

![Domain Controller Promotion](ScreenshotsP1/AD-5.png)

![Domain Controller Promotion](ScreenshotsP1/AD-6.png)

![Domain Controller Promotion](ScreenshotsP1/AD-7.png)

![Domain Controller Promotion](ScreenshotsP1/AD-8.png)

---

### Step 3: Automating Multi-Department Onboarding via PowerShell
Instead of manually creating accounts, I utilized PowerShell ISE to write an automation script. The script automatically built separate Organizational Units (OUs) for HR, IT, and Finance, parsed user data, and provisioned standard employee accounts with secure temporary passwords.

![PowerShell Automation Script](ScreenshotsP1/PS-1.png)

![PowerShell Automation Script](ScreenshotsP1/PS-2.png)

![PowerShell Automation Script](ScreenshotsP1/PS-3.png)

![PowerShell Automation Script](ScreenshotsP1/PS-4.png)

![PowerShell Automation Script](ScreenshotsP1/PS-5.png)

---

### Step 4: Activating Corporate DHCP Core Services
I deployed the DHCP Server role on the Domain Controller and created an active IP assignment scope. This ensures any corporate machine plugged into the network automatically receives an IP address within the valid `192.168.150.50 - .150` range while explicitly setting the server as their primary DNS director.

![DHCP Scope Setup](ScreenshotsP1/DHCP-1.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-2.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-3.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-4.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-5.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-6.png)

![DHCP Scope Setup](ScreenshotsP1/DHCP-7.png)

---

### Step 5: Client Workstation Domain-Join & Authentication
Booted up the Windows 11 Client VM, verified via `ipconfig` that it pulled a clean network configuration from the server's DHCP pool, and changed its system settings to join the `corp.local` domain. I successfully logged in for the first time using a script-generated user profile.

![Domain Join Success Welcome](ScreenshotsP1/Client-1.png)

![Domain Join Success Welcome](ScreenshotsP1/Client-2.png)

![Domain Join Success Welcome](ScreenshotsP1/Client-3.png)

![Domain Join Success Welcome](ScreenshotsP1/Client-4.png)

![Domain Join Success Welcome](ScreenshotsP1/Client-5.png)
