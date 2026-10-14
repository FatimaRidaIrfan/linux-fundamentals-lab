# Linux Networking

## 1. Introduction to Linux Networking

Linux networking allows a computer to communicate with other computers, servers, and devices over a network. A network can be a local network (LAN) or a larger network such as the internet. Linux provides commands and tools to inspect network connections, manage network interfaces, check IP addresses, and troubleshoot connectivity problems.

Important Networking Terms : 

- Network: A group of connected devices that communicate with each other.
- IP Address: It is used to identify a device or network interface.
- Network Interface: A physical or virtual connection through which a device communicates over a network.
- Gateway: A device that forwards traffic from one network to another.
- DNS: Domain Name System, which translates domain names into IP addresses.
- DHCP: Dynamic Host Configuration Protocol, which automatically provides network configuration to devices.

## 2. Network Interfaces in Linux

A network interface is the point through which a Linux system sends and receives network traffic.

Common examples include:

- `lo` — The loopback interface used for communication within the same computer.
- `eth0` — A commonly used name for an Ethernet interface.
- `wlan0` — A commonly used name for a wireless interface.
- `enp0s3` — An interface name often seen in virtual machines.

Interface names depend on the system and its configuration.

Useful Commands 

| Command | Purpose | 
| --- | --- | 
| `ip link` | Displays network interfaces and their link states. | 
| `ip -br link` | Displays a brief summary of network interfaces. | 
| `ip -br addr` | Displays a brief summary of network interfaces and their IP addresses. | 
| `ip addr` | Displays `IP` address information for network interfaces. | 

## 3. IP Addresses 

An `IP` address identifies a network interface for communication using the Internet Protocol. 

There are two main versions of `IP` addresses:

- `IPv4`: Uses a 32-bit address. Example: `192.168.1.10`.

- `IPv6`: Uses a 128-bit address. Example: `2001:db8::10`.

An `IP` address helps identify where network traffic should be delivered.

## 4. Viewing IP Addresses

Linux provides the `ip` command to inspect and manage network configuration.

Examples : 

- `ip addr` 
- `ip -br addr`
- `ip link` 

The ip addr command displays information such as : 
- Network interface names 
- `IPv4` and `IPv6` addresses 
- Interface states 

The `ip -br addr` command presents a shorter summary that is easier to read.

## 5. Default Gateway and Routing

A routing table tells Linux where to send network packets. A default gateway is used when traffic does not match a more specific route and the routing table contains a suitable default route.

Useful Commands 

- `ip route` 
- `ip route show default` 

The default route is commonly used to reach destinations outside the local network.

## 6. Basic Network Troubleshooting 

Linux provides several commands to help identify network connectivity problems.

| Command | Purpose | 
| --- | --- | 
| `ping` | Tests reachability by sending ICMP Echo Requests. | 
| `ip route` | Displays routing information. | 
| `ss` | Displays socket information. |
| `hostname` | Displays or manages the system's hostname. | 

Examples 

- `ping -c 4 127.0.0.1`
- `hostname`
- `ss -tuln`

`ping -c 4 127.0.0.1` sends four ICMP Echo Requests to the local loopback address.
`hostname` displays the system's hostname.
`ss -tuln` displays listening `TCP` and `UDP` sockets with numeric addresses and ports.

## 7. Key Takeaways  

- Linux networking enables communication between devices.
- `IP` addresses identify network interfaces for IP communication.
- `IPv4` uses 32-bit addresses, while `IPv6` uses 128-bit addresses.
- A routing table determines where packets should be sent.
- A default gateway commonly connects a local network to other networks.
- `DNS` translates domain names into `IP` addresses.
- `DHCP` can automatically provide network configuration.
- The `ip` command is essential for inspecting Linux network settings.
- Commands such as `ping`, `ip route`, and `ss` help with troubleshooting.