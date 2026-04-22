# BWC Skills Marketplace

> De officiële verzameling skills van Bloom with Colour — voor het hele office team.

![status](https://img.shields.io/badge/status-preview-yellow) ![versie](https://img.shields.io/badge/versie-1.0.0-red)

## Wat is dit?

Dit is de centrale repo waar alle BWC-skills wonen. Als Tim een skill aanpast of een nieuwe toevoegt, komt die update **automatisch** binnen bij alle medewerkers die deze marketplace hebben geïnstalleerd in Cowork. Eén keer installeren, daarna werkt alles vanzelf mee.

## Voor medewerkers — installatie in Cowork

### Eenmalige setup (3 minuten)

1. Open de **Claude desktop app** en zorg dat **Cowork mode** aanstaat.
2. Ga naar **Settings → Plugins → Marketplaces**.
3. Klik op **"Add marketplace"**.
4. Plak deze URL:

   ```
   BWC-Barry/bwc-skills-marketplace
   ```

5. Klik op **"BWC Concepts Skills"** in de lijst → **Install**.
6. Klaar! Barry heeft nu alle 7 skills paraat.

### Na de install

Typ iets als:

- `/briefing` — voor je dagstart
- "Barry, maak een ticketlink voor Lizzy op 25 april" — Eventlink
- "Barry, verwerk de facturen van deze week" — Facturen
- "Barry, maak een weekendrecap voor Club Novia" — Social Media

Voor elke skill is er een **installatie-dialoog**: Barry loopt je bij eerste gebruik door een korte check heen om te zorgen dat je de juiste toegangen hebt.

## Voor Tim — een skill updaten

1. Open de skill lokaal in je editor (de folder in deze repo).
2. Pas de `SKILL.md` of scripts aan.
3. Commit + push naar GitHub:

   ```bash
   git add .
   git commit -m "update social-media-manager: nieuwe template voor reels"
   git push
   ```

4. Verhoog het versienummer in `.claude-plugin/marketplace.json` (bv. `1.0.0` → `1.0.1`).
5. Medewerkers krijgen de update automatisch zodra ze Cowork opnieuw openen.

## Welke skills zitten erin?

| # | Skill | Wat doet 'ie? | Voor wie? |
|---|---|---|---|
| 1 | 🧠 BWC Context | Organisatie-kennisbank (team, concepten, venues) | Iedereen — auto-load |
| 2 | 🌅 Morning Briefing | Dagstart met agenda + mails | Iedereen |
| 3 | 🎟 Eventlink | Ticket- en gastenlijstlinks via Weeztix | Projectmanagers |
| 4 | 📋 Productieformulier | Automatisch ingevulde productieformulieren | Advancing |
| 5 | 💶 Facturen Bijwerken | Wekelijkse factuurverwerking | Finance |
| 6 | 📧 Invoice Reminder | DJ-factuurherinneringen via Gmail | Finance |
| 7 | 📸 Social Media Manager | Content voor alle BWC-concepten | Marketing |

## Structuur van deze repo

```
bwc-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json         ← welke plugins zijn beschikbaar
├── plugins/
│   └── bwc-office-skills/
│       ├── .claude-plugin/
│       │   └── plugin.json      ← plugin metadata
│       └── skills/
│           ├── bwc-context/          ← organisatie-kennisbank (auto-loads)
│           │   └── SKILL.md
│           ├── morning-briefing/
│           │   ├── SKILL.md
│           │   └── ...
│           ├── eventlink/
│           ├── productieformulier/
│           ├── facturen-bijwerken/
│           ├── invoice-reminder/
│           └── social-media-manager/
└── README.md
```

## Nieuwe skill toevoegen

1. Maak een nieuwe map onder `plugins/bwc-office-skills/skills/[nieuwe-skill]/`.
2. Voeg een `SKILL.md` toe (zie de bestaande als voorbeeld).
3. Registreer de skill in `plugins/bwc-office-skills/.claude-plugin/plugin.json` onder `"skills"`.
4. Commit + push.
5. De nieuwe skill verschijnt automatisch bij alle teamleden.

## Support

Iets werkt niet? Stuur Tim een bericht op Slack met een screenshot. Ziet hij dat meer mensen hetzelfde hebben, dan komt het in de FAQ van het handboek.

---

**Bloom with Colour** · Intern gebruik · Gemaakt door Tim & Barry
