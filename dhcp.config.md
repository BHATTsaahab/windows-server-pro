# 📌 DHCP Server Setup on Windows Server

A concise guide to configuring a DHCP server on Windows Server 2025 in Oracle VM VirtualBox with Active Directory (AD) integration.

## 🌐 Prerequisites
- **VirtualBox**: Latest (7.2.x) from [virtualbox.org](https://www.virtualbox.org/).
- **Windows Server 2025 ISO**: Evaluation from [Microsoft](https://www.microsoft.com/en-us/evalcenter).
- **Windows 11 ISO**: Client for testing, from [Microsoft](https://www.microsoft.com/software-download/windows11).
- **System**: 8GB RAM, 60GB disk, VT-x/AMD-V enabled.
- **Example**: A lab PC runs a network for DHCP practice.

## 🔧 Install Windows Server
- Create VM in VirtualBox:
  - **Name**: `DHCP-Server`.
  - **Type**: Microsoft Windows > Windows 2022 (64-bit).
  - **RAM**: 2048MB.
  - **CPUs**: 1.
  - **Disk**: VDI, dynamically allocated, 20GB.
- Attach ISO, boot, select **Standard (Desktop Experience)**.
- Install (10–20 min), set **Administrator** password, log in.
- Install Guest Additions: **Devices > Insert Guest Additions CD**, run, reboot.
- **Example**: Server setup for a small office.

## 🌍 Configure Static IP
- Open **Control Panel > Network and Sharing Center > Change adapter settings**.
- Right-click **Ethernet** > **Properties** > **IPv4** > **Properties**.
- Set:
  - **IP**: `192.168.1.1`
  - **Subnet Mask**: `255.255.255.0`
  - **DNS**: `192.168.1.1` (self for AD)
- Click **OK**, verify: `ipconfig /all`.
- **Example**: Ensures server reliability in network.

## 🔌 Install DHCP Role
- Open **Server Manager**, click **Manage > Add Roles and Features**.
- Select **Role-based installation**, choose server.
- Check **DHCP Server**, install, close.
- **Example**: Enables IP assignment for clients.

## 📋 Configure DHCP Scope
| Setting | Value |
|---------|-------|
| :computer: Name | Office Network |
| :globe_with_meridians: IP Range | 192.168.1.50–192.168.1.100 |
| :lock: Subnet Mask | 255.255.255.0 |
| :router: Gateway | 192.168.1.1 |
| :satellite: DNS | 192.168.1.1 |

- In **Server Manager**, go to **Tools > DHCP**.
- Expand server, right-click **IPv4** > **New Scope**.
- Enter settings above, activate scope, finish.
- **Example**: Assigns IPs to office devices.

## 🔒 Authorize DHCP
- In **DHCP Manager**, right-click server > **Authorize**.
- Refresh, ensure server is running.
- **Example**: Activates DHCP in AD environment.

## 💻 Setup AD and Domain Join
### 1. Install AD DS
- In **Server Manager**, add **Active Directory Domain Services** role.
- Install, promote to domain controller:
  - New forest: `lab.local`.
  - Complete, reboot.
- **Example**: Manages domain users.

### 2. Configure DNS for AD
- In **DHCP Manager > Scope Options**, set:
  - **006 DNS Servers**: `192.168.1.1`.
- Verify `lab.local` zone in **DNS Manager**.
- **Example**: Resolves `client1.lab.local`.

### 3. Join Client to Domain
- Create Windows 11 VM:
  - **Name**: `Client1`.
  - **Type**: Windows 11 Pro, 2048MB RAM, 20GB disk.
  - Install, set local user, join network.
- On **Client1**:
  - **System Properties > Computer Name > Change**.
  - Join domain: `lab.local`, use **Administrator** credentials.
  - Reboot.
- **Example**: Client accesses domain resources.

## 📊 Test DHCP and AD
- On **Client1**:
  - Set network to **Obtain IP automatically**.
  - Run: `ipconfig /renew`.
- Verify:
  - IP in `192.168.1.50–192.168.1.100` (`ipconfig /all`).
  - Domain login with AD user.
  - DNS: `nslookup lab.local`.
- **Example**: Client gets IP and logs into domain.





