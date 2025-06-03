## Part 1: Subnet the Assigned Network

a. LAN-A needs at least: 50 hosts
b. LAN-B needs at least: 40 hosts
c. Plus 2 additional subnets

---

Questions:

How many host addresses are needed in the largest required subnet?
→ 50

What is the minimum number of subnets required?
→ 4 (LAN-A, LAN-B, and 2 spare)

What is the /24 subnet mask in binary?
→ 11111111.11111111.11111111.00000000

---

Network Mask Bits:

What do the ones represent?
→ Network bits

What do the zeros represent?
→ Host bits

---

Subnet Analysis:

Prefix	Binary Representation	Dotted Decimal	# of Subnets	# of Hosts per Subnet
/25	11111111.11111111.11111111.10000000	255.255.255.128	2	126
/26	11111111.11111111.11111111.11000000	255.255.255.192	4	62
/27	11111111.11111111.11111111.11100000	255.255.255.224	8	30
/28	11111111.11111111.11111111.11110000	255.255.255.240	16	14
/29	11111111.11111111.11111111.11111000	255.255.255.248	32	6
/30	11111111.11111111.11111111.11111100	255.255.255.252	64	2


---

Final Subnet Mask Chosen: /26

→ Provides 4 subnets, 62 hosts each

---

Subnet Table:

Subnet Address	Prefix	Subnet Mask
192.168.0.0	/26	255.255.255.192
192.168.0.64	/26	255.255.255.192
192.168.0.128	/26	255.255.255.192
192.168.0.192	/26	255.255.255.192


---

IP Assignment (Fill into Packet Tracer):

LAN-A Subnet: 192.168.0.0/26
	•	CustomerRouter G0/0: 192.168.0.1
	•	LAN-A Switch VLAN1: 192.168.0.2, GW: 192.168.0.1
	•	PC-A: 192.168.0.62, GW: 192.168.0.1

LAN-B Subnet: 192.168.0.64/26
	•	CustomerRouter G0/1: 192.168.0.65
	•	LAN-B Switch VLAN1: 192.168.0.66, GW: 192.168.0.65
	•	PC-B: 192.168.0.126, GW: 192.168.0.65

---

**Part 1: Configure Devices**

🔹 Step 1: Configure CustomerRouter
	1.	Click on CustomerRouter → CLI tab
	2.	Enter the following:

```
enable
configure terminal
hostname CustomerRouter
enable secret Class123
line console 0
password Cisco123
login
exit
interface g0/0
ip address 192.168.0.1 255.255.255.192
no shutdown
exit
interface g0/1
ip address 192.168.0.65 255.255.255.192
no shutdown
exit
end
write memory
```

---

🔹 Step 2: Configure Switches

LAN-A Switch
	1.	Click LAN-A Switch → CLI tab

```
enable
configure terminal
interface vlan 1
ip address 192.168.0.2 255.255.255.192
no shutdown
exit
ip default-gateway 192.168.0.1
exit
```

LAN-B Switch
	1.	Click LAN-B Switch → CLI tab

```
enable
configure terminal
interface vlan 1
ip address 192.168.0.66 255.255.255.192
no shutdown
exit
ip default-gateway 192.168.0.65
exit
```

---

**Step 3: Configure PCs**

PC-A
	1.	Click PC-A → Desktop → IP Configuration

IP Address: 192.168.0.62
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.0.1

PC-B
	1.	Click PC-B → Desktop → IP Configuration

IP Address: 192.168.0.126
Subnet Mask: 255.255.255.192
Default Gateway: 192.168.0.65


---

Part 2: Test Connectivity

On PC-A:
	•	Ping default gateway → ping 192.168.0.1
	•	Ping PC-B → ping 192.168.0.126

On PC-B:
	•	Ping default gateway → ping 192.168.0.65
	•	Ping PC-A → ping 192.168.0.62

