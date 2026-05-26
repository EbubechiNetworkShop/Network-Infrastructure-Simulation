# Network-Infrastructure-Simulation
Secure multi zoned virtual network leveraging security features and structures such as pfSense, Pi-hole, and segmentation. (Still under experimentation)
# Secure Multi-Zone Homelab Network Infrastructure

## 📋 Project Overview
Designed, engineered, and deployed an enterprise-grade, multi-zone network architecture inside an isolated hypervisor environment to simulate modern corporate segmentation and traffic monitoring.

## 🗺️ Architectural Topography
* **WAN Interface:** Configured via a Bridged Adapter to the host machine to securely negotiate internet traffic via an external Double-NAT gateway.
* **LAN Zone (IT Management):** `10.10.0.0/24` — Dedicated administrative management plane hosting secure hosts.
* **IoT Zone:** Segmented subnet designed to isolate automated device traffic.
* **Public Guest Zone:** Low-trust isolated environment restricted from lateral local area communication.

## 🛡️ Enforced Security Implementations (ACL Logic)
* **Zero Trust Policy Enforcements:** Configured strict ingress-filtering firewall rules inside pfSense to prioritize precise host communication (e.g., dedicated Windows management access) while maintaining a strict stateful blocking posture on the WAN against unsolicited external discovery.
* **Stateful Traffic Monitoring:** Leveraged pfSense's stateful inspection engine on the `IT_MANAGEMENT_ADMIN` interface to permit secure outbound transactions while actively shielding internal assets from lateral movement.

## 🔧 Engineering Log & Diagnostic Wins
1. **Hypervisor Packet Filtration Resolution:** Diagnosed an infrastructure packet-dropping anomaly by shifting VirtualBox Promiscuous Mode configurations from *Deny* to *Allow All*, clearing the block on custom VLAN tags and unmapped headers.
