# IPv4 Spickzettel – Ausführlich mit Beispielen & Erklärungen

### Thema 1: Subnetting – Netz aufteilen

#### Was bedeutet das?
Subnetting heisst: Du nimmst ein großes Netzwerk (z. B. 192.168.0.0/24) und teilst es in kleinere Stücke auf, sogenannte Subnets. Jedes Subnet bekommt eine eigene Netzwerkadresse und hat eine bestimmte Anzahl an IP-Adressen.

#### Begriffserklärungen:
	•	Netzwerkadresse: Die erste IP in einem Subnetz (z. B. 192.168.0.0) – sie identifiziert das Netz.
	•	Subnetzmaske: Sagt, wie viele Bits zum Netz gehören, z. B. /24 = 255.255.255.0.
	•	CIDR-Notation: Das „/24“ nach einer IP bedeutet, dass die ersten 24 Bits zur Netzadresse gehören.
	•	Sprunggröße: Wie viele IPs pro Subnetz (abhängig von der neuen Maske).

#### Beispiel-Quizfrage:

''' Divide 192.168.130.0/23 into 4 subnets. What is the 3rd subnet? '''

✅ Schritt-für-Schritt:
	1.	/23 = 512 IPs → Du willst 4 Subnetze
	2.	Wie viele Bits brauchst du für 4 Subnetze?
	•	Antwort: 2 Bits → 2^2 = 4 Subnetze
	3.	Neue Maske = /25 (23 + 2)
	4.	Anzahl IPs pro Subnetz: 2^(32-25) = 128

➗ Subnetz-Aufteilung:

Subnetz	Netzwerkadresse	Bereich
1	192.168.130.0/25	192.168.130.0–127
2	192.168.130.128/25	192.168.130.128–255
3 ✅	192.168.131.0/25	192.168.131.0–127
4	192.168.131.128/25	192.168.131.128–255


---

### Thema 2: Netzwerkadresse berechnen

#### Was bedeutet das?

Die Netzwerkadresse ist die erste Adresse eines IP-Blocks. Sie sagt: „Hier beginnt das Netz.“

Du findest sie, indem du ein bitweises AND zwischen der IP-Adresse und der Subnetzmaske machst.

#### Begriffserklärungen:
	•	IP-Adresse: Z. B. 99.252.194.61
	•	Subnetzmaske (z. B. /22): Gibt an, wie viele Bits fürs Netz sind.
	•	Bitweises AND: Binäre Verknüpfung: Nur 1 AND 1 = 1, alles andere = 0
	•	Ergebnis: Gibt dir die Netzwerkadresse

#### Beispiel-Quizfrage:

''' What is the network address of 99.252.194.61/22? '''

✅ Schritt-für-Schritt:
	1.	IP: 99.252.194.61
	2.	/22 → Subnetzmaske: 255.255.252.0
	3.	Ziel: Finde die Adresse, bei der alle Hostbits auf 0 sind

Lösung:
	•	/22 = 22 Bit für Netz, 10 Bit für Hosts → 1024 IPs pro Netz
	•	Wir suchen die größte durch 1024 teilbare Adresse unterhalb von 99.252.194.61
	•	Ergebnis: ✅ 99.252.192.0

Das ist die Netzwerkadresse des Blocks, in dem 99.252.194.61 liegt.


## Screenshot der Abgabe 
40/40 war eingestellt 30/30 waren nötig 

![IPv4 Quiz 31:40](https://github.com/user-attachments/assets/7327b219-0200-4612-a88a-86e21fe31ea9)

