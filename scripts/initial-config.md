# FortiGate Initial Configuration Commands

## Overview
This document contains all the CLI commands used to configure the FortiGate VM during the initial deployment.

## Commands

Run these commands in order after first login:

```bash
# 1. Set timezone (replace with yours)
config system global
    set timezone America/New_York
end
```

# 2. Enable NTP
```bash
config system ntp
    set ntpsync enable
    set server-mode enable
    set type custom
    set server "0.pool.ntp.org"
    set server "1.pool.ntp.org"
end
execute ntp-sync
```

# 3. Configure port1 (WAN)
```bash
config system interface
    edit port1
        set mode static
        set ip 10.1.1.220 255.255.255.0
        set allowaccess ping https ssh
    end
```

# 4. Set default gateway
```bash
config router static
    edit 1
        set device port1
        set gateway 10.1.1.1
    next
end
```

# 5. Set DNS
```bash
config system dns
    set primary 8.8.8.8
    set secondary 8.8.4.4
end
```

# 6. Verify connectivity
```bash
execute ping 10.1.1.1
execute ping 8.8.8.8
```

# 7. License activation (replace with your credentials)
```bash
execute vm-license-options account-id your_email@example.com
execute vm-license-options account-password your_password
execute vm-license
```

# 8. After reboot, configure port2 (LAN)
```bash
config system interface
    edit port2
        set mode static
        set ip 192.168.1.1 255.255.255.0
        set allowaccess ping https ssh
    end
```

# 9. Enable DHCP on port2 (CLI equivalent)
```bash
config system dhcp server
    edit 1
        set default-gateway 192.168.1.1
        set netmask 255.255.255.0
        set interface port2
        set ip-range 192.168.1.100 192.168.1.200
        set dns-server1 8.8.8.8
        set dns-server2 8.8.4.4
    end
```

# 10. Firewall policy (CLI equivalent)
```bash
config firewall policy
    edit 1
        set name "LAN to WAN"
        set srcintf port2
        set dstintf port1
        set srcaddr all
        set dstaddr all
        set action accept
        set schedule always
        set service ALL
        set nat enable
    end
```
