
### `docs/03-licensing.md`

```markdown
# 3. Licensing the FortiGate VM

## Purpose
Activate the free permanent evaluation license to unlock full functionality for learning.

## Steps

1. Ensure the VM has internet access (ping 8.8.8.8 works).
2. Synchronise system time with NTP:

   ```bash
   config system global
       set timezone America/New_York    # replace with your timezone
   end

   config system ntp
       set ntpsync enable
       set server-mode enable
       set type custom
       set server "0.pool.ntp.org"
       set server "1.pool.ntp.org"
   end

   execute ntp-sync