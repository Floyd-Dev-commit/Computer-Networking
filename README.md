# Computer-Networking
Computer Networking Laboratory ProjectsThis repository contains a collection of laboratory projects from the Computer Networking course. 

The projects cover a wide range of topics, from physical layer hardware construction to application layer protocol analysis and network device configuration.

2. Protocol Analysis with WiresharkObjective: Capture and analyze live network traffic to understand packet structures.Key Focus: * Analysis of IP datagram formats and MAC address variations across hops.Detailed inspection of the TCP three-way handshake and HTTP request/response cycles.Study of IPv4 addressing classes (A, B, and C).

3. DNS (Domain Name System) ResolutionObjective: Tracing the iterative resolution process of domain names.Tools: dig command in Linux.Mechanism: Understanding how requests move from Root Servers to TLD (.cn) and finally to Authoritative Name Servers (e.g., hdu.edu.cn) to retrieve IP addresses.

4. Socket Programming (Python)Objective: Implementing basic network communication using the Socket API.Features:UDP: Connectionless, high-speed transfer for real-time applications.TCP: Connection-oriented, reliable transfer involving handshake and release procedures.Implementation of echo servers that transform lowercase input into uppercase.

5. Switch & Router Configuration (Cisco IOS)Objective: Mastering the Command Line Interface (CLI) for network infrastructure devices.Configurations:Modes: Navigation between User, Privileged, Global Configuration, and Interface modes.Management: Setting hostnames, Message of the Day (MOTD) banners, and interface speeds.Routing: Interface IP assignment, enabling ports (no shutdown), and verifying routing tables.Persistence: Saving running configurations to startup configurations.

#Advanced Part
This section of the repository focuses on enterprise-level network configurations, including VLAN management, advanced NAT, dynamic routing protocols, and network security through traffic control.

1. VLAN & Inter-VLAN Routing
Cross-Switch VLANs: Implemented VLAN tagging and configured Trunk links between switches to enable communication across separated physical locations.

Router-on-a-Stick: Configured router sub-interfaces and IEEE 802.1Q encapsulation to allow routing between different VLANs.

2. Network Address Translation (NAT)
Static NAT: Established one-to-one permanent mappings between internal private IPs and external public IPs.

Dynamic NAT: Configured address pools and Access Control Lists (ACLs) to dynamically assign public IP addresses to internal hosts, optimizing the use of public IP space.

3. Dynamic Routing Protocols
RIP (Routing Information Protocol): Configured RIPv2 for automated route updates between routers in smaller network environments.

OSPF (Open Shortest Path First): Implemented OSPF in single-area environments (Area 0), demonstrating efficient route calculation and link-state management.

4. Traffic Control & Security
Standard ACLs: Applied IP-based standard Access Control Lists to permit or deny traffic from specific subnets, enhancing network security and resource management.
