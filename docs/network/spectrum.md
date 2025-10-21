# ROOMNET Apple TV Network Requirements: For Networks without Multicast TV

The ROOMNET Apple TV solution is cloud-based and enables users to stream their favorite content. A robust and correctly configured network is essential for a good user experience.

## Core Network Foundation

This section covers the fundamental network infrastructure, including dedicated networks, IP addressing, and hardware specifications.

### Dedicated Network Infrastructure

**Dedicated VLAN:** The IPTV network must operate on a dedicated VLAN that spans the entire property as one unified network. This VLAN should *NOT* be the default VLAN (typically VLAN 1). If additional services beyond TV systems are required on the IPTV VLAN, inform your project manager to ensure no impact on the TV solution.

**Public IP Addresses:**
- A dedicated static public IP address per property is required for the TV solution.
- The dynamic top-shelf configuration relies on the public IP address of each Apple TV for communication with ROOMNET's cloud infrastructure.
- Each property must use a unique public IP.
- A maximum of two separate public IP blocks per location is supported.
- If more than one public IP is used, notify your project manager or ROOMNET as soon as possible for the necessary additional DHCP configuration.

**Hardware:**
- We recommend enterprise-grade networking hardware throughout the IPTV/Apple TV network. This includes manufacturers such as Cisco, Ruckus, and HP/Aruba.
- All copper edge ports Apple TVs must be Gigabit throughout the network.
- All uplink ports between switching hardware should Gigabit or better.

### Network Connectivity & Traffic Management

**Wired Connectivity:** Ensure wired Gigabit network connectivity for all in-room hardware.

**Outbound Traffic:** The IPTV VLAN must have no outbound restrictions. This network should be managed similarly to guest HSIA networks, meaning no filtering, proxies, packet inspection, or other technologies that could interfere with outbound network traffic. There are no requirements for inbound configurations.

## Essential Services & Servers

This section details the critical services and servers required for the Apple TV solution to function correctly.

### ROOMNET Caching Server

**Purpose:** This server is a Mac Mini that utilizes Apple's caching service along with custom ROOMNET configurations. It hosts apps, firmware, and local replicas of assets such as branding, channel icons, and top-shelf content. It also provides a convenient way to investigate network issues.

**Location & Access:** The caching server must be accessible by all Apple TVs with bi-directional communication and should exist within the same VLAN as the Apple TVs.

**IP Addressing:** The caching server requires two static IP addresses.

### DNS Configuration

**Primary DNS:** The ROOMNET caching server will run as a virtual machine and act as the primary DNS server for the IPTV network. This allows local hosting of content like artwork and icons, improving the guest experience.

**Additional DNS:** ROOMNET will provide secondary and tertiary DNS servers during the project phase. It is crucial *NOT* to add additional DNS servers, as this will negatively affect platform performance.

### DHCP Management

**Requirement:** DHCP should be configured on the IPTV VLAN.

**IP Assignment:** Manual IP addresses for IPTV endpoints cannot be used because devices are wiped after checkout. However, it is acceptable to use DHCP reservations via MAC address. A complete list of MAC addresses cannot be made available until all Apple TVs have been enrolled in MDM.

## Switch & Port Optimizations

This section outlines specific switch and port configurations needed for optimal performance and management of Apple TV traffic.

### Port-Fast Configuration

**Requirement:** All switch ports with Apple TVs connected should have port-fast enabled.

**Caution:** Not enabling port-fast may result in Apple TVs failing to configure automatically after a checkout.

**Note:** If spanning tree is not configured, this step is unnecessary.

### mDNS Traffic Management

**Issue:** Apple devices generate significant background traffic via mDNS. When many Apple TVs are on a single VLAN, this will slow content loading and hardware performance.

**Solution (ACLs):** To avoid these issues, apply ACLs (Access Control Lists) to block IPv4 and IPv6 mDNS traffic.

- Example IPv4 ACL: Deny host 224.0.0.251 port 5353 and permit all other UDP traffic.
- Example IPv6 ACL: Deny ff02::fb/128 any port 5353 and permit all other UDP traffic.

**Application:** Apply these restrictions to the edge ports where Apple TVs connect. If that is not possible, apply them to uplink ports to contain mDNS traffic to each switch.

**Caution:** Avoid general port isolation commands, as they can disrupt MDM connections and other functions.

## Bandwidth & Performance

This section provides recommendations for managing network bandwidth to ensure a consistent and high-quality guest experience.

### Bandwidth Recommendations

**Efficiency:** Apple TVs are generally efficient in WAN bandwidth usage. Most applications do not require constant streaming from external sources, and video content (except live TV) is typically downloaded in chunks using protocols like DASH or HLS.

**Recommendation:** We recommend 5 Mbps per device to ensure a consistently good experience for all guests.

**Management:** Avoid per-device bandwidth restrictions, as they complicate management and updates. If there are concerns over bandwidth availability or management, discuss these with your account or project manager.

## Spectrum Requirements

For the Spectrum network components an addtional Public IP is required. 
There will also need to be routing in place to allow communication between the Spectrum hardware and the Apple TVs

Further details of these requiremts will be provided by the Spectrum team.

