
Spickzettel: Be A Router

1. Ziel der Aufgabe

Ein Paket kommt an → Du musst entscheiden, an welchen Port (ethX) der Router das IPv4-Paket weiterleiten soll.

⸻

So gehst du vor – Schritt für Schritt

1. Schaue dir die Ziel-IP (Dest IP) im grünen Kasten rechts unten an.

2. Gehe zur Routing-Tabelle (oben rechts) und finde den passenden Eintrag, bei dem das Ziel-IP in das Netzwerk fällt:

Beispiel:
	•	Ziel: 192.168.128.78
	•	Routing-Eintrag: 192.168.128.0/21 passt → eth0

Nutze z. B. Subnet Calculator bei Bedarf.

**3. Wenn mehrere passen, nimm den präzisesten Eintrag (größte Präfixlänge, z. B. /27 ist präziser als /21).

**4. Schaue in der gleichen Zeile in der Routing-Tabelle nach, welcher dev ethX verwendet wird → das ist der Port, den du auswählen musst!

⸻

3. Subnetz-Tipps (CIDR Basics)

CIDR	Hosts nutzbar	Subnetzmaske

/30	2	255.255.255.252

/29	6	255.255.255.248

/28	14	255.255.255.240

/27	30	255.255.255.224

/26	62	255.255.255.192

/25	126	255.255.255.128

/24	254	255.255.255.0

/23	510	255.255.254.0


⸻

4. Netzwerkadressen schnell bestimmen

IP-Adresse & Subnetzmaske → bitweises UND = Netzadresse

Beispiel:
	•	IP: 192.168.131.250
	•	Maske (z. B. /21 → 255.255.248.0)
	•	Rechne: 192.168.128.0 → Netzadresse

⸻

❗ 5. Wenn keine Route passt?

→ Standardroute 0.0.0.0/0 verwenden (letzter Ausweg).

⸻

⚠️ Fehler vermeiden:
	•	Achte genau auf Präfix-Länge → nicht einfach ersten passenden Eintrag nehmen.
	•	Verwechsle nicht Source IP mit Dest IP – du routest immer nach dem Ziel!
	•	Nie mehr als 1 Port auswählen, außer es steht ausdrücklich anders.

##Screenshots zur Bestätigung der Übung 

40/40 leider falsch eingestellt:

![image](https://github.com/user-attachments/assets/3d968ceb-48d3-4265-a892-9faa84a8476b)

10/10 damit ich die volle punktzahl von 50/50 erreichen kann

![Be A Router 10:10](https://github.com/user-attachments/assets/7987eb27-eb95-4d6e-a5bd-45fa6d349f0c)


