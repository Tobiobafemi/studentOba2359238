Week 7 Journal – Network Configuration and Performance Analysis


All practical evidence, command outputs, and results referenced in this journal are provided in a separate screenshots file submitted alongside this document.

1. Introduction


This journal documents the completion of Week 7 practical tasks focusing on Linux network configuration, interface inspection, routing verification, and network performance analysis. The tasks were carried out on an Ubuntu 25.10 system using standard Linux networking and benchmarking tools. Screenshots have been captured at each stage to evidence correct command execution and results.

2. Network Interface Identification (Task 1.1)


To identify available network interfaces and their states, the command ip link show was used. This displayed all interfaces present on the system along with their operational status (UP/DOWN), MAC addresses, and link types.


From the output, the following interfaces were identified:

    lo – Loopback interface, used for internal communication.

    enp87s0 – Wired Ethernet interface, present but not connected (NO-CARRIER).

    wlp86s0 – Wireless network interface, active and in use.

    virbr0 – Virtual bridge interface associated with virtualisation.


The wireless interface wlp86s0 was confirmed as the primary active interface, shown in the UP state with an assigned MAC address. This interface was used for all subsequent networking and performance tests.

3. Interface Addressing and Configuration (Task 1.2 & 3.5)


To inspect detailed IP addressing information, the command ip addr show wlp86s0 was used. This provided both IPv4 and IPv6 configuration details.


The system was assigned a dynamically allocated IPv4 address in the 172.20.10.0/28 subnet. The presence of a valid subnet mask and broadcast address confirms correct DHCP configuration. An IPv6 link-local address was also shown, indicating dual-stack capability.


To review persistent network configuration, the directory /etc/netplan/ was listed using ls /etc/netplan/. Multiple YAML configuration files were present, confirming that Netplan is used for network management on this system. Attempts to read these files without elevated privileges resulted in permission denied messages, which is expected behaviour.

4. Interface Statistics and Traffic Monitoring (Task 2)


Network interface statistics were examined using the command ip -s link show. This displayed transmitted (TX) and received (RX) packet counts, byte totals, and error statistics.


The active interface wlp86s0 showed steadily increasing RX and TX values during testing, with zero packet errors or dropped packets recorded. This indicates a stable and reliable network connection during the practical session.


Additional live monitoring was carried out using a custom Bash script executed via nano. This script periodically recorded latency, active TCP connections, and interface byte counters while performance tests were running. Output was logged to a timestamped file for later analysis.

5. Network Latency Testing


Latency was measured using the ping command targeting the local host address 127.20.10.7. Extended tests were run with outputs redirected to a file for analysis.


Results showed:

    0% packet loss
Average round-trip time consistently below 0.1 ms

    Very small jitter between minimum and maximum values


These results indicate excellent local network responsiveness and negligible latency.

6. Network Throughput Testing with iPerf3


Network throughput was evaluated using iperf3 in both client and server modes. The server was started using iperf3 -s, and multiple client tests were executed using:

    iperf3 -c 127.20.10.7 -t 30

    Reverse mode testing using -R

    Parallel stream testing using -P

    UDP testing with bandwidth caps


Across multiple test runs, throughput consistently reached values above 60 Gbps during TCP testing. Minor throughput fluctuations were observed during parallel and UDP tests, which is expected under high concurrency.


Overall, the results indicate that the network stack and virtualised environment can sustain very high data transfer rates without significant packet loss or retransmissions.

7. Web Server Performance Testing (ApacheBench)


An Apache HTTP server was verified as running using systemctl status apache2. The service was confirmed as active and listening on port 80.


Web performance testing was carried out using ApacheBench (ab) with increasing load levels:

    1,000 requests at concurrency 10

    2,000 requests at concurrency 50

    5,000 requests at concurrency 100

    10,000 requests at concurrency 100


Results showed:

    Zero failed requests across all tests

    Requests per second increasing with concurrency

    Average request times remaining below 4 ms even at high load

    Acceptable connection and processing times


Warnings regarding statistical deviation appeared at higher loads, which is normal during aggressive benchmarking and does not indicate functional issues.

8. Port Scanning and Firewall Verification


Port availability was verified using nmap -p 22,80,443 172.20.10.7. The results confirmed:

    Port 22 (SSH): open

    Port 80 (HTTP): open

    Port 443 (HTTPS): closed


Firewall rules were inspected using ufw status numbered, confirming that only required services were permitted. Active socket inspection using ss -tulnp further verified listening services and active connections.

9. File Transfer Performance Testing


Secure file transfer testing was conducted using scp to copy a 100 MB test file between hosts. Transfer times showed sustained speeds exceeding 4 GB/s, demonstrating efficient local data transfer and confirming network stability under load.

10. Analysis and Conclusion


All Week 7 tasks were completed successfully and fully evidenced. The system demonstrated:

    Correct network interface configuration

    Stable IP addressing and routing

    Excellent latency and throughput performance

    Reliable web server behaviour under high concurrency

    Secure and efficient file transfer capabilities


No significant network bottlenecks were identified. Performance degradation only occurred under extreme synthetic load, which is expected behaviour. Overall, the system meets and exceeds expected performance characteristics for the tested environment.
