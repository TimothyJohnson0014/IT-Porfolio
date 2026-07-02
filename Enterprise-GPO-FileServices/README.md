# Enterprise Secured File Infrastruce & Group Policy Lockdown

## Project Overview
This project simulates designing a Security Group with OUs, designing and implementing file shares via NTFS and shared permissions, deploying GPOs from the server, and configuring network drives and global lockout thresholds.

---

## Step-by-Step Implementation

### Step 1: Setting up a Security Group
To properly assign the appropriate file permissions for future steps, I created security groups corresponding to each department. The naming scale is not too difficult for better scalability if future departments are needed to be added. Eaxh group was manually named then the OUs were linked to the group.

![Security Group](ScreenshotsP2/Group-1.png)

![Security Group](ScreenshotsP2/Group-2.png)

![Security Group](ScreenshotsP2/Group-3.png)

![Security Group](ScreenshotsP2/Group-4.png)

![Security Group](ScreenshotsP2/Group-5.png)

![Security Group](ScreenshotsP2/Group-6.png)

---

### Step 2: NTFS File Deployment
Advanced security permissions required me to delete each user using special permissions and ensuring each department was only given specific permission such as full control for the HR_Share folder for only the HR department. Each limitation was tested in the last step.

![NTFS Permissions](ScreenshotsP2/NTFS-1.png)

![NTFS Permissions](ScreenshotsP2/NTFS-2.png)

![NTFS Permissions](ScreenshotsP2/NTFS-3.png)

![NTFS Permissions](ScreenshotsP2/NTFS-4.png)

![NTFS Permissions](ScreenshotsP2/NTFS-5.png)

![NTFS Permissions](ScreenshotsP2/NTFS-6.png)

![NTFS Permissions](ScreenshotsP2/NTFS-7.png)

---

### Step 3: Automating Multi-Department Onboarding via PowerShell
Instead of manually creating accounts, I utilized PowerShell ISE to write an automation script. The script automatically built separate Organizational Units (OUs) for HR, IT, and Finance, parsed user data, and safely provisioned standard employee accounts with secure temporary passwords.

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
