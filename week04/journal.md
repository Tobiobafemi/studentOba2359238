Linux Server Security Hardening and Monitoring Journal


Introduction


The aim of this coursework was to explore practical Linux server security by implementing multiple defensive mechanisms and automation techniques. The tasks focused on securing a Linux system using built-in security tools, monitoring for malicious activity, automating updates, and creating custom Bash scripts to verify and monitor system security.


A defence-in-depth approach was applied throughout the coursework, combining Mandatory Access Control, intrusion detection, automatic patching, security auditing, and remote monitoring. All tasks were implemented and verified on an Ubuntu-based system.


All supporting evidence, including command outputs, configuration verification, and script execution results, is provided separately in the screenshots directory.

Task 1: Mandatory Access Control Using AppArmor


Mandatory Access Control (MAC) was implemented using AppArmor. Unlike Discretionary Access Control (DAC), which relies on user ownership and file permissions, MAC enforces centrally defined security policies that cannot be overridden by users or compromised processes.


The AppArmor service was first checked to ensure it was installed and active. System status output confirmed that the AppArmor kernel module was loaded and that multiple profiles were present on the system. Profiles were observed to be running primarily in enforce mode, meaning policy violations would be actively blocked rather than only logged.


Additional checks were carried out to list profiles running in enforce and complain modes. This demonstrated how AppArmor supports both strict enforcement and policy testing. Enforce mode prevents unauthorised actions, while complain mode logs violations without blocking them, allowing administrators to refine policies safely.


A specific AppArmor profile was inspected directly from the /etc/apparmor.d/ directory. Reviewing the profile structure revealed explicit allow and deny rules for file access, network permissions, and Linux capabilities. This demonstrated the principle of least privilege in practice, ensuring that services only have access to resources they require.


This task highlighted the importance of Mandatory Access Control in limiting the impact of potential compromises by restricting application behaviour beyond standard Linux permissions.

Task 2: Intrusion Detection with Fail2Ban


To protect the system from brute-force attacks, Fail2Ban was installed and configured. Fail2Ban works by monitoring system log files for repeated authentication failures and automatically banning offending IP addresses.


After installation, the Fail2Ban service was verified to be active and enabled at system startup. Configuration was performed by copying the default configuration file to a local configuration file, following best practices to avoid overwriting custom settings during updates.


The SSH (sshd) jail was enabled to monitor failed login attempts. Configuration parameters such as maximum retries, ban duration, and detection time windows were reviewed to balance security and usability.


Fail2Ban status checks confirmed that the SSH jail was active and monitoring authentication logs. Log files were examined to verify that Fail2Ban was correctly parsing authentication failures and ready to apply bans when thresholds were exceeded.


This task demonstrated how automated intrusion detection significantly reduces the effectiveness of brute-force attacks while requiring minimal administrative intervention.

Task 2: Automatic Security Updates


To reduce exposure to known vulnerabilities, automatic security updates were configured using the unattended-upgrades package. This ensures that critical security patches are applied automatically without requiring manual updates.


The package was installed and configured to enable automatic installation of security updates only. Service status checks confirmed that unattended-upgrades was running correctly in the background.


Configuration files were reviewed to verify which repositories and update types were included. Log files were examined to confirm that updates were being applied as expected.


While automatic updates introduce a small risk of compatibility issues, limiting updates to security patches provides a balanced approach that improves system security while maintaining stability.

Task 3.1: Security Baseline Verification Script


A custom Bash script, security-baseline.sh, was created to provide a consolidated security assessment of the system. The purpose of this script is to quickly verify that essential security controls are correctly configured.


The script performs a series of checks, including SSH security configuration, firewall status, Fail2Ban service status, AppArmor enforcement, administrative user accounts, automatic updates, and system resource usage.


Each check produces clear output indicating whether the configuration is secure or requires attention. This allows administrators to quickly assess the system’s security posture after configuration changes or during routine audits.


The script was made executable and run successfully, producing a formatted security report. This task demonstrated how automation can improve consistency, reduce human error, and save time during security assessments.

Task 3.2: Remote Server Monitoring Script


A second Bash script, monitor-server.sh, was developed to perform remote server monitoring via SSH. Unlike the security baseline script, which runs locally, this script is designed to run from a workstation and collect metrics from a remote server.


The script defines the remote server connection and generates a timestamped log file for each execution. It uses SSH to remotely execute commands that collect system information, uptime, CPU usage, memory usage, disk usage, and service status.


Output is displayed in real time and written to a log file simultaneously. This allows both immediate monitoring and historical analysis of system performance and security.


The script was tested successfully, confirming SSH connectivity and correct data collection. This task demonstrated the value of automation and remote monitoring in system administration, reducing the need for repeated manual logins and enabling proactive system management.

Reflection


This coursework provided practical experience in securing and monitoring Linux systems using industry-standard tools. Implementing AppArmor highlighted the importance of Mandatory Access Control in limiting application behaviour. Fail2Ban demonstrated effective automated intrusion prevention, while unattended-upgrades reduced the system’s exposure to vulnerabilities.


Writing custom Bash scripts reinforced the role of automation in maintaining security consistency and operational efficiency. The combination of baseline verification and remote monitoring reflects real-world system administration practices.


Overall, this project demonstrated how layered security controls and automation can significantly improve the security and manageability of Linux server environments.

Conclusion


All coursework tasks were successfully completed and verified. The system was hardened using Mandatory Access Control, intrusion detection, and automatic patching. Custom scripts were developed to verify security configurations and monitor the system remotely.


This project demonstrates a defence-in-depth approach to Linux server security and provides a strong foundation for real-world system administration and cybersecurity practices.
