Journal 1: Initial Security Assessment with Lynis


The initial security assessment was conducted using the Lynis auditing tool on the Ubuntu Linux server. Lynis was installed using the system package manager and a full system audit was performed using the sudo lynis audit system command. The audit completed successfully after several minutes and produced a detailed report outlining the system’s current security posture.


The initial Lynis scan reported a hardening index of 68 out of 100, with 265 tests performed. The audit identified two security warnings and several additional suggestions. These warnings indicated areas where system configuration did not fully align with recommended security best practices and required further investigation.


The initial assessment provided a baseline against which later hardening efforts could be measured. Capturing the initial audit report allowed for a structured comparison before and after security improvements were implemented.

Journal 2: Analysis of Lynis Results


Following the initial audit, the Lynis log file was analysed to extract key metrics, including the hardening index, warnings, and suggestions. Command-line tools such as grep and wc were used to identify and count warnings and suggestions within the audit log.


The presence of warnings highlighted specific security weaknesses that required prioritisation. Although suggestions are advisory in nature, warnings represent more immediate risks and were therefore treated as higher priority. Reviewing these outputs helped to better understand the areas where the system was vulnerable and informed decisions on which security controls should be applied first.


This analysis stage was essential in translating raw audit output into actionable security improvements.

Journal 3: Security Prioritisation Matrix


Based on the Lynis audit results, security issues were categorised using a prioritisation matrix. Issues that posed a higher security risk and required minimal effort to resolve were classified as high priority, while less critical or more complex changes were classified as medium or low priority.


The two Lynis warnings were classified as high priority, as they represented concrete security weaknesses and could be resolved through configuration changes. Suggested improvements that did not pose immediate risk were treated as lower priority and documented for future implementation.


This prioritisation ensured that the most impactful security improvements were addressed first, improving overall system security efficiently.

Journal 4: Network Security Assessment (nmap)


A network security assessment was conducted using the nmap tool to identify open ports and exposed services on the server. The scan revealed that port 22 (SSH) was open, which is required for remote system administration.


No unnecessary ports were identified as open. This indicates that the system’s network exposure is minimal and appropriately restricted. Documenting open ports is important to ensure that only essential services are accessible and to reduce the attack surface.


The results of the network scan confirmed that the server was not exposing unintended services to the network.

Journal 5: Firewall Verification


The firewall configuration was reviewed using UFW (Uncomplicated Firewall). The firewall status and rules were examined using commands such as ufw status numbered and ufw status verbose.


The firewall was confirmed to be active, with default policies configured to deny incoming connections unless explicitly allowed. Tests were performed by attempting connections to blocked ports, which correctly failed, demonstrating that the firewall was functioning as intended.


This verification confirmed that unauthorised network access was being effectively blocked, contributing to the overall security posture of the system.

Journal 6: Service Inventory and Analysis


A service inventory was conducted to identify all running and listening services on the server. Commands such as ss, netstat, and systemctl were used to enumerate active services.


The analysis showed that only essential services were running, with SSH being the primary externally accessible service. No unnecessary services were identified for removal. Maintaining a minimal service footprint is important as each running service represents a potential attack vector.


This step confirmed that service minimisation principles were being followed.

Journal 7: Kernel Security Hardening


Kernel security hardening was implemented by modifying system control parameters in /etc/sysctl.conf. Several parameters were adjusted to improve protection against network-based attacks, including disabling IP forwarding, disabling ICMP redirects, enabling TCP SYN cookies, and enabling IP spoofing protection.


These changes improve resilience against denial-of-service attacks, packet spoofing, and network misconfiguration abuse. Kernel-level hardening provides an additional layer of security that operates independently of user-space controls.


All changes were applied and verified to be active.

Journal 8: File System Security Hardening


File system security was enhanced by securing shared memory using restrictive mount options, reducing the risk of executable code being run from shared memory. Checks were also performed to identify world-writable files and files without an owner, as these can pose serious security risks.


SUID and SGID files were reviewed, as these files run with elevated privileges and can be abused for privilege escalation if misconfigured. No critical issues were identified, but the inventory was documented for audit purposes.


These actions reduce the risk of privilege escalation and unauthorised file manipulation.

Journal 9: Password and Authentication Hardening


Password security was strengthened by enforcing stricter password quality requirements using pwquality.conf. A minimum password length of 12 characters was enforced, along with complexity requirements for uppercase, lowercase, numeric, and special characters.


Password ageing policies were also configured to require regular password changes and provide advance warnings before expiry. Account lockout controls were introduced to limit the number of failed login attempts.


These measures significantly reduce the risk of brute-force and credential-based attacks.

Journal 10: Post-Hardening Verification


After implementing security hardening measures, the Lynis audit was re-run to verify improvements. The post-hardening audit reported a hardening index of 68 out of 100, unchanged from the initial score. However, all previously identified warnings were resolved, reducing the number of warnings from 2 to 0.


Although the numerical hardening index did not increase, the elimination of warnings demonstrates a tangible improvement in system security. This highlights that Lynis scoring is weighted and that not all fixes result in immediate score increases.


Overall, the system is now more secure and aligned with security best practices.

Final Reflection


This practical exercise demonstrated the importance of systematic security auditing, prioritisation, and verification. While automated tools such as Lynis provide valuable insight, meaningful security improvements come from understanding and acting on audit findings rather than focusing solely on numerical scores.
