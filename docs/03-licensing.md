# 3. Licensing the FortiGate VM
## Purpose
Activate the free permanent evaluation license to unlock full functionality for learning.

## Prerequisites
Internet connectivity (ping 8.8.8.8 works).

A FortiCare account (create one at https://support.fortinet.com).

The free trial is limited to one license per account – ensure you don't have another active trial.

## Steps
### 3.1 Synchronise System Time
SSL/TLS handshakes for licensing require accurate time. Set your timezone and enable NTP.

Find your timezone name:

```bash
get system timezone
(Scroll with Space to find your region, e.g., America/New_York)

Set the timezone:

bash
config system global
    set timezone America/New_York   # replace with yours
end
```
Enable NTP:

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
Verify the time:

```bash
get system status
```
Look for System Time – it should now be correct.

### 3.2 Activate the License
Run these commands one by one (replace with your FortiCare credentials):

```bash
execute vm-license-options account-id your_email@example.com
execute vm-license-options account-password your_password
execute vm-license
```
The system will ask to reboot – type y and press Enter.

## 3.3 Verify
After reboot, run:

```bash
get system status
```
Look for License Status: Valid. You can also check with:

```bash
diagnose debug vm-print-license
```