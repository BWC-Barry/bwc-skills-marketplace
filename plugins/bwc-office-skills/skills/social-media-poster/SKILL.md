---
name: social-media-poster
description: >
  Maakt complete Instagram posts (foto's + caption + checklist) voor elke nachtzaak
  die met de brand-mapper skill in kaart is gebracht. Account-agnostisch: leest dynamisch
  een brand-context bestand in en past de werkwijze daarop aan. Vervangt op termijn
  de hardcoded social-media-manager skill. Activeer wanneer Tim, Lotte of een ander
  teamlid vraagt om een post, caption, foto's, content, weekendrecap of weekplanning
  voor een specifieke zaak — ook als ze het woord "skill" niet noemen. Triggers:
  "post voor [zaak]", "caption schrijven", "foto's zoeken voor [zaak]", "weekendrecap",
  "ticketpush", "announcement post", "story voor [zaak]".
---

# Social Media Poster — posts maken op basis van brand-context

---

## Doel

Per aanvraag een volledig kant-en-klaar pakket opleveren:

1. Foto's gevonden in Google Drive, gedownload, gecheckt op dubbelen
2. Twee tot drie captionvarianten, passend bij de tone of voice van de zaak
3. Checklist met alle vaste regels voor publicatie (likes, tags, fotograaf, muziek)

De skill leest dynamisch het brand-context bestand voor de gevraagde zaak. Daardoor
werkt 'ie zowel voor BWC-concepten als KO-zaken zonder dat de skill zelf aangepast
hoeft te worden.

---

## Eerste keer? Even jezelf instellen

Bij de eerste run vragen en onthouden voor de hele sessie:

**Werk-emailadres (`{USER_EMAIL}`)** — moet `bwc` of `ko` in de naam bevatten.

- Vraag: "Wat is jouw werk-emailadres voor Google Drive?"
- Valideer: het adres bevat `bwc` of `ko`
- Bevat het adres geen van beide? Vraag opnieuw

---

## Werkwijze bij elke aanvraag

### Stap 1 — Identificeer de zaak en laad brand-context

1. Zoek in de gebruikersvraag naar welke zaak het gaat (Lizzy, Clear, Novia, Aspen
   Valley, Fifth Avenue, etc.)
2. Bepaal de slug (bijv. "aspen-valley-enschede", "lizzy-op-donderdag")
3. Zoek het brand-context bestand in deze volgorde:

   **Pad 1 (lokaal, meest recent):**
   `~/Desktop/Claude Co-work/brand-contexts/brand-context-[slug].md`

   **Pad 2 (marketplace, team-shared):**
   `~/Desktop/Claude Co-work/BWC Skills Marketplace/online-hub-template/plugins/bwc-office-skills/brand-contexts/brand-context-[slug].md`

   Voor team-leden die de plugin via marketplace hebben geinstalleerd, kan pad 2
   onder `~/Library/Application Support/Claude/...` of een vergelijkbaar
   plugin-installatie-pad staan. Zoek desnoods met:
   ```bash
   find ~ -name "brand-context-[slug].md" 2>/dev/null
   ```

4. Bestaat het bestand op geen van beide locaties? Vraag de gebruiker om eerst de
   brand-mapper skill te draaien voor deze zaak. Geef de exacte trigger-zin:
   "Barry, breng [zaak] in kaart"
5. Lees het gevonden bestand volledig en gebruik het als leidraad voor alle
   vervolgstappen
6. Als zowel pad 1 als pad 2 bestaan en ze verschillen: gebruik pad 1 (lokaal is
   leidend) en meld de gebruiker dat er een update beschikbaar is in de
   marketplace versie

---

### Stap 2 — Begrijp de brief volledig

Vraag door wat ontbreekt:

- **Welke zaak?** (al bevestigd in stap 1)
- **Wat is de insteek?** Weekendrecap, sfeerimpressie, announcement, ticketpush,
  event-dag, aftermovie, DJ host night, count-down, sold-out, etc.
- **Datum of event?** (indien relevant)
- **DJ's of artiesten?** Met Instagram-handles voor tagging
- **Type post?** Feedpost, reel, story, carrousel
- **Stadnaam?** (indien relevant voor format met caps-stadnaam)

---

### Stap 3 — Lees live de actuele Instagram-feed

*Doe dit altijd. De brand-context geeft het patroon, maar de feed laat zien wat er
de afgelopen weken speelde. Daarmee voorkom je dat je dezelfde formule herhaalt
die al recent gebruikt is.*

Navigeer naar `instagram.com/[handle]/` (handle uit de brand-context).

Bekijk de laatste 10 tot 15 posts en let op:

- Welke recente formules zijn al gebruikt
- Welke woorden of zinnen zijn recent uitvergroot
- Welke foto's zijn gepost (voor dubbelen-check later)
- Welke sfeer staat momenteel in het account

---

### Stap 4 — Zoek passende foto's in Google Drive

Volg het Drive-pad uit de brand-context, sectie 5.

1. Open Chrome en ga naar `drive.google.com`, ingelogd als `{USER_EMAIL}`
2. Navigeer naar het pad in de brand-context
3. Open de map die past bij de brief (meest recent event, of een specifieke editie)
4. Bekijk de foto's en selecteer 4 tot 6 opties die passen
5. Bij twijfel: hou er meer over dan minder

**Richtlijnen voor fotokeuze:** gebruik de fotostijl-omschrijving uit brand-context
sectie 3.

---

### Stap 5 — Controleer op dubbelen

1. Ga terug naar Instagram van de zaak
2. Scroll door de laatste 30 posts en bekijk de beelden
3. Vergelijk geselecteerde foto's met wat al gepost is
4. Bij twijfel: zet een ⚠️ bij de foto en meld het in stap 8

---

### Stap 6 — Download de geselecteerde foto's

Het doel: de gebruiker hoeft niks meer op te zoeken. Alles staat klaar.

**Downloaden uit Google Drive via de browser:**

1. Open elke geselecteerde foto in Drive (klikken zodat 'ie groot wordt)
2. Klik op de drie puntjes rechtsboven → "Downloaden"
3. Herhaal voor elke foto

**Organiseer de downloads:**

- Maak een nieuwe map in de Cowork-werkmap met de naam:
  `[Zaak] - [Datum] - Klaar om te posten`
  Voorbeeld: `Aspen Valley Enschede - 24.05.2026 - Klaar om te posten`
- Verplaats alle gedownloade foto's naar deze map
- Hernoem onduidelijke bestanden naar `foto-1.jpg`, `foto-2.jpg`, etc.

---

### Stap 7 — Schrijf 2 tot 3 captionvarianten

Gebruik de tone of voice, vaste sluitingen, signature emojis en terugkerende woorden
uit brand-context sectie 2. Volg de formule die past bij het posttype uit sectie 4.

**Schrijf geen kopie van een bestaande caption.** Gebruik ze als inspiratie voor
ritme, energie en woordkeuze.

Lever:

- **Korte versie** (1 tot 3 regels, voor story of minimalistische feed)
- **Middellange versie** (4 tot 7 regels, standaard feedpost)
- **Uitgebreide versie** (alleen als de brief om een announcement of speciale editie
  vraagt)

Geef per variant aan:

- Geschikt voor feed of story
- Welke foto's er het beste bij passen
- Welke DJ's en venues getagd moeten worden

---

### Stap 8 — Lever het resultaat op

Format:

**📁 Foto's**

Geef voor elke foto een directe `computer://` link met opmerking over geschiktheid:

```
- foto-1.jpg ✅ — past bij variant B (sfeerbeeld + crowd)
- foto-2.jpg ✅ — alternatief voor variant A
- foto-3.jpg ⚠️ — vergelijkbaar met post van 12.05, dubbelcheck zelf
```

Geef ook de maplink zodat de gebruiker alles in één keer kan openen.

**✍️ Caption-varianten**

Alle varianten met korte toelichting per variant.

**📋 Checklist voor publicatie**

Op basis van brand-context sectie 6. Voorbeeld:

```
- [ ] Likes uitzetten
- [ ] DJ's taggen: @dj1, @dj2
- [ ] Fotograaf taggen: @[handle]
- [ ] Shared met: @[partner]
- [ ] Adverteren: ja/nee
- [ ] Pinnen: ja/nee
- [ ] Muziek toevoegen: [stijl]
```

---

## Beslis-flow bij ontbrekende informatie

| Situatie | Wat te doen |
|---|---|
| Brand-context bestaat niet | Vraag om eerst brand-mapper te draaien |
| Drive-pad in context onvolledig | Vraag het juiste pad en bied aan brand-context bij te werken |
| Instagram-handle niet bereikbaar | Vraag of account privé of opgeheven is, log en stop |
| Geen geschikte foto's gevonden | Vraag of er een alternatieve map is, of stel voor om de brief aan te passen |
| Gebruiker vraagt om concept dat niet in brand-context staat | Stel voor brand-mapper te draaien, niet improviseren |

---

## Wat deze skill niet doet

- Brand-context bestanden maken (dat doet brand-mapper)
- Posten op Instagram (publicatie blijft handmatig door de gebruiker)
- Stories editen met grafische templates (separate workflow, eventueel in CapCut)
- Reels monteren (separate workflow)

---

## Backwards compatibility

Voor BWC-concepten die nog in de oude `social-media-manager` skill staan (Lizzy,
Clear, Novia, Secret Lola, Luna, Lush, After 16 Hours) kun je deze skill al gebruiken
zodra de overeenkomstige brand-context bestanden bestaan. Tot die tijd blijft de
oude skill werken als fallback.

Migratiepad:

1. Draai brand-mapper voor één BWC-concept
2. Valideer dat de gegenereerde brand-context overeenkomt met de bestaande hardcoded
   informatie
3. Test social-media-poster met dat concept
4. Herhaal voor de andere concepten
5. Zodra alle 7 concepten een brand-context hebben: social-media-manager skill
   uitfaseren

---

## Bekende beperkingen

- Brand-contexts worden in twee folders gezocht (lokale werkmap eerst, marketplace
  folder als fallback). Synchronisatie tussen team-leden gebeurt via een git push
  naar de marketplace repo door wie de brand-mapper draaide.
- Foto-selectie is observationeel, geen automatische visuele match-scoring.
- Instagram-feed-analyse vereist Chrome MCP toegang.
