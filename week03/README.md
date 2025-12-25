# Week 03 – Initial Security Configuration Lab Journal

Student: Tobi obafemi
Module: Infrastructure, Processes and Control
System: Ubuntu 25.10 (GNU/Linux 6.17.x)
Week: 03

----------------------------------------------------------------

Evidence Location

All screenshot evidence referenced in this journal is stored separately
in the GitHub repository under the following directory:

/week03/screenshots/

Each screenshot is clearly named according to the task it supports
(e.g. task1_1.png, task2_3.png) and includes visible command prompts
and outputs as required.

----------------------------------------------------------------

Part 1: Process Fundamentals and Management

----------------------------------------------------------------

Task 1.1: Exploring Process States

Objective:
To examine running processes on a Linux system and understand how
process states are represented.

Commands Used:
ps aux
ps -ef
top
htop

Explanation:
The ps aux command displays all running processes, showing ownership,
CPU usage, memory usage, and process state. The ps -ef command provides
a full-format listing with parent-child relationships.

Real-time process monitoring was carried out using top and htop, which
allowed observation of CPU and memory usage while processes were running.

Process States:
R - Running (actively executing on the CPU)
S - Sleeping (waiting for an event or resource)
D - Uninterruptible sleep (waiting for I/O)
Z - Zombie (terminated but not yet reaped)
T - Stopped (suspended via signal such as Ctrl+Z)

----------------------------------------------------------------

Task 1.2: Process Relationships and Control

Objective:
To explore process hierarchy and practise foreground and background
process management.

Commands Used:
pstree
pstree -p
sleep 300 &
jobs
sleep 500
Ctrl+Z
bg
fg
kill [PID]
killall sleep
nice -n 10 sleep 400 &
top

Explanation:
The pstree command was used to visualise parent and child process
relationships. Background processes were created using the ampersand (&)
operator, and job control commands such as bg and fg were used to manage
execution.

Process priority was adjusted using nice, demonstrating how CPU
scheduling can be influenced.

----------------------------------------------------------------

Part 2: SSH Key-Based Authentication

----------------------------------------------------------------

Task 2.1: Generating SSH Keys

Objective:
To generate a secure SSH key pair for authentication.

Command Used:
ssh-keygen -t ed25519 -C "email@example.com"

Explanation:
An ed25519 SSH key pair was generated. Ed25519 is recommended over RSA
because it provides strong security with smaller key sizes and improved
performance.

----------------------------------------------------------------

Task 2.2: Copying SSH Key to Server

Objective:
To enable passwordless SSH authentication.

Commands Used:
ssh-copy-id username@server_ip
ssh username@server_ip

Explanation:
The public key was copied to the server, allowing secure authentication
without entering a password. Successful login without a password prompt
confirmed correct configuration.

----------------------------------------------------------------

Part 3: SSH Hardening and Firewall Configuration

----------------------------------------------------------------

Task 2.3: Hardening SSH Configuration

Objective:
To reduce the attack surface of the SSH service.

Commands Used:
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
sudo nano /etc/ssh/sshd_config
sudo systemctl restart sshd

Configuration Changes:
PasswordAuthentication no
PubkeyAuthentication yes
PermitRootLogin no

Verification:
After restarting the SSH service, login attempts prompted for the SSH
key passphrase rather than a user password. This confirms that password
authentication was successfully disabled.

Security Justification:
Disabling password authentication prevents brute-force attacks.
Public key authentication provides stronger cryptographic security.
Disabling root login enforces the principle of least privilege.

----------------------------------------------------------------

Task 3.1: Implementing Firewall Rules

Objective:
To restrict network access using UFW.

Commands Used:
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from <workstation_ip> to any port 22
sudo ufw enable
sudo ufw status verbose

Explanation:
Incoming connections are denied by default, and SSH access is restricted
to a trusted workstation IP. This significantly reduces exposure to
unauthorised access.

----------------------------------------------------------------

Part 4: User and Privilege Management

----------------------------------------------------------------

Task 3.2: User and Privilege Management

Objective:
To apply the principle of least privilege by using a non-root
administrative user.

Commands Used:
sudo adduser adminuser
sudo usermod -aG sudo adminuser
groups adminuser
id adminuser
su - adminuser
sudo apt update
whoami
getent group sudo

Explanation:
A non-root administrative account was created and added to the sudo
group. Administrative tasks require explicit privilege escalation,
reducing the risks associated with direct root access.

This approach improves system security, accountability, and auditability.

----------------------------------------------------------------

Part 5: Remote Administration Evidence

----------------------------------------------------------------

Task 3.3: Remote Administration via SSH

Objective:
To demonstrate secure remote system administration.

Commands Used:
ssh username@server_ip uname -a
ssh username@server_ip free -h
ssh username@server_ip df -h
ssh -t username@server_ip sudo ufw status
ssh username@server_ip systemctl status sshd

Explanation:
Administrative commands were successfully executed remotely via SSH,
demonstrating secure access with enforced authentication and privilege
separation.

----------------------------------------------------------------

Conclusion

This lab implemented multiple layers of system security, including:
- Secure process monitoring and control
- SSH key-based authentication
- Hardened SSH configuration
- Firewall enforcement using UFW
- Least-privilege user management
- Secure remote administration

All configurations were validated using command output and are supported
by screenshot evidence stored in the GitHub repository.
