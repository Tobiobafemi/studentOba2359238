# Assessment Week 1 – Phase 1
## System Planning and Distribution Selection

Module: Operating Systems
Student: Tobi
Week: 01

---

## 1. System Architecture Diagram

This system uses a dual-boot configuration with Ubuntu 25.10 and Windows installed on the same physical machine. Ubuntu is used as the primary operating system for this coursework.

Ubuntu connects directly to the network using the physical network adapter (Wi-Fi/Ethernet), allowing access to local and internet resources without virtualisation.

[Diagram to be added in GitHub repository]

---

## 2. Distribution Selection Justification

Ubuntu was selected as the operating system due to its stability, strong community support, and widespread use in industry and education.

Compared to Debian, Ubuntu provides easier configuration and more up-to-date software packages. Compared to Windows Server, Ubuntu is open-source, lightweight, and does not require licensing costs.

These factors make Ubuntu a suitable choice for system deployment and learning purposes.

---

## 3. Workstation Configuration Decision

The system uses a dual-boot configuration, allowing Ubuntu to run directly on physical hardware alongside Windows. This setup provides full access to system resources without virtualisation overhead.

Running Ubuntu directly on hardware improves performance and closely reflects real-world system administration environments.

---

## 4. Network Configuration

The Ubuntu system connects directly to the network using the physical network adapter. Network configuration was verified using the `ip addr` command.

The system was assigned the IPv4 address:

192.168.122.1/24

This confirms that the system has an active and functional network connection.

---

## 5. System Specifications (CLI Evidence)

The following commands were executed in the Ubuntu terminal to document system specifications.

### 5.1 Kernel Information – uname -a
This command confirms the Linux kernel version and system architecture.

---

### 5.2 Memory Usage – free -h
This command displays total, used, and available system memory.

---

### 5.3 Disk Usage – df -h
This command shows disk usage and available storage across mounted file systems.

---

### 5.4 Network Interfaces – ip addr
This command displays network interfaces and assigned IP addresses.

---

### 5.5 Operating System Version – lsb_release -a
This command confirms the installed Ubuntu version and codename.

---

End of Week 01 Journal.
