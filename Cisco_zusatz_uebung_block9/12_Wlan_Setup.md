# Cisco Packet Tracer Wireless Lab – Additional Task (Block 9) 

This guide describes the full configuration of a wireless network in Cisco Packet Tracer using a **WLC-2504**, **Lightweight Access Point**, **DHCP Server**, and **Wireless Client (Laptop)**.

---

### 1. Network Topology

Add the following devices:

- 1x 1841 Router  
- 1x 2960 Switch  
- 1x WLC-2504 Wireless LAN Controller  
- 1x 3702i Lightweight Access Point  
- 1x Server  
- 1x PC  
- 1x Laptop  

### 🔌 Cable Connections

| Device         | Interface     | Connected To    | Interface     |
|----------------|---------------|------------------|---------------|
| Router         | Fa0/0         | Switch           | Fa0/5         |
| PC             | Fa0           | Switch           | Fa0/2         |
| Server         | Fa0           | Switch           | Fa0/4         |
| WLC-2504       | Gig1          | Switch           | Fa0/1         |
| Access Point   | Gig0          | Switch           | Fa0/3         |

---

### 2. Configure WLC-2504

- Go to: `Config` > `Management Interface`
- Set the following:
  - **IP Address**: `192.168.1.10`
  - **Subnet Mask**: `255.255.255.0`
  - **Default Gateway**: `192.168.1.1`

---

### 3. Configure PC0 (Wired Client)

- IP Address: `192.168.1.100`  
- Subnet Mask: `255.255.255.0`  

**Command Prompt Tests:**

```
ipconfig
ping 192.168.1.100
ping 192.168.1.10
```

---

### 4. Access WLC Web GUI
	1.	On PC0 > Web Browser: http://192.168.1.10
	2.	Login: admin / admin
	3.	Setup screen:
	•	System Name: WLC-2504
	•	Management IP: 192.168.1.10
	•	Subnet: 255.255.255.0
	•	Gateway: 192.168.1.1
	•	VLAN ID: 0
	4.	Wireless Network:
	•	SSID: Employee
	•	Security: WPA2 Personal
	•	Passphrase: Employee
	5.	Apply settings and log back in.
	6.	Go to WLANs tab > Confirm SSID Employee exists.
	7.	Go to WLAN ID > Security > Layer2:
	•	WPA2 Policy ✔️
	•	AES ✔️
	•	PSK: Employee

---

### 5. Router Configuration (Simulated Default Gateway)

```
enable
configure terminal
interface FastEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
exit
write memory
```

### 6. Configure DHCP on Server
	•	IP Address: 192.168.1.20
	•	Subnet Mask: 255.255.255.0

### DHCP Settings:

Field	Value
- Pool Name	DHCP-Pool
- Default Gateway	192.168.1.1
- Subnet Mask	255.255.255.0
- Starting IP	192.168.1.101
- Max Users	100

---

 ### 7. Configure Access Point (AP)
- Automatically gets IP via DHCP.
- If not: switch to static, then back to DHCP to force renewal.
- From WLC Web GUI > Wireless tab: Confirm AP is connected.

---

### 8. Configure Laptop (Wireless Client)

1.	Physical Tab:
- Power off
- Remove FastEthernet module
- Add Linksys WPC300N
- Power on

2.	Config Tab > Wireless0:
- SSID: Employee
- Auth: WPA2-PSK
- Passphrase: Employee
- Encryption: AES
- IP Configuration: DHCP
- If needed: switch to static, then back to DHCP

---

### 9. Test Connectivity
- On Laptop:
- ipconfig /all
- ping 192.168.1.20 (server)

---

### 10. Simulation Mode – CAPWAP Traffic
1.	Switch to Simulation Mode
2.	Set filters: ICMP and CAPWAP
3.	On Laptop: ping 192.168.1.100 (PC)
4.	Watch packet path:
- vLaptop ⟶ AP ⟶ Switch ⟶ PC
5.	Inspect CAPWAP packet:
- Look for UDP Port: 5246 or 5247

![Screenshot 2025-07-08 at 09 25 13](https://github.com/user-attachments/assets/4d3962a9-03e6-4cd5-9206-9113efca2b3c)   


![Screenshot 2025-07-08 at 09 42 44](https://github.com/user-attachments/assets/39b290e8-e206-449a-983b-68dba3f6a55a)


