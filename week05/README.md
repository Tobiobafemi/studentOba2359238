# System Security and Hardening Audit

## Module
System Security and Hardening

## Student ID
oba23592328

## System Details
- Operating System: Ubuntu Linux Server
- Server IP Address: 127.20.10.7
- Audit Tool: Lynis (v3.1.4)

---

## Project Overview

This repository documents a practical security audit and hardening exercise
performed on an Ubuntu Linux server. The assessment follows a structured
approach including initial security auditing, analysis of findings, security
prioritisation, implementation of hardening measures, and post-hardening
verification.

The work demonstrates the application of defence-in-depth principles using
industry-standard tools and best practices.

---

## Tasks Completed

### Part 1: Initial Security Assessment
- Installed and verified Lynis
- Performed full system security audit
- Recorded initial hardening index and warnings
- Analysed audit results and prioritised security issues

### Part 2: Network and Firewall Security
- Identified open ports (SSH on port 22)
- Verified firewall configuration using UFW
- Confirmed blocked ports cannot be accessed
- Analysed running and listening services

### Part 3: Security Hardening Implementation
- Implemented kernel security hardening (sysctl parameters)
- Applied file system security controls
- Strengthened password and authentication policies
- Re-ran Lynis audit to verify improvements

---

## Audit Summary

- Initial Hardening Index: 68 / 100
- Final Hardening Index: 68 / 100
- Initial Warnings: 2
- Remaining Warnings After Hardening: 0
- Total Tests Performed: 265

Although the hardening index did not increase numerically, all identified
security warnings were resolved, resulting in an improved security posture.

---

## Repository Contents

- Journal entries documenting each task and security decision
- Analysis and comparison of pre- and post-hardening results
- Configuration changes applied during hardening
- Supporting documentation for audit verification

---

## Screenshot Evidence

**IMPORTANT**

All screenshot evidence (Lynis scans, firewall status, command outputs, etc.)
is stored in a **separate submission file** and is **not included in this Git
repository**.

This is intentional to:
- Keep the repository lightweight
- Avoid committing large binary image files
- Maintain clean version control history

Screenshot evidence is provided alongside this repository as part of the
formal coursework submission.

---

## Tools Used

- Lynis
- UFW (Uncomplicated Firewall)
- nmap
- systemctl, ss, netstat
- Standard Linux command-line utilities

---

## Notes

This repository contains original coursework completed by the student listed
above. All scans and tests were conducted on systems owned or controlled by
the student in an isolated environment.
