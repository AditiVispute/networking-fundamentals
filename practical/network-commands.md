# Basic Networking Commands (Practical)

This document includes some commonly used networking commands that are helpful for checking connectivity, identifying system network details and troubleshooting basic network related issues in a Linux environment.

---

## ping

  Use:
     This command is used to check whether the system is able to communicate with another device over the network.

  Command:
    ```bash
    ping google.com

  output
    64 bytes from 142.250.192.14: icmp_seq=1 ttl=115 time=18 ms

If the packets are received successfully, it means the network connection is working properly.

## ip a
   Use:
      Displays the IP address and other details related to the network interface of the system.

   Command:
      ip a

   output:
      inet 192.168.1.10/24 brd 192.168.1.255 scope global dynamic

   This shows the private IP address assigned to the system.

## ifconfig
  Use:
    Used to display information about all the network interfaces present on the system.

  Command:
      ifconfig

  Output:
      eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>
      inet 192.168.1.10 netmask 255.255.255.0

  Helps in identifying whether a network interface is active or not.

## traceroute
  Use:
   Tracks the path taken by the data packets from the system to the destination server.

  Command:
    traceroute google.com

  Output:
    1 192.168.1.1 1.123 ms
    2 10.10.0.1 5.456 ms
    3 142.250.192.14 20.345 ms

  Shows the number of hops between source and destination.

## netstat
  Use:
   Displays active network connections and listening ports on the system.

  Command:
     netstat -tulnp

  Output:
     tcp 0 0 0.0.0.0:22 0.0.0.0:* LISTEN

  Used to check which services are currently running on specific ports.  

## nslookup
  Use:
    Used to find the IP address of a domain using DNS lookup.

  Command:
   nslookup google.com

  Output:
    Name: google.com
    Address: 142.250.192.14

  Helps in resolving domain names to IP addresses.

## hostname
  Use:
   Displays the name of the system connected to the network.

  Command:
    hostname

  Sample Output:
    aditi-PC

  Used to identify the system name on the network.
