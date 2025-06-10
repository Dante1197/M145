# Labor 1: Ping mit Switch – GNS3 Anleitung

---

**1. Neues Projekt in GNS3 erstellen**
	1.	GNS3 starten.
	2.	Klicke oben links auf „File > New Blank Project“.
	3.	Projektname: z. B. Labor1_PingMitSwitch.
	4.	Speicherort wählen und auf „OK“ klicken.

---

**2. Geräte hinzufügen & verbinden**

Geräte einfügen
	1.	Links in der Geräteliste suchst du nach:
	•	3× VPCS
	•	1× Switch (Ethernet Switch aus „End Devices“ oder „Ethernet Switch (Unmanaged)“ verwenden)
	2.	Ziehe die Geräte in das Arbeitsfeld (Drag & Drop).

Geräte verbinden
	1.	Klicke auf das Verkabelungs-Symbol (kleines Kabel oben links).
	2.	Verbinde:
	•	PC1 → Switch
	•	PC2 → Switch
	•	PC3 → Switch

---

**3. VPCS konfigurieren (IP-Adresse setzen)**

Geräte starten
	1.	Rechtsklick auf jedes Gerät > Start.
	2.	Danach Rechtsklick > Console, um Terminal zu öffnen.

IP-Adressen manuell setzen (Beispiel):

Für PC1:
``` 
ip 192.168.10.1 255.255.255.0
```

Für PC2:
```
ip 192.168.10.2 255.255.255.0
```

Für PC3:
```
ip 192.168.10.3 255.255.255.0
```

**Kein Gateway nötig, da alles im selben Subnetz.**

---

**4. Ping-Test durchführen**

Von PC1:
```
ping 192.168.10.2
ping 192.168.10.3
```

Von PC2:
```
ping 192.168.10.1
ping 192.168.10.3
```

Wenn du Reply bekommst: Verbindung funktioniert.

---

**5. Wireshark Packet Capture**

Schritt-für-Schritt:
	1.	Rechtsklick auf Verbindung (Kabel) zwischen PC1 und Switch.
	2.	Wähle Start Capture.
	3.	Wireshark öffnet sich automatisch.
	4.	Wechsle zurück zur VPCS-Konsole und führe einen ping durch.
	5.	Beobachte in Wireshark → Du solltest ICMP Echo Request / Reply Pakete sehen.

**Filter in Wireshark verwenden**
icmp

Capture stoppen
	1.	In GNS3: Rechtsklick auf Link > Stop capture.

![image](https://github.com/user-attachments/assets/a7d9e12e-de93-418d-ae77-fd96a774eeb0)
