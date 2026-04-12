# Router and Switch in Computer Networking

---

# Router

![Image](https://images.ctfassets.net/aoyx73g9h2pg/1Vfu5lV8rlQUkw2sYQPS7c/69d1dc12a8ce350c6f0b785af3305087/What_is_a_Router-Diagram.jpg)

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Computer-and-networks-Wireless-router-home-area-network-diagram.png)

![Image](https://creately.com/static/assets/guides/home-network-diagram/basic-network-diagram-example-with-modem-and-router-VSfKzRefoUg.svg)

## What is a Router?

A **Router** is a networking device used to **connect multiple networks** and forward data packets between them.

Simply:

> Router connects **Network → Network**

Example:

* Home Network → Internet
* Office LAN → WAN

---

## Working Principle

1. Device sends data packet.
2. Router checks **Destination IP Address**.
3. Router decides the **best path** using routing table.
4. Packet is forwarded to the correct network.

---

## OSI Layer

* Works at **Layer 3 — Network Layer**

---

## Main Functions

* Connects LAN to Internet
* Routes packets between networks
* Performs Network Address Translation (NAT)
* Traffic management
* Security filtering (basic firewall)

---

## Components Inside Router

* Routing Table
* CPU & Memory
* WAN Port
* LAN Ports
* Wireless Access Point (in WiFi routers)

---

## Advantages

* Connects different networks
* Provides Internet access
* Improves security
* Supports wireless connectivity

---

## Disadvantages

* Higher cost than switch
* Configuration required
* Slightly slower than switches

---

## Real-Life Example

Home Wi-Fi Router connecting:

* Mobile
* Laptop
* Smart TV
* Printer

---

---

# Switch

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Computer-and-networks-10Base-T-star-network-topology.png)

![Image](https://www.pcweenie.com/images/hni/s03p014_connectRouterDiagram.png)

![Image](https://www.mydraw.com/NIMG.axd?i=Diagrams%2FNetwork%2FLogicalNetworkDiagram.png)

## What is a Switch?

A **Switch** is a networking device used to connect multiple devices **within the same network (LAN)**.

Simply:

> Switch connects **Device → Device**

Example:

* Computer lab network
* Office LAN system

---

## Working Principle

1. Device sends data frame.
2. Switch checks **MAC Address**.
3. Data is sent only to destination port.
4. Other devices do not receive unnecessary traffic.

---

## OSI Layer

* Works at **Layer 2 — Data Link Layer**

(Some modern switches work at Layer 3.)

---

## Main Functions

* Connects computers in LAN
* Controls traffic flow
* Reduces collision
* Improves network performance

---

## Advantages

* High speed communication
* Efficient data transfer
* Intelligent forwarding
* Less network congestion

---

## Disadvantages

* Cannot connect different networks
* Needs router for internet access

---

## Real-Life Example

College computer lab where all PCs connect using one switch.

---

---

# Router vs Switch

| Feature      | Router             | Switch            |
| ------------ | ------------------ | ----------------- |
| Connection   | Network to Network | Device to Device  |
| OSI Layer    | Layer 3            | Layer 2           |
| Address Used | IP Address         | MAC Address       |
| Main Purpose | Internet & Routing | LAN Communication |
| Speed        | Medium             | High              |
| Example      | WiFi Router        | LAN Switch        |

---

# How Router and Switch Work Together

![Image](https://www.conceptdraw.com/How-To-Guide/picture/Network-diagram-System-design.png)

![Image](https://www.uml-diagrams.org/examples/home-network-diagram-example.png)

![Image](https://www.lifewire.com/thmb/d-0PVRYIwjLuB1qfLW_CXvjNb6s%3D/1500x0/filters%3Ano_upscale%28%29%3Amax_bytes%28150000%29%3Astrip_icc%28%29/wireless-diagram-1-5804ecb83df78cbc28846dc4.jpg)

Typical Network Flow:

```
Internet
   ↓
Router
   ↓
Switch
   ↓
Computers / Printers / Devices
```

✔ Router connects network to Internet
✔ Switch connects multiple local devices

---

# Simple Analogy

* **Router = Post Office** 
  → Sends parcel to another city (network)

* **Switch = Office Manager** 
  → Delivers parcel to correct employee (device)

---

# Conclusion

* Router manages **communication between networks**.
* Switch manages **communication inside a network**.
* Both devices together build modern computer networks.



