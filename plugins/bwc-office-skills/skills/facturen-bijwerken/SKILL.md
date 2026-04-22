---
name: facturen-bijwerken
description: >
  BWC Concepts Facturen Bijwerken — verwerkt automatisch alle nieuwe DJ-facturen
  van de afgelopen week in de BWC Facturen 2026 Google Spreadsheet. Gebruik
  deze skill wanneer Tim vraagt om facturen bij te werken, "zet de facturen in
  de sheet", "verwerk de facturen van deze week", "check de facturen in Drive",
  of vergelijkbare verzoeken. Activeer ook proactief wanneer Tim vraagt om de
  wekelijkse factuurverwerking te doen, zelfs zonder het woord "skill" te
  noemen. De skill doorzoekt meerdere Google Drive-mappen, leest PDF-facturen
  uit, en voert de gegevens in in de juiste maand-tab van de spreadsheet.
---

# BWC Facturen Bijwerken

## Doel
Verwerk alle nieuwe facturen van de afgelopen week in de **BWC Facturen 2026** spreadsheet. Doe dit in twee duidelijke fases: eerst **alle** data verzamelen, dan **alles** invoeren. Geen interleaving.

---

## Spreadsheet

- **URL (edit mode):** `https://docs.google.com/spreadsheets/u/4/d/1JMOqjbIpKhbXH4-kK3AXymgRbiJWzCB_J6mXRUoFD20/edit`
- **Google account:** authuser=4 (`timpoelmansbwc@gmail.com`) — gebruik altijd `/u/4/` in Drive-URLs
- **Structuur:** Tabel3, kolommen: **Wie | Factuurnummer | Bedrag | Evenement + datum**
- **Tabblad:** gebruik het tabblad dat overeenkomt met de huidige maand (Januari, Februari, Maart, April, etc.)
- **Bedrag:** vul alleen het getal in (geen €-teken) — de kolom heeft al valuta-opmaak
- **Factuurnummer met leading zero** (bijv. 006): gebruik apostrof-prefix zodat het als tekst opgeslagen wordt (`'006`)

---

## FASE 1: Alle data verzamelen uit Google Drive

Volg deze stappen volledig voordat je ook maar iets in de spreadsheet invoert.

### Drive-mappen om te controleren

Gebruik altijd `/u/4/` in Drive-URLs. Controleer alle onderstaande mappen op nieuwe facturen voor de huidige maand.

#### BWC Events
- Zoek in Google Drive op: **"Facturen - BWC 2026 (Karin Janssen)"**
- Mappen daarbinnen (herken op naam, bijv. "Novia Saturdays", "Secret Lola", "Rolluik VRIJDAG", "Rolluik ZATERDAG")
- **Let op:** elke eventmap kan meerdere datumsubmappen hebben (bijv. "06 MAART", "13 MAART") — controleer **ALLE** datumsubmappen

#### Club Lizzy
- **LIZZY EDITIES 2026** (Nijmegen) → huidige maand → check alle datumsubmappen
- **LIZZY ALKMAAR** → maand-map voor de huidige maand
- **LIZZY TILBURG @ STUDIO TILBURG** → maand-map voor de huidige maand
- **LIZZY BREDA @CLUB BARON** → maand-map voor de huidige maand
- **LIZZY UTRECHT** → maand-map voor de huidige maand

### Werkwijze per map

1. Open de map via Google Drive (authuser=4)
2. Haal **alle** file IDs op in één keer via JavaScript:
   ```javascript
   Array.from(document.querySelectorAll('[data-id]')).map(el => el.getAttribute('data-id'))
   ```
3. Open elke PDF via: `https://drive.google.com/file/d/[FILE_ID]/preview`
4. Lees de factuur: noteer **Wie**, **Factuurnummer**, **Totaalbedrag** (incl. BTW), **Evenement + datum**
5. Als een PDF niet leesbaar is: sla over, noteer de bestandsnaam voor handmatige follow-up

### Regels voor de data

- **Evenement + datum:** strip de locatienaam. Gebruik bijv. `Secret Lola 13.03.2026` (niet "Secret Lola @ Novia Nijmegen 13.03.2026")
- **Kwitantie:** gebruik "Kwitantie" als factuurnummer
- **Declaratieformulier:** gebruik "Declaratieformulier" als factuurnummer
- **Datum format:** DD.MM.YYYY

Sla na Fase 1 alle gevonden facturen op als een interne lijst. Ga pas naar Fase 2 als alle mappen zijn doorlopen.

---

## FASE 2: Data invoeren in de spreadsheet

Nu alle facturen bekend zijn, voer je ze in. Gebruik **geen clipboard paste** — typ elke cel direct in via het toetsenbord.

### Stappen

1. **Open de spreadsheet** via de URL hierboven
2. **Navigeer naar het juiste maand-tabblad** (klik op de tab onderaan)
3. **Bepaal de eerste lege rij** via JavaScript:
   ```javascript
   document.querySelectorAll('table tbody tr').length
   ```
4. **Controleer op duplicaten:** lees de bestaande rijen en sla facturen over die al aanwezig zijn (vergelijk op Factuurnummer + Evenement)
5. **Klik op de eerste lege cel in kolom A** van de eerste rij die ingevoerd moet worden

### Per rij invoeren (herhaal voor elke nieuwe factuur)

Typ iedere cel apart — geen clipboard, geen paste:

```
Typ: [Wie-waarde]       → druk Tab
Typ: [Factuurnummer]    → druk Tab
Typ: [Bedrag als getal] → druk Tab
Typ: [Evenement+datum]  → druk Enter
```

- **Tab** gaat naar de volgende cel in dezelfde rij
- **Enter** bevestigt de rij en gaat naar de volgende rij (kolom A)
- Bij een factuurnummer met leading zero: typ eerst `'` (apostrof), dan het nummer (bijv. `'006`)
- Controleer na elke rij kort of de data correct is ingevoerd

### Als je vastzit

Als een cel niet reageert op typen:
- Klik opnieuw op de cel
- Druk F2 om de cel in edit-modus te zetten
- Typ daarna pas de waarde

---

## Afsluiting

Stuur een korte samenvatting via de Gmail MCP tool naar `timpoelmansbwc@gmail.com` met:
- Hoeveel nieuwe facturen zijn verwerkt
- Per event een overzicht (Wie, Factuurnummer, Bedrag)
- Eventuele overgeslagen of onleesbare bestanden

Maak een Gmail concept aan via `gmail_create_draft`.
