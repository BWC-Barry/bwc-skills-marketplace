---
name: invoice-reminder
description: >
  BWC Concepts DJ Factuur Reminder systeem. Gebruik deze skill wanneer Tim
  een wekelijkse lijst van events en DJ's stuurt met ◦ (factuur ontbreekt) en
  ✓ (factuur ontvangen) symbolen. De skill parseert de lijst, zoekt de
  e-mailadressen op van DJ's met ontbrekende facturen, en maakt Gmail concepten
  aan via de Gmail MCP tool. Activeer altijd wanneer de gebruiker een lijst
  stuurt met eventnamen, datums, en DJ-namen met ◦/✓ symbolen.
---

# BWC Concepts - DJ Factuur Reminder Skill

## Doel
Verwerk de wekelijkse factuurlijst van BWC Concepts: stuur automatisch
reminder-concepten naar DJ's die hun factuur nog niet hebben ingediend.

## Werkwijze

### Stap 1: Parseer de lijst

Lees de invoerlijst van Tim. Alle regels met ◦ zijn DJ's met een ontbrekende
factuur. Groepeer per event (naam + datum).

### Stap 2: Zoek e-mailadressen op

**Gebruik altijd eerst de meest recente DJ-contacten CSV** die Tim heeft
geüpload. De bestandsnaam is iets als: `BWC DJ's, Doorhosts en Media Info - Blad1 (5).csv`
(gebruik de meest recente versie in de conversatie of workspace).

Lees dit bestand met de Read tool. De kolommen zijn:
`DJ/Handelsnaam | Tel Nr. | E-mail | Volledige naam | Presskit`

Zoek de DJ-naam (of een variatie, afkorting of alias) op in de eerste kolom.
Gebruik de `Volledige naam` kolom voor de aanhef (voornaam).

Als een DJ niet in de CSV staat, zoek dan via Gmail (eerdere factuurmails of
boekingsberichten van/naar die DJ).

**Meerdere events per DJ:** Combineer altijd in één e-mail — stuur nooit
meerdere losse mails naar dezelfde persoon. Noem alle gigs in de lijst.

### Stap 3: Maak Gmail concepten aan

Gebruik voor elke DJ de `gmail_create_draft` MCP tool met `contentType: text/html`
en de volledige HTML-body inclusief de Shayan-handtekening (zie E-mail format).

**Maak concepten aan voor ALLE DJ's met een bekend e-mailadres.**

### Stap 4: Rapporteer aan de gebruiker

Geef na afloop een overzicht:
- Hoeveel concepten aangemaakt + wie (naam + event)
- Wie NIET gevonden werd (niet in CSV, niet in Gmail)

Als er DJ's zonder e-mail zijn, maak dan ook automatisch een concept aan
naar Kelvin (kelvin@bwc-concepts.nl) met de lijst van ontbrekende DJ's
gegroepeerd per event, met als referentie "de lijst van deze week".

---

## E-mail format (HTML)

Gebruik **altijd** `contentType: text/html` en de volgende HTML-body met de
volledige Shayan-handtekening. Het woord "COLOUR" wordt weergegeven met
individuele gekleurde letters (Gmail ondersteunt GEEN CSS gradients op tekst).
Vervang de placeholders tussen [ ].

**Één gig:**

```html
<div style="font-family: Arial, sans-serif; font-size: 14px; color: #000000;">
<p>Hi [voornaam DJ],</p>

<p>Vanuit onze finance heb ik doorgekregen dat wij nog een factuur van jou missen.<br>
Het gaat om de factuur bij je gig:</p>

<ul>
  <li>[Eventnaam], [datum]</li>
</ul>

<p>Kan je deze naar <a href="mailto:finance@bwc-concepts.nl">finance@bwc-concepts.nl</a> sturen?</p>

<p>Alvast bedankt en een fijne dag!</p>

<br>
<table cellpadding="0" cellspacing="0" border="0" style="font-family: Arial, sans-serif; font-size: 13px;">
  <tr><td style="padding-bottom: 4px; color: #555555;">Met vriendelijke groet,</td></tr>
  <tr><td style="padding-bottom: 2px;"><strong>Shayan Kowsari</strong></td></tr>
  <tr><td style="padding-bottom: 2px; color: #555555;">Finance &amp; Advancing</td></tr>
  <tr>
    <td style="padding-bottom: 8px; font-weight: bold;">
      BLOOM WITH <span style="color:#CC0000;">C</span><span style="color:#228B22;">O</span><span style="color:#003DA5;">L</span><span style="color:#DAA520;">O</span><span style="color:#1E6FBA;">U</span><span style="color:#7B2D8E;">R</span>
    </td>
  </tr>
  <tr><td style="color: #555555; font-size: 12px;">Creative concept &amp; event agency</td></tr>
  <tr>
    <td style="font-size: 12px;">
      E-mail: <a href="mailto:finance@bwc-concepts.nl" style="color: #000000; text-decoration: none;">finance@bwc-concepts.nl</a>
      / <a href="mailto:advancing@bwc-concepts.nl" style="color: #000000; text-decoration: none;">advancing@bwc-concepts.nl</a>
    </td>
  </tr>
  <tr>
    <td style="font-size: 12px;">
      Website: <a href="https://www.bloomwithcolour.nl" style="color: #000000; text-decoration: none;">www.bloomwithcolour.nl</a>
    </td>
  </tr>
</table>
</div>
```

**Meerdere gigs** — zelfde template, maar:
- Meervoud in tekst: "nog facturen van jou missen" en "bij je gigs:"
- Meerdere `<li>` items in de `<ul>`
