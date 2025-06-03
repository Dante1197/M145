**Packet Tracer - Identify MAC and IP Addresses**

---

**Objectives**

* Part 1: Gather PDU Information for Local Network Communication
* Part 2: Gather PDU Information for Remote Network Communication
* Part 3: Answer Reflection Questions

---

**Part 1: Gather PDU Information for Local Network Communication**

**Ping from 172.16.31.5 to 172.16.31.2**

| At Device   | Dest. MAC        | Src MAC          | Src IPv4    | Dest IPv4   |
| ----------- | ---------------- | ---------------- | ----------- | ----------- |
| 172.16.31.5 | 000C:85CC:1DA7   | 00D0\:D311\:C788 | 172.16.31.5 | 172.16.31.2 |
| Switch1     | 000C:85CC:1DA7   | 00D0\:D311\:C788 | 172.16.31.5 | 172.16.31.2 |
| 172.16.31.2 | 00D0\:D311\:C788 | 000C:85CC:1DA7   | 172.16.31.2 | 172.16.31.5 |

**Ping from 172.16.31.3 to 172.16.31.2**

| At Device   | Dest. MAC      | Src MAC        | Src IPv4    | Dest IPv4   |
| ----------- | -------------- | -------------- | ----------- | ----------- |
| 172.16.31.3 | 000C:85CC:1DA7 | 00D0:588C:2401 | 172.16.31.3 | 172.16.31.2 |
| Switch1     | 000C:85CC:1DA7 | 00D0:588C:2401 | 172.16.31.3 | 172.16.31.2 |
| 172.16.31.2 | 00D0:588C:2401 | 000C:85CC:1DA7 | 172.16.31.2 | 172.16.31.3 |

**Ping from 172.16.31.5 to 172.16.31.4**

| At Device   | Dest. MAC        | Src MAC          | Src IPv4    | Dest IPv4   |
| ----------- | ---------------- | ---------------- | ----------- | ----------- |
| 172.16.31.5 | 00D0:234C:1FA1   | 00D0\:D311\:C788 | 172.16.31.5 | 172.16.31.4 |
| Switch1     | 00D0:234C:1FA1   | 00D0\:D311\:C788 | 172.16.31.5 | 172.16.31.4 |
| 172.16.31.4 | 00D0\:D311\:C788 | 00D0:234C:1FA1   | 172.16.31.4 | 172.16.31.5 |

---

**Part 2: Gather PDU Information for Remote Network Communication**

**Ping from 172.16.31.5 to 10.10.10.2**

| At Device    | Dest. MAC       | Src MAC          | Src IPv4    | Dest IPv4   |
| ------------ | --------------- | ---------------- | ----------- | ----------- |
| 172.16.31.5  | 00D0\:BA8E:741A | 00D0\:D311\:C788 | 172.16.31.5 | 10.10.10.2  |
| Switch1      | 00D0\:BA8E:741A | 00D0\:D311\:C788 | 172.16.31.5 | 10.10.10.2  |
| Router       | 0060:2F84:4AB6  | 00D0\:BA8E:741A  | 172.16.31.5 | 10.10.10.2  |
| Switch0      | 0060:2F84:4AB6  | 00D0:588C:2401   | 172.16.31.5 | 10.10.10.2  |
| Access Point | 0060:2F84:4AB6  | 00D0:588C:2401   | 172.16.31.5 | 10.10.10.2  |
| 10.10.10.2   | 00D0:588C:2401  | 0060:2F84:4AB6   | 10.10.10.2  | 172.16.31.5 |

---

**Part 3: Reflection Questions & Answers**

1. **Were there different types of cables/media used to connect devices?**
   Yes, copper (Ethernet) cables and wireless connections were used.

2. **Did the cables change the handling of the PDU in any way?**
   No, cables do not change the structure of the PDU, only the medium through which it travels.

3. **Did the Hub lose any of the information that it received?**
   No, hubs do not lose information, but they broadcast it to all ports.

4. **What does the Hub do with MAC addresses and IP addresses?**
   Hubs do not interpret MAC or IP addresses; they simply forward all incoming traffic to all ports.

5. **Did the wireless Access Point do anything with the information given to it?**
   Yes, it forwarded the data to the correct wireless device using MAC addresses.

6. **Was any MAC or IP address lost during the wireless transfer?**
   No, the addresses were preserved during wireless transmission.

7. **What was the highest OSI layer that the Hub and Access Point used?**

   * Hub: Layer 1 (Physical)
   * Access Point: Layer 2 (Data Link)

8. **Did the Hub or Access Point ever replicate a PDU that was rejected with a red “X”?**
   No, they did not replicate rejected PDUs.

9. **When examining the PDU Details tab, which MAC address appeared first, the source or the destination?**
   The destination MAC address appears first.

10. **Why would the MAC addresses appear in this order?**
    Because the destination address is needed to forward the frame correctly.

11. **Was there a pattern to the MAC addressing in the simulation?**
    Yes, each device type (e.g., switch, router, PC) had a consistent MAC prefix.

12. **Did the switches ever replicate a PDU that was rejected with a red “X”?**
    No, switches only forward frames to correct ports based on MAC address tables.

13. **Where did the MAC addresses change during transmission between the 10 and 172 networks?**
    At the router (Layer 3 boundary), when forwarding between networks.

14. **Which device uses MAC addresses that start with 00D0\:BA?**
    The router interface connected to the 172.16.31.0 network.

15. **What devices did the other MAC addresses belong to?**
    PCs, switches, routers, and access points all had their own unique MACs.

16. **Did the sending and receiving IPv4 addresses change in any of the PDUs?**
    No, source and destination IPs remain the same throughout the communication.

17. **When you follow the reply to a ping (pong), do the sending and receiving IPv4 addresses switch?**
    Yes, the destination becomes the source and vice versa.

18. **What is the pattern to the IPv4 addressing used in this simulation?**
    172.16.31.x for local devices and 10.10.10.x for remote ones.

19. **Why do different IP networks need to be assigned to different ports of a router?**
    Because each interface represents a different subnet and allows routing between them.

20. **If this simulation was configured with IPv6 instead of IPv4, what would be different?**
    IPv6 addresses would be longer, use colons instead of dots, and MAC-to-IP resolution would use NDP instead of ARP.

