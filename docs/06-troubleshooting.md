# 6. Troubleshooting Log

This section documents the key issues encountered and how they were resolved.

## Issue 1: Layer-2 Connectivity (ping to gateway failed)

**Symptom:** FortiGate could not ping `10.1.1.1` (the gateway) even with a correct IP.

**Root Cause:** VMware's bridged network (VMnet0) was set to "Automatic", which bound to the wrong physical adapter.

**Solution:** Manually set VMnet0 to the specific Wi‑Fi or Ethernet adapter in **Virtual Network Editor**.

## Issue 2: `curl 28` Licensing Timeout

**Symptom:** `execute vm-license` returned `curl forticare failed, 28`.

**Root Cause:** System time was incorrect (NTP not set), breaking the SSL handshake.

**Solution:** Enabled NTP, set the correct timezone, and ran `execute ntp-sync` before retrying.

## Issue 3: DNS Resolution Failure

**Symptom:** `ping support.fortinet.com` failed.

**Root Cause:** No DNS servers configured.

**Solution:** Set DNS to `8.8.8.8` and `8.8.4.4` in the FortiGate CLI.

## Issue 4: File System Check Prompt on Every Login

**Symptom:** GUI asked to run a system check after each unclean shutdown.

**Solution:** Shut down the VM gracefully using `execute shutdown` instead of powering off from VMware. Run `execute fsck` (if available) or simply click "Skip" – the check is unnecessary for a fresh VM.