# 5. Firewall Policy – LAN to WAN

## Purpose
Allow the Windows 10 client to access the internet through the FortiGate.

## Steps
### 5.1 Create the Policy
1. In the GUI, go to **Policy & Objects > Firewall Policy**.
2. Click **Create New**.
3. Fill in:
   - **Name:** `LAN to WAN`
   - **Incoming Interface:** `port2`
   - **Outgoing Interface:** `port1`
   - **Source:** `all`
   - **Destination:** `all`
   - **Schedule:** `always`
   - **Service:** `ALL`
   - **Action:** `ACCEPT`
4. Under the **NAT** tab, check **Use Outbound Interface Address**.
5. Click **OK**.

### 5.2 Verification

- On the Windows 10 VM, open a browser and try to visit any website.
- It should work.