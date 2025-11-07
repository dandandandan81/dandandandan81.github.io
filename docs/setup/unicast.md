# ROOMNET Apple TV Network Requirements: For Configurations With No Multicast.

This Guide is specifically for installations without Multicast IPTV.
If this does not match the install scenario choose the correct scenario from the [setup guide](index.md).

All sections are relevant, if a requirement cannot be met please notify your project manager so we can work on a solution.


## Core Network Foundation

This section covers the fundamental network infrastructure, including dedicated networks, IP addressing, and hardware specifications.

### Dedicated Network Infrastructure

**Dedicated VLAN:** 

- The IPTV network must operate on a dedicated VLAN that spans the entire property as one unified network. This VLAN should *NOT* be the default VLAN (typically VLAN 1). If additional devices beyond the IPTV streamer and ROOMNET provided equipment are to be included in the VLAN, inform your project manager so we can evaluate any impact to the solution.

**Public IP Addresses:**

- All outbound traffic should be routed via a single Public IP address. This does not need to be dedicated to only the IPTV solution. Multiple Static IPs can be accommodated but may require additional configuration on your network.
- The dynamic top-shelf configuration relies on the public IP address of each Apple TV for communication with ROOMNET's cloud infrastructure. To ensure the correct branding is shown on screen, each property needs to use unique public IPs
- If static public IPs are not available this will reduce branding opportunities within the solution.

**Hardware:**

- We recommend enterprise-grade networking hardware throughout the IPTV/Apple TV network. This includes manufacturers such as Cisco, Ruckus, and HP/Aruba.
- There are issues with the implementation of IGMP in Unifi and TP-link hardware. Issues range from challenges with initial configuration to general stability issues. As such we recommend these brands are avoided. If assistance is needed in configuring this network hardware there may be additional charges.
- All copper edge ports AppleTVs must be Gigabit throughout the network.
- All uplink ports between switching hardware should Gigabit or better. Preferably 10GB or better.

### Network Connectivity & Traffic Management

**Wired Connectivity:** Ensure wired gigabit network connectivity for all in-room hardware.

**Outbound Traffic:** The IPTV VLAN must have no outbound restrictions. This network should be managed similarly to guest HSIA networks, meaning no filtering, proxies, packet inspection, or other technologies that could interfere with outbound network traffic. Restrictions to inbound traffic are allowed.

## Essential Services & Servers

This section details the critical services and servers required for the Apple TV solution to function correctly.

### ROOMNET Caching Server

**Purpose:** 

This server is a MacMini that utilizes Apple's caching service along with custom ROOMNET configurations. It's primary roles are:

- Local node for ROOMNET and Apple CDN, improving deployment speed and asset loading for guests.
- Primary DNS Server for the IPTV VLAN
- A remote access and support tool.

**Location & Access:** The caching server must be accessible by all Apple TVs with bi-directional communication and should exist within the same VLAN as the Apple TVs.

**IP Addressing:** The caching server has a single NIC but requires two static local IP addresses.

### DNS Configuration

**Primary DNS:** The ROOMNET caching server will provide Primary DNS services for the IPTV network.

**Additional DNS:** ROOMNET will provide secondary and tertiary DNS servers during the project phase. It is crucial to not add additional DNS servers, as this will negatively affect platform performance.

### DHCP Management

**Requirement:** 

The IPTV VLAN requires DHCP for the AppleTVs ensure the scope is large enough to accommodate all devices.

**IP Assignment:** 

Manual IP addresses for IPTV endpoints cannot be used because devices are wiped after checkout. However, it is acceptable to use DHCP reservations via MAC address. A complete list of MAC addresses cannot be made available until all Apple TVs have been enrolled in MDM.

## Switch & Port Optimizations

This section outlines specific switch and port configurations needed for optimal performance and management of Apple TV traffic.

### Port-Fast

**Requirement:** 

At check out the AppleTVs in the associated room are reset and automatically rebuild. On reboot it is important the AppleTVs are able to access the WAN immediately. If this is not possible the AppleTVs may not automatically rebuild and require manual intervention.

**Solution:** 

Enable Port Fast on all access/edge ports an AppleTV is going to be connected to.

!!! info
     If spanning tree is not configured, this step is unnecessary.

### mDNS Traffic Management

**Issue**

Apple devices generate significant background traffic via mDNS. When many Apple TVs are on a single VLAN, this can cause resource issues in switches and AppleTVs resulting in poor performance. If you have a converged network, it can affect other services running on the switch hardware.

**Solution:** 

To avoid these issues, apply ACLs (Access Control Lists) to block IPv4 and IPv6 mDNS traffic. Whilst it is not possible to provide instruction for every brand of switch the traffic that needs to be blocked is listed below:


IPv4:  
Destination IP: 224.0.0.251  
Destination Port: UDP 5353  
Protocol: UDP


IPv6:  
Destination IP: ff02::fb  
Destination Port: UDP 5353  
Protocol: UDP


Example Rules
```
deny udp any host 224.0.0.251 eq 5353
deny udp any host ff02::fb eq 5353
```

!!! warning
    IPv6 ACLs are required even if you do not actively have IPv6 setup on your network


**Application:** 

Apply these restrictions to the edge ports where Apple TVs connect. If that is not possible, apply them to uplink ports to contain mDNS traffic to each switch.

**Caution:** 

Avoid general port isolation commands, as they can disrupt MDM connections and other functions.

## Bandwidth & Performance

Compared to a traditional TV based IPTV system the bandwidth requirements of the ROOMNET solution are higher, this is due to a larger range of apps and content made available to the guest.

### Bandwidth Recommendations

**Efficiency:** 

Apple TVs are generally efficient in WAN bandwidth usage. Most applications do not require constant streaming from external sources, and video content (except live TV) is typically downloaded in chunks using protocols like DASH or HLS.

**Recommendation:** 

We recommend 5 Mbps per device to ensure a consistently good experience for all guests.

**Management:** 

Avoid per-device bandwidth restrictions, as they complicate management and updates. If there are concerns over bandwidth availability or management, discuss these with your account or project manager.