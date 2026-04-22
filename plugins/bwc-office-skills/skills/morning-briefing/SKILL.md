---
name: morning-briefing
description: >
  BWC Concepts Morning Briefing — persoonlijke dagstart voor medewerkers van Bloom with Colour.
  Gebruik deze skill wanneer iemand vraagt om een morning briefing, dagstart, /briefing,
  "wat staat er vandaag op mijn agenda", "geef me een overzicht van mijn dag", of "wat moet ik
  vandaag doen". De skill haalt data op uit Google Calendar en Gmail, en genereert een mooi
  opgemaakt HTML-briefing in BWC-stijl. Activeer altijd bij /briefing of vergelijkbare verzoeken
  om een dagelijkse samenvatting of overzicht — ook zonder expliciete vermelding van "skill".
---

# BWC Morning Briefing

## Doel
Genereer elke ochtend een persoonlijke, visueel aantrekkelijke briefing voor een medewerker van Bloom with Colour. De briefing geeft in één oogopslag overzicht van de dag: agenda, prioritaire mails, aankomende events en focuspunten — zodat de medewerker meteen weet waar hij of zij aan moet beginnen.

De output is een **HTML-bestand** dat wordt opgeslagen in de workspace en direct geopend kan worden in de browser. Het design volgt de BWC-huisstijl: donker, strak, professioneel met kleuraccenten.

---

## Stap 1 — Stel de identiteit vast

Lees het gebruikersprofiel als dat beschikbaar is (zie Stap 6 voor profielstructuur). Als er geen profiel is, vraag dan kort: "Wie ben je en wat is je rol bij BWC?" — en sla het daarna op.

Gebruik de naam en rol bij het personaliseren van de briefing en het filteren van relevante informatie.

---

## Stap 2 — Haal Google Calendar data op

Gebruik de Google Calendar MCP tools:
1. Haal **alle agenda's** op voor de gebruiker (`gcal_list_calendars`)
2. Haal **alle events van vandaag** op (`gcal_list_events` voor de huidige dag, 00:00–23:59)
3. Haal ook **events van de komende 7 dagen** op — specifiek om BWC-events (Lizzy, Clear, Novia, Lola, Luna, Lush, etc.) te detecteren

**Wat je zoekt in de agenda:**
- Meetings, calls, afspraken vandaag — met tijd, titel en eventuele deelnemers
- Deadlines die vandaag vervallen (items met "deadline", "inleveren", "opleveren", "submit" in de titel)
- BWC-events in de komende 7 dagen — dit zijn events zoals "Lizzy op Donderdag", "Clear", "Secret Lola", etc.

---

## Stap 3 — Haal Gmail data op

Gebruik de Gmail MCP tools om twee categorieën te identificeren:

**A. Urgente mails (vandaag actie vereist):**
Zoek naar mails die voldoen aan één of meer van deze criteria:
- Ongelezen én ontvangen in de afgelopen 48 uur
- Bevatten urgentie-woorden: "urgent", "asap", "deadline", "vandaag", "today", "z.s.m.", "zo snel mogelijk", "uiterlijk", "vóór"
- Zijn een reply die al meer dan 24u wacht op een reactie
- Zijn van bekende zakenrelaties of partners (Khalid, Koen, Sebastian, artiesten, sponsors)

Gebruik `gmail_search_messages` met query's zoals:
- `is:unread newer_than:2d` — recente ongelezen mails
- `is:unread subject:(urgent OR deadline OR vandaag OR asap)` — urgente ongelezen mails

**B. Achterstallige mails (al 24u+ geen reply):**
Zoek naar threads waarbij de laatste mail van jou al 24u of langer geleden is en er nog geen antwoord is binnengekomen, of threads waarbij jij de ontvanger bent en nog niet gereageerd hebt.

Gebruik `gmail_search_messages` met: `is:unread older_than:1d` als aanvulling.

Lees de relevante mails (`gmail_read_message`) om onderwerp en urgentieniveau te begrijpen. Beperk je tot maximaal 8-10 mails — kies de meest relevante.

---

## Stap 4 — Analyseer en prioriteer

Nu je alle data hebt, maak je een prioriteitenlijst voor de dag:

**Prioriteit bepalen:**
- 🔴 **Hoog** — Deadline vandaag, urgente mail, meeting binnen 2 uur
- 🟡 **Middel** — Mail die 24u+ wacht, afspraak later vandaag, BWC-event binnen 3 dagen
- 🟢 **Laag** — Informatieve mails, events verder dan 3 dagen weg

**Focustip:**
Kijk naar de workload van de dag en formuleer één concrete focustip. Bijvoorbeeld:
- "Je hebt 2 meetings en 3 urgente mails — begin met de mail van [naam] vóór je eerste meeting."
- "Lichte dag qua meetings — goed moment om achterstallige mails af te handelen."
- "Lizzy is over 2 dagen — check of het productieformulier al klaar is."

---

## Stap 5 — Genereer de HTML-briefing

Sla de briefing op als HTML-bestand in de workspace map: `morning-briefing-[datum].html`

Gebruik het onderstaande HTML-template als basis. Vul alle secties in met de opgehaalde data. Als een sectie leeg is (bijv. geen urgente mails), toon dan een vriendelijk bericht zoals "Alles rustig op dit front ✓".

### HTML Template

```html
<!DOCTYPE html>
<html lang="nl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>BWC Morning Briefing — [DATUM]</title>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;900&display=swap');

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Inter', sans-serif;
      background: #0a0a0a;
      color: #ffffff;
      min-height: 100vh;
      padding: 0;
    }

    /* Header */
    .header {
      background: linear-gradient(135deg, #111111 0%, #1a1a1a 100%);
      border-bottom: 1px solid #222;
      padding: 40px 60px 32px;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
    }

    .header-left .greeting {
      font-size: 13px;
      font-weight: 500;
      color: #888;
      text-transform: uppercase;
      letter-spacing: 2px;
      margin-bottom: 8px;
    }

    .header-left .name {
      font-size: 36px;
      font-weight: 900;
      color: #ffffff;
      line-height: 1;
    }

    .header-left .name span {
      color: #c8f542;
    }

    .header-right {
      text-align: right;
    }

    .header-right .date {
      font-size: 14px;
      color: #666;
      font-weight: 400;
    }

    .header-right .time {
      font-size: 28px;
      font-weight: 700;
      color: #ffffff;
      margin-top: 4px;
    }

    .bwc-logo {
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: #444;
      margin-top: 8px;
    }

    /* Focus strip */
    .focus-strip {
      background: linear-gradient(90deg, #c8f542 0%, #a8d432 100%);
      padding: 14px 60px;
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .focus-strip .label {
      font-size: 10px;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 2px;
      color: #000;
      white-space: nowrap;
    }

    .focus-strip .text {
      font-size: 14px;
      font-weight: 500;
      color: #000;
    }

    /* Main content */
    .content {
      padding: 40px 60px;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
      max-width: 1400px;
    }

    /* Cards */
    .card {
      background: #111111;
      border: 1px solid #1e1e1e;
      border-radius: 12px;
      overflow: hidden;
    }

    .card.full-width {
      grid-column: 1 / -1;
    }

    .card-header {
      padding: 20px 24px 16px;
      border-bottom: 1px solid #1e1e1e;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .card-header .icon {
      font-size: 18px;
    }

    .card-header h2 {
      font-size: 13px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1.5px;
      color: #ffffff;
    }

    .card-header .count {
      margin-left: auto;
      background: #1e1e1e;
      color: #888;
      font-size: 11px;
      font-weight: 600;
      padding: 3px 10px;
      border-radius: 20px;
    }

    .card-header .count.urgent {
      background: rgba(255, 75, 75, 0.15);
      color: #ff4b4b;
    }

    .card-body {
      padding: 8px 0;
    }

    /* Agenda items */
    .agenda-item {
      padding: 14px 24px;
      border-bottom: 1px solid #161616;
      display: flex;
      gap: 16px;
      align-items: flex-start;
      transition: background 0.15s;
    }

    .agenda-item:last-child { border-bottom: none; }
    .agenda-item:hover { background: #151515; }

    .agenda-time {
      min-width: 60px;
      font-size: 12px;
      font-weight: 600;
      color: #c8f542;
      padding-top: 2px;
    }

    .agenda-details .title {
      font-size: 14px;
      font-weight: 500;
      color: #ffffff;
      margin-bottom: 3px;
    }

    .agenda-details .meta {
      font-size: 12px;
      color: #555;
    }

    /* Mail items */
    .mail-item {
      padding: 14px 24px;
      border-bottom: 1px solid #161616;
      display: flex;
      gap: 12px;
      align-items: flex-start;
      transition: background 0.15s;
    }

    .mail-item:last-child { border-bottom: none; }
    .mail-item:hover { background: #151515; }

    .priority-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      margin-top: 5px;
      flex-shrink: 0;
    }

    .priority-dot.high { background: #ff4b4b; }
    .priority-dot.medium { background: #ffb830; }
    .priority-dot.low { background: #4bff91; }

    .mail-details .sender {
      font-size: 12px;
      font-weight: 600;
      color: #888;
      margin-bottom: 3px;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .mail-details .subject {
      font-size: 14px;
      font-weight: 500;
      color: #ffffff;
      margin-bottom: 3px;
    }

    .mail-details .preview {
      font-size: 12px;
      color: #555;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 400px;
    }

    .mail-details .age {
      font-size: 11px;
      color: #ff4b4b;
      margin-top: 4px;
      font-weight: 500;
    }

    /* Events (aankomend) */
    .event-item {
      padding: 14px 24px;
      border-bottom: 1px solid #161616;
      display: flex;
      align-items: center;
      gap: 16px;
    }

    .event-item:last-child { border-bottom: none; }

    .event-badge {
      padding: 4px 12px;
      border-radius: 20px;
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 1px;
      white-space: nowrap;
    }

    /* Concept kleuren */
    .badge-lizzy { background: rgba(255, 200, 80, 0.15); color: #ffc850; }
    .badge-clear { background: rgba(80, 160, 255, 0.15); color: #50a0ff; }
    .badge-novia { background: rgba(200, 80, 255, 0.15); color: #c850ff; }
    .badge-lola { background: rgba(255, 80, 120, 0.15); color: #ff5078; }
    .badge-luna { background: rgba(80, 255, 200, 0.15); color: #50ffc8; }
    .badge-lush { background: rgba(255, 120, 200, 0.15); color: #ff78c8; }
    .badge-default { background: rgba(200, 245, 66, 0.15); color: #c8f542; }

    .event-info .name {
      font-size: 14px;
      font-weight: 600;
      color: #ffffff;
      margin-bottom: 2px;
    }

    .event-info .date {
      font-size: 12px;
      color: #555;
    }

    .event-countdown {
      margin-left: auto;
      font-size: 12px;
      font-weight: 700;
      color: #888;
    }

    .event-countdown.soon { color: #ffb830; }
    .event-countdown.urgent { color: #ff4b4b; }

    /* Empty state */
    .empty-state {
      padding: 28px 24px;
      text-align: center;
      color: #333;
      font-size: 13px;
    }

    .empty-state .check { font-size: 20px; margin-bottom: 6px; }

    /* Footer */
    .footer {
      padding: 24px 60px;
      border-top: 1px solid #1a1a1a;
      display: flex;
      justify-content: space-between;
      align-items: center;
      color: #2a2a2a;
      font-size: 11px;
      font-weight: 500;
      text-transform: uppercase;
      letter-spacing: 1.5px;
    }

    /* Responsive */
    @media (max-width: 900px) {
      .content { grid-template-columns: 1fr; padding: 24px; }
      .header { padding: 28px 24px 20px; flex-direction: column; align-items: flex-start; gap: 12px; }
      .focus-strip { padding: 14px 24px; }
      .footer { padding: 20px 24px; }
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <div class="header">
    <div class="header-left">
      <div class="greeting">Good morning</div>
      <div class="name">Goedemorgen, <span>[NAAM]</span> 👋</div>
    </div>
    <div class="header-right">
      <div class="date">[DAG], [DATUM]</div>
      <div class="time">[TIJD]</div>
      <div class="bwc-logo">Bloom with Colour</div>
    </div>
  </div>

  <!-- FOCUS STRIP -->
  <div class="focus-strip">
    <div class="label">⚡ Focus vandaag</div>
    <div class="text">[FOCUSTIP]</div>
  </div>

  <!-- CONTENT GRID -->
  <div class="content">

    <!-- AGENDA VANDAAG -->
    <div class="card">
      <div class="card-header">
        <span class="icon">📅</span>
        <h2>Agenda vandaag</h2>
        <span class="count">[AANTAL] afspraken</span>
      </div>
      <div class="card-body">
        <!-- AGENDA ITEMS HIER — of empty state -->
        <!--
        <div class="agenda-item">
          <div class="agenda-time">10:00</div>
          <div class="agenda-details">
            <div class="title">Meeting met Khalid</div>
            <div class="meta">Google Meet · 45 min</div>
          </div>
        </div>
        -->
      </div>
    </div>

    <!-- URGENTE MAILS -->
    <div class="card">
      <div class="card-header">
        <span class="icon">📬</span>
        <h2>Urgente mails</h2>
        <span class="count urgent">[AANTAL] actie vereist</span>
      </div>
      <div class="card-body">
        <!-- MAIL ITEMS HIER — of empty state -->
        <!--
        <div class="mail-item">
          <div class="priority-dot high"></div>
          <div class="mail-details">
            <div class="sender">Khalid Oubaha</div>
            <div class="subject">Contract verlenging Club Novia</div>
            <div class="preview">Hey, kunnen we vandaag nog even...</div>
          </div>
        </div>
        -->
      </div>
    </div>

    <!-- ACHTERSTALLIGE MAILS -->
    <div class="card">
      <div class="card-header">
        <span class="icon">⏳</span>
        <h2>Wacht op reactie</h2>
        <span class="count">[AANTAL] openstaand</span>
      </div>
      <div class="card-body">
        <!-- ACHTERSTALLIGE MAILS HIER -->
      </div>
    </div>

    <!-- AANKOMENDE BWC EVENTS -->
    <div class="card">
      <div class="card-header">
        <span class="icon">🎉</span>
        <h2>Aankomende events</h2>
        <span class="count">[AANTAL] deze week</span>
      </div>
      <div class="card-body">
        <!-- EVENT ITEMS HIER -->
        <!--
        <div class="event-item">
          <div class="event-badge badge-lizzy">Lizzy</div>
          <div class="event-info">
            <div class="name">Lizzy op Donderdag</div>
            <div class="date">Donderdag 27 maart · Rolluik</div>
          </div>
          <div class="event-countdown soon">2 dagen</div>
        </div>
        -->
      </div>
    </div>

  </div>

  <!-- FOOTER -->
  <div class="footer">
    <span>Bloom with Colour — Internal Briefing</span>
    <span>Gegenereerd door Barry · [DATUM]</span>
  </div>

</body>
</html>
```

---

## Stap 6 — Sla het bestand op en presenteer het

1. Vul alle `[PLACEHOLDERS]` in met de echte data
2. Sla op als `/sessions/sweet-eager-fermat/mnt/Claude Co-work/morning-briefing-[JJJJ-MM-DD].html`
3. Geef de gebruiker een directe link naar het bestand

---

## Stap 7 — Gebruikersprofiel opslaan (eerste keer)

Als er nog geen profielbestand bestaat, maak dan aan:
`/sessions/sweet-eager-fermat/mnt/.claude/profiles/[naam].json`

```json
{
  "naam": "Tim",
  "rol": "Stagiair / Innovatieproject",
  "focus": ["acquisitie", "skills", "innovatie"],
  "concepten": ["alle"],
  "email": "timpoelmansbwc@gmail.com"
}
```

Bij volgende briefings wordt dit profiel automatisch ingeladen om de briefing te personaliseren (naam in de header, gefilterde mails op basis van rol, relevante events).

---

## Concept-badge mapping

Gebruik deze mapping om events automatisch de juiste kleur/badge te geven:

| Zoekterm in eventnaam | Badge class | Naam |
|---|---|---|
| lizzy | badge-lizzy | Lizzy op Donderdag |
| clear | badge-clear | Clear |
| novia | badge-novia | Club Novia |
| lola | badge-lola | Secret Lola |
| luna | badge-luna | That's What Luna Said |
| lush | badge-lush | Louder Than Lush |
| kaya / urban | badge-default | Kaya |
| overig | badge-default | BWC Event |

---

## Toon & stijl richtlijnen

- **Naam**: gebruik altijd de voornaam van de medewerker, nooit de achternaam
- **Taal**: Nederlands, tenzij mails/events in het Engels zijn
- **Emojis**: spaarzaam — alleen in de header en bij de focustip
- **Prioriteit**: wees direct en concreet — geen vaagheden
- **Lege secties**: nooit weglaten, altijd een korte bevestiging tonen ("Niets gepland vandaag ✓")
- **Mails samenvatten**: nooit letterlijk citeren — parafraseer in max. 1 zin
