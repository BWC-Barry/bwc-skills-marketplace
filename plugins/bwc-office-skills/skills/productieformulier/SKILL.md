---
name: productieformulier
description: >
  BWC Concepts Productieformulier generator. Gebruik deze skill wanneer Tim
  vraagt om een productieformulier aan te maken voor een event. De skill maakt
  een kopie van het template-spreadsheet in Google Drive, hernoemt het naar
  het event, en vult het in met de data uit het Artist Program, de DJ contacten,
  het doorhost rooster en de doorhost contacten. Activeer wanneer Tim vraagt:
  "maak een productieformulier voor [event]" of vergelijkbare formuleringen.
---

# BWC Concepts - Productieformulier Skill

## Doel
Maak automatisch een ingevuld productieformulier (Google Spreadsheet) aan voor
een BWC Concepts event, op basis van het Artist Program en de contactenlijsten.

---

## 🔧 Eerste keer? Even jezelf instellen

Deze skill is voor het hele BWC-team (meestal Advancing). Bij de eerste run bij een nieuwe gebruiker, vraag en onthoud deze twee waarden voor de rest van de sessie:

**1. BWC-e-mailadres (`{USER_EMAIL}`)** — **verplicht met `bwc` in de naam**.

- Vraag: "Wat is jouw BWC-e-mailadres voor Google Drive?"
- Valideer: het adres MOET de letters `bwc` bevatten (bijv. `kelvinbwc@gmail.com`, `ninabwc@gmail.com`, `timpoelmansbwc@gmail.com`).
- Bevat het adres geen `bwc`? → vraag opnieuw. Dit is bewust — alle BWC-werk-accounts hebben `bwc` in de naam.

**2. Google authuser-index (`{AUTH_USER}`)** — welk account in Chrome.

- Open `drive.google.com` in Chrome en kijk naar de URL. Als je ingelogd bent met meerdere Google-accounts zie je `/u/X/` waarin `X` een getal is.
- Vraag: "Welk getal staat er bij jou na `/u/` in de Drive URL?"
- Typische waarden: `0` (eerste account), `1`, `2`, `3`, `4` (Tim).

Gebruik `{USER_EMAIL}` en `{AUTH_USER}` overal in de rest van deze skill.

---

## Databronnen

### 1. Template spreadsheet
- **ID**: `1sHzX2hcMJ5651s0ISS9on8TPjz9fdXzx3jh4B7X4ZL0`
- Gebruik dit als basis voor elk nieuw formulier (kopie maken via browser)

### 2. Artist Program spreadsheet
- **ID**: `10PGiDLPfA-kfk7n8GdAugbBkb89us0_E_ZFH-FquN3s`
- Novia Saturdays tab: `gid=654227655`
- Kolommen: datum, event naam, DJ's op timetable (met tijden)

### 3. BWC DJ & Doorhost contacten
- **ID**: `1H1F2sxIQ8QBOT3TO92xG2W2HFMqIv7qajUIIYChifJk`
- **DJ's** (Blad1, kolommen A–D):
  - A = DJ/Handelsnaam
  - B = Tel Nr. (format: 316xxxxxxxxxx)
  - C = E-mail
  - D = Volledige naam
- **Doorhosts** (Blad1, kolommen H–I, rechts van de DJ-tabel):
  - H = Naam doorhost
  - I = Tel Nr. (format: 316xxxxxxxxxx)

### 4. Doorhost rooster
- **ID**: `1GbkQuDTainSxzmD-OC3BJq3xXASG8iRADNxWsD2vU3s`
- **Tab**: `gid=1407460098`
- Geeft per week en locatie aan welke doorhost ingeroosterd staat
- Zoek op weeknummer + locatie (bijv. "Week 12 – Nijmegen")

---

## Werkwijze

### Stap 1: Haal event-data op
Navigeer naar het Artist Program spreadsheet en zoek het event op:
- Event naam (bijv. "Novia Saturdays")
- Datum (bijv. "28.03.2026")
- Locatie (bijv. "Club Novia Nijmegen")
- Tijd (bijv. "23:00-05:00")
- Timetable: tijdslots + DJ-namen

### Stap 2: Maak kopie van template
1. Open het template spreadsheet in de browser (Google account u/{AUTH_USER} = {USER_EMAIL})
2. Ga naar Bestand → Kopie maken
3. Geef de kopie de naam: `Productieformulier [Event naam] [DD-MM-YYYY]`
   Voorbeeld: `Productieformulier Novia Saturdays 28-03-2026`
4. Sla op in de BWC Concepts Google Drive

### Stap 3: Zoek DJ-telefoonnummers op
Voor elke DJ op de timetable:
- Zoek de naam op in de BWC DJ contacten (kolom A van Blad1)
- Noteer het telefoonnummer uit kolom B
- Als niet gevonden: laat de cel leeg

### Stap 4: Zoek doorhost op
1. Bepaal het weeknummer van de eventdatum
2. Navigeer naar het doorhost rooster (gid=1407460098)
3. Zoek op weeknummer + locatie/stad voor de juiste doorhost
4. Zoek het telefoonnummer van de doorhost in de BWC contacten
   (kolom H = naam, kolom I = telefoonnummer, rechts van de DJ-tabel)

### Stap 5: Vul de kopie in
Open de gekopieerde spreadsheet en vul de volgende cellen in via de Name Box
(cel-navigatie). **Gebruik altijd Enter (geen Tab) om te bevestigen.**

#### Basisgegevens (rij 7–12)
| Cel | Inhoud |
|-----|--------|
| B7  | Event naam (bijv. "Novia Saturdays") |
| B8  | Datum (DD.MM.YYYY, bijv. "28.03.2026") |
| B9  | Locatie (bijv. "Club Novia Nijmegen") |
| B10 | Tijd (bijv. "23:00-05:00") |
| B11 | Pre-borrel tijd (leeg als niet van toepassing) |
| B12 | Max capacity (voor Novia: 450) |

#### Rechterkolom basisgegevens
| Cel | Inhoud |
|-----|--------|
| D8  | **Artist coins** = aantal UNIEKE DJ's × 6 (zie Berekeningsregels — b2b's tellen elke DJ apart, dubbel-boekingen maar 1×) |
| D11 | **Expected Occ.** = zelfde als Max capacity |

#### Timetable (rijen 16–19, max 4 slots — uitbreidbaar voor grotere events)
| Cel  | Inhoud |
|------|--------|
| A16  | Tijdslot (bijv. "23.00 - 00.30") |
| B16  | DJ naam (bij b2b: "DJ1 b2b DJ2") |
| C16  | Telefoonnummer **1e DJ** (leeg als niet gevonden) |
| D16  | Telefoonnummer **2e DJ** bij b2b (leeg als solo of niet gevonden) |
| A17–D19 | Idem voor volgende slots |

⚠️ **B2b telefoonnummer-regel**: bij "Armand b2b Daniël" staat Armand's tel in kolom C, Daniël's tel in kolom D. Plaats ze **nooit** allebei in C (dat klopt niet met hoe het formulier gelezen wordt).

Wis eventuele resterende rijen (A18:D19) als er minder dan 4 DJ's zijn.

**Wis altijd eerst het complete timetable-bereik (A16:D20) via Name Box → `A16:D20` → Delete** voordat je een nieuwe timetable plakt. Het template kan nog data bevatten van een eerdere kopie.

**Plakken via clipboard** (snelst):
- Schrijf regels met tab-separated waarden: `tijdslot\tDJ-naam\ttel1\ttel2\n`
- Navigeer via Name Box naar A16, dan cmd+v
- Voor meer dan 4 slots: breid het bereik uit en plak vanaf A16

#### Entrance fee & Doorhost (rijen 22–26)
| Cel  | Inhoud |
|------|--------|
| B22  | Entrance fee (bijv. "€5" voor Novia; leeg als geen entree) |
| B23  | Naam doorhost |
| C23  | Werktijd doorhost (altijd "23:00 - 04:00") |
| D23  | Telefoonnummer doorhost |

Laat B24–B26, C24–C26, D24–D26 leeg als er maar 1 doorhost is.

#### Technical Riders (rijen 29–34)
| Cel  | Inhoud |
|------|--------|
| B34  | RMX: "1X" voor Novia / leeg voor Rolluik |

(B31 CDJ 3000 = "3X" en B33 Mixer = "A9" blijven ongewijzigd vanuit template)

---

## Venue-specifieke regels

| Venue              | Max cap | Entrance fee | RMX  |
|--------------------|---------|--------------|------|
| Club Novia Nijmegen | 450     | €5           | 1X   |
| Rolluik (Rolclub)  | ?       | nader te bepalen | leeg |

---

## Berekeningsregels

- **Artist coins** = aantal UNIEKE DJ's op de lineup × 6 coins per DJ
  - ⚠️ **BELANGRIJK** — tel elke unieke DJ één keer, ook als die in meerdere slots/b2b's voorkomt
  - **Bij b2b-sessies tellen beide DJ's apart** (2 DJ's in 1 slot = 12 coins voor dat slot)
  - **Een DJ die in meerdere slots voorkomt telt maar 1× mee** (bv. als Daniël Saini zowel in een b2b-slot als solo-slot staat, krijgt hij 6 coins, niet 12)
  - **Reken uit op basis van de timetable, niet op basis van het aantal slots**
  - Voorbeeld 1 — Event met 4 slots (1 solo + 3 b2b's):
    - 23:00-00:30 Kjell (1)
    - 00:30-02:00 Lukas b2b JIPX2 (2)
    - 02:00-03:30 Sven b2b Carlos (2)
    - 03:30-05:00 Casarena b2b Angelo (2)
    - Totaal = 7 unieke DJ's × 6 = **42 coins**
  - Voorbeeld 2 — Event met 5 slots waarvan 1 DJ dubbel voorkomt:
    - 21:30-23:00 Rik b2b Olaf (2)
    - 23:00-00:30 A-Aron b2b Knijff (2)
    - 00:30-02:00 Melis b2b Daniël Saini (2, waarvan Daniël nieuw)
    - 02:00-03:30 Daniël Saini (0 nieuw — hij telde al mee)
    - 03:30-05:00 Kyran (1)
    - Totaal = 7 unieke DJ's × 6 = **42 coins**
  - Voorbeeld 3 — Event met 3 solo-slots:
    - Mér / Vitór / Milan = 3 unieke DJ's × 6 = **18 coins**
- **Expected Occ.** = altijd gelijk aan Max capacity van de venue
- **Doorhost werktijd** = altijd 23:00 - 04:00
- **Entrance fee Novia** = standaard €5, tenzij Tim anders aangeeft

---

## Opmerkingen voor de automatisering

- Altijd een **nieuwe Google Spreadsheet** aanmaken (nooit een lokaal bestand)
- Template wordt gekopieerd via browser (Bestand → Kopie maken)
- Navigeer naar cellen via de **Name Box** (cel-referentie linksboven)
- Bevestig elke cel-invoer met **Enter** (niet Tab — dat zorgt voor concatenatie in dezelfde cel)
- Google account voor Drive: **u/{AUTH_USER}** = {USER_EMAIL}
