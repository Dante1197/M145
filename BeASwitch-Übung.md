## Be A Switch Übung - Notizen - 13.05.2025

### Dabei musst du immer 2 Fragen beantworten:
	1.	Soll eine neue MAC-Adresse in die Tabelle eingetragen werden?
	2.	An welche Ports soll das Frame gesendet werden?

## 🧠 Es gibt 4 Haupt-Szenarien:

✅ Szenario 1: Ziel-MAC ist bekannt, Quell-MAC ist neu

	•	➕ Neue MAC-Adresse (Source) wird gelernt
	•	📦 Frame wird nur an den Port gesendet, wo die Ziel-MAC sitzt

Antwort:
	•	☑️ New MAC address table entry required
	•	✅ Send to Ziel-Port
	•	❌ NICHT an andere Ports senden

⸻

✅ Szenario 2: Ziel-MAC ist bekannt, Quell-MAC ist schon bekannt

	•	🚫 Keine neue MAC-Adresse nötig
	•	📦 Frame wird nur an Ziel-Port gesendet

Antwort:
	•	🔘 No new MAC address table entry required
	•	✅ Send to Ziel-Port
	•	❌ NICHT an andere Ports

⸻

✅ Szenario 3: Ziel-MAC ist unbekannt, Quell-MAC ist neu

	•	➕ Neue MAC-Adresse wird gelernt
	•	📡 Frame wird an alle anderen Ports außer dem Eingangsport gesendet (Flooding)

Antwort:
	•	☑️ New MAC address table entry required
	•	✅ Send to alle Ports außer dem Eingangsport
	•	❌ NICHT an den Port, von dem das Frame kam

⸻

✅ Szenario 4: Ziel-MAC ist unbekannt, Quell-MAC ist schon bekannt

	•	🚫 Keine neue MAC-Adresse nötig
	•	📡 Frame wird an alle anderen Ports außer dem Eingangsport gesendet (Flooding)

Antwort:
	•	🔘 No new MAC address table entry required
	•	✅ Send to alle Ports außer dem Eingangsport
	•	❌ NICHT an den Eingangsport

## Screenshot Abgabe der Aufgabe 

![BeASwitch30Points](https://github.com/user-attachments/assets/a47f800e-c70b-4b82-8f60-9a304e75a719)


