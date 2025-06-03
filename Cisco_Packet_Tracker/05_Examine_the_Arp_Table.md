**Packet Tracer - Examine the ARP Table**

---

### Addressing Table

| Device      | Interface | MAC Address    | Switch Interface |
| ----------- | --------- | -------------- | ---------------- |
| Router0     | G0/0      | 0001.6458.2501 | G0/1             |
| Router0     | S0/0/0    | N/A            | N/A              |
| Router1     | G0/0      | 00E0.F7B1.8901 | G0/1             |
| Router1     | S0/0/0    | N/A            | N/A              |
| 10.10.10.2  | Wireless  | 0060.2F84.4AB6 | F0/2             |
| 10.10.10.3  | Wireless  | 0060.4706.572B | F0/2             |
| 172.16.31.2 | F0        | 000C.85CC.1DA7 | F0/1             |
| 172.16.31.3 | F0        | 0060.7036.2849 | F0/2             |
| 172.16.31.4 | G0        | 0002.1640.8D75 | F0/3             |

---

## Part 1: Examine an ARP Request

**Step 1:** Generate ARP requests by pinging 172.16.31.3 from 172.16.31.2.

**Question:** Is this address listed in the table above?

* **Yes**, 0060.7036.2849 is the MAC of 172.16.31.3.

**Question:** How many copies of the PDU did Switch1 make?

* **Three**, one for each device on different switch ports (F0/2, F0/3, etc.).

**Question:** What is the IP address of the device that accepted the PDU?

* **172.16.31.3**

**Question:** What happened to the source and destination MAC addresses?

* Source MAC = 000C.85CC.1DA7 (sender)
* Destination MAC = FFFF.FFFF.FFFF (broadcast)

**Question:** How many copies of the PDU did the switch make during the ARP reply?

* **One**, directed only to the source that requested the MAC.

**Step 2: Examine the ARP table.**

**Question:** Do the MAC addresses of the source and destination align with their IP addresses?

* **Yes**, both are correctly paired with their corresponding IPs.

**Question:** To what IP address does the MAC address entry correspond?

* **172.16.31.3** → 0060.7036.2849

**Question:** In general, when does an end device issue an ARP request?

* **When it wants to resolve an IP address to a MAC address before communication.**

---

## Part 2: Examine a Switch MAC Address Table

**Step 1: Generate traffic**

**Question:** How many replies were sent and received?

* **Four ICMP replies total**, two per successful ping.

**Step 2: Examine MAC address tables**

**Question:** Do the entries on Switch1 correspond to those in the table above?

* **Yes**, MAC addresses appear on the ports associated with those devices.

**Question:** Do the entries on Switch0 correspond to those in the table above?

* **Yes**, each MAC is correctly linked to the interface.

**Question:** Why are two MAC addresses associated with one port?

* **This can occur if a wireless access point or a hub is connected, allowing multiple hosts to connect via the same physical interface.**

---

## Part 3: Examine the ARP Process in Remote Communications

**Step 1: Generate traffic**

**Question:** What is the IP address of the new ARP table entry?

* **Likely 172.16.31.1**, the default gateway of 172.16.31.2.

**Question:** How many PDUs appear?

* **Two**, one ARP request and one ICMP packet waiting.

**Question:** What is the target destination IP address of the ARP request?

* **172.16.31.1**

**Question:** Why?

* **Because to reach a remote IP, the packet must first be sent to the default gateway, and its MAC must be resolved.**

**Step 2: Examine the ARP table on Router1.**

**Question:** How many MAC addresses are in the table? Why?

* **Usually one or two**, depending on how many recent packets were routed. Routers only store entries they directly communicate with.

**Question:** Is there an entry for 172.16.31.2?

* **Yes**, if Router1 received traffic from that device.

**Question:** What happens to the first ping when the router responds to the ARP request?

* **The first ping is delayed/lost, but subsequent pings succeed once the ARP reply is received.**

---

**End of Document**
