# 4. Network Configuration – LAN (port2) and DHCP
## Purpose

Set up port2 as the gateway for the Windows 10 client, and enable DHCP to automatically assign IP addresses.

## Steps
### 4.1 Configure port2 Interface
In the FortiGate web GUI (https://10.1.1.220), go to Network > Interfaces.

Click Edit on the port2 interface.

Fill in:

Alias: LAN

Role: LAN

Addressing mode: Manual

IP/Netmask: 192.168.1.1/255.255.255.0

Administrative Access: check PING, HTTPS, SSH

Click OK.

### 4.2 Enable DHCP Server
Scroll down in the same port2 edit page to the DHCP Server section:

Check Enable DHCP Server.

IP Range: 192.168.1.100 – 192.168.1.200

Netmask: 255.255.255.0

Default Gateway: 192.168.1.1

DNS Server: 8.8.8.8, 8.8.4.4

Click OK.

### 4.3 Configure Windows 10 Client
Power on the Windows 10 VM.

Open Control Panel > Network and Sharing Center > Change adapter settings.

Right‑click the network adapter and select Properties.

Select Internet Protocol Version 4 (TCP/IPv4) and click Properties.

Select Obtain an IP address automatically and Obtain DNS server address automatically.

Click OK and close.

### 4.4 Verification
Open a command prompt on Windows 10.

Run ipconfig. You should see an IP like 192.168.1.100.

Run ping 192.168.1.1 – it should succeed.