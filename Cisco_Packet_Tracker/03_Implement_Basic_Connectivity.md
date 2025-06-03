# 🧠 Packet Tracer: Implement Basic Connectivity

### Addressing Table

``` 
Device	Interface	IP Address	Subnet Mask
S1	VLAN 1	192.168.1.253	255.255.255.0
S2	VLAN 1	192.168.1.254	255.255.255.0
PC1	NIC	192.168.1.1	255.255.255.0
PC2	NIC	192.168.1.2	255.255.255.0
``` 

⸻

## Part 1: Basic Switch Configuration (S1 and S2)

#### Configure Each Switch

**Complete these steps on both S1 and S2 using the CLI tab.**

**Step 1: Set Hostname**

``` 
Switch> enable
Switch# configure terminal
Switch(config)# hostname S1   # (or S2 for the second switch)
``` 

**Step 2: Set Console Password and Login**

``` 
S1(config)# line console 0
S1(config-line)# password cisco
S1(config-line)# login
S1(config-line)# exit
``` 

**Step 3: Set Encrypted Privileged EXEC Password**
``` 
S1(config)# enable secret class
``` 

**Step 4: Set a Banner Message**
``` 
S1(config)# banner motd # Authorized access only. Violators will be prosecuted to the full extent of the law. #
``` 

**Step 5: Save Configuration**
``` 
S1# write memory

Command to save configuration to NVRAM:

write memory

or

copy running-config startup-config
``` 

---

## Part 2: Configure PCs

Step 1: Assign IP Addresses

PC1:
	•	Click PC1 > Desktop > IP Configuration
	•	IP Address: 192.168.1.1
	•	Subnet Mask: 255.255.255.0
	•	Default Gateway: (leave blank)

PC2:
	•	IP Address: 192.168.1.2
	•	Subnet Mask: 255.255.255.0

---

## Part 3: Configure Switch Management Interface (VLAN 1)

Why Assign IPs to Switches?

So you can remotely manage the switch using Telnet/SSH, and also ping the switch to test connectivity.

⸻

**Step 1: Configure S1 VLAN 1 Interface**

``` 
S1# configure terminal
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.253 255.255.255.0
S1(config-if)# no shutdown
S1(config-if)# exit
S1(config)# exit
``` 

**Step 2: Configure S2 VLAN 1 Interface**

``` 
S2# configure terminal
S2(config)# interface vlan 1
S2(config-if)# ip address 192.168.1.254 255.255.255.0
S2(config-if)# no shutdown
S2(config-if)# exit
S2(config)# exit
``` 

Why no shutdown?
To bring the VLAN interface up, otherwise it remains administratively down.
 
---

## Step 3: Verify IP Configuration on Switches

``` 
show ip interface brief
``` 

Look for:
	•	VLAN 1 has the correct IP.
	•	Status: up
	•	Protocol: up

**Step 4: Save Configuration**

``` 
write memory
``` 
---

## Part 4: Test Network Connectivity

**Step 1: From PC1 Command Prompt**

``` 
ping 192.168.1.2    # Ping PC2
ping 192.168.1.253  # Ping S1
ping 192.168.1.254  # Ping S2
``` 

Step 2: From PC2 Command Prompt
``` 
ping 192.168.1.1    # Ping PC1
ping 192.168.1.253  # Ping S1
ping 192.168.1.254  # Ping S2
``` 

🟢 If any ping fails:
	•	Recheck cables and port lights (should be green).
	•	Check VLAN IP config.
	•	Use show running-config on switches for errors.
