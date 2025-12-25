# Linux Server Security Hardening and Monitoring

This repository documents the implementation of Linux server security hardening and monitoring using Bash scripting and native Ubuntu security tools.

All supporting evidence (command outputs, configuration verification, and script execution results) is provided in a separate `screenshots/` directory. Scripts referenced below are located in the `scripts/` directory.

---

## Project Overview

This project demonstrates a defence-in-depth approach to Linux server security and administration. All required coursework tasks have been completed, tested, and verified.

The implementation includes:
- Mandatory Access Control using AppArmor
- Intrusion detection and prevention using Fail2Ban
- Automatic security updates
- A security baseline verification script
- A remote server monitoring script using SSH

---

## Mandatory Access Control (AppArmor)

AppArmor was used to implement Mandatory Access Control on the system.

The AppArmor service was verified as installed and active, with profiles loaded and enforced. This ensures applications are restricted according to predefined security policies, providing stronger protection than standard Discretionary Access Control alone.

Relevant verification outputs can be found in the screenshots directory.

---

## Intrusion Detection and Automatic Updates

Fail2Ban was installed and enabled to protect against brute-force attacks. The SSH (`sshd`) jail was configured and confirmed as active, monitoring authentication logs and applying temporary bans to offending IP addresses.

Automatic security updates were configured using `unattended-upgrades`. The service was installed, enabled, and verified to ensure that security patches are applied automatically without manual intervention.

Configuration checks and service status outputs are included in the screenshots directory.

---

## Security Baseline Verification Script

The script `security-baseline.sh` provides a consolidated security check of the server. It validates that key security controls are correctly configured and produces a formatted security report.

### Security Checks Performed
- SSH configuration (password authentication, root login, public key authentication)
- Firewall (UFW) status and active rules
- Fail2Ban service and SSH jail status
- Mandatory Access Control status
- Administrative users with sudo privileges
- Automatic security updates
- System memory and disk usage

### Execution
```bash
chmod +x scripts/security-baseline.sh
./scripts/security-baseline.sh

