---
name: brand-mapper
description: >
  Brengt een nachtzaak, festival of nightlife-concept volledig in kaart en levert
  een herbruikbaar brand-context bestand op. Analyseert live de laatste 25 Instagram
  posts voor tone of voice, leest het brandbook indien beschikbaar, extracten visuele
  identity (kleuren, fotostijl, typografie), en interviewt de gebruiker over voorbeelden
  en smaakkaders. Output is één markdown-file die de social-media-poster skill daarna
  dynamisch kan inlezen. Activeer wanneer een nieuwe zaak of concept aan het Barry-systeem
  toegevoegd moet worden, ook als de gebruiker het woord "skill" niet noemt. Triggers:
  "nieuwe zaak", "concept in kaart brengen", "brand mappen", "Aspen Valley toevoegen",
  "Fifth Avenue setup", "branding voor [zaak]", "tone of voice analyseren".
---

# Brand Mapper — een zaak volledig in kaart brengen

---

## Doel

Per nieuwe nachtzaak of concept één compleet brand-context bestand opleveren dat alle
informatie bevat die de social-media-poster skill later nodig heeft:

- Tone of voice met echte voorbeelden uit de live Instagram-feed
- Vaste woorden, signature emojis, sluitingsformules
- Contentfrequentie en formules per dag-type
- Visuele identity: kleuren, fotostijl, typografie, sfeer
- Drive-pad naar foto's en mapnaming-conventies
- Vaste regels: tagging, fotograaf, advertenties, pinning
- Do's en don'ts uit de mond van de gebruiker zelf

**Eindresultaat:** `~/Desktop/Claude Co-work/brand-contexts/brand-context-[zaak-slug].md`

Optioneel ook gepusht naar de gedeelde marketplace-folder zodat het hele team de
context direct beschikbaar heeft via een plugin-update.

Dit bestand is account-onafhankelijk. Het werkt op elk Claude-account (BWC, KO, ander).

---

## Eerste keer? Even jezelf instellen

Bij de eerste run vragen en onthouden voor de hele sessie:

**Werk-emailadres (`{USER_EMAIL}`)** — moet `bwc` of `ko` in de naam bevatten.

- Vraag: "Wat is jouw werk-emailadres voor Google Drive?"
- Valideer: het adres bevat `bwc` of `ko` (bijv. `lottebwc@gmail.com`, `lotteko@gmail.com`)
- Bevat het adres geen `bwc` of `ko`? Vraag opnieuw

---

## Werkwijze

### Stap 0 — Briefing

Voordat je begint, zorg dat je het volgende weet. Vraag door wat ontbreekt.

- **Zaaknaam** voluit (bijv. "Aspen Valley Enschede", "Fifth Avenue Arnhem")
- **Slug** voor bestandsnaam (bijv. `aspen-valley-enschede`)
- **Instagram-handle** (zonder @)
- **Brandbook beschikbaar?** Ja → waar (Drive-link, lokaal pad, of platgeplakte tekst)
- **Drive-map met foto's** (pad of link)
- **Welke organisatie** (BWC, KO, ander)
- **Welke schrijftaal** (NL, EN, mix)
- **Doelgroep** in één zin

---

### Stap 1 — Live Instagram-analyse van 25 posts

*Doe dit altijd. Vertrouw nooit op aannames over een merk, ook niet als de gebruiker
denkt te weten hoe het klinkt. De feed is de waarheid.*

Navigeer via Chrome MCP naar `instagram.com/[handle]/`.

Verzamel van de **laatste 25 posts/reels**:

1. Caption volledig
2. Datum
3. Posttype: feedpost, reel, carrousel, foto
4. Geschatte caption-lengte in regels en woorden
5. Aanwezige emojis
6. Aanwezige hashtags (vaak: geen, soms wel)
7. Mentions (@accounts)
8. Visuele observatie van de cover: foto van mensen, DJ-shot, sfeerbeeld, grafisch, flyer, etc.

Verwerk de 25 captions tot een patroon-analyse:

- **Caption-lengte-verdeling**: gemiddeld, kortste, langste
- **Taal**: NL, EN, of mix (en welke verhouding)
- **Emoji-frequentie**: gemiddeld per post + welke emojis terugkeren
- **Vaste openers**: zinnen of woorden die meerdere keren als opening voorkomen
- **Vaste sluitingen**: hoe eindigen captions doorgaans
- **Terugkerende woorden**: top 15 unieke woorden of uitdrukkingen die karakteristiek zijn
- **Terugkerende mentions**: vaste partners, venues, fotografen
- **Format-verdeling**: % carrousel / reel / foto
- **Posting-frequentie**: gemiddeld aantal posts per week, en welke dagen

---

### Stap 2 — Brandbook lezen

Als de gebruiker een brandbook heeft aangeleverd:

1. Open het bestand of de Drive-link
2. Lees aandachtig op:
   - Missie, visie, positionering
   - Tone of voice-richtlijnen (vaak opgeschreven, ook al schrijft het account er soms anders)
   - Visuele richtlijnen: kleuren met hex-waarden, fonts, logo-gebruik, fotorichting
   - Vaste woordvoering: do's en don'ts uit het brandbook zelf
3. Noteer waar het brandbook afwijkt van wat je in stap 1 zag op de live feed
4. **Bij conflict tussen brandbook en live feed wint de live feed altijd.** Het brandbook
   is theorie, de feed is praktijk. Noteer de afwijking wel zodat de gebruiker beslist
   of het brandbook moet worden bijgewerkt.

Geen brandbook? Skip deze stap en noteer dat in de output.

---

### Stap 3 — Visuele identity extraheren

Doel: design tokens van de zaak vastleggen zodat de social-media-poster ze later
mee kan nemen als referentie voor fotokeuze en eventuele templates.

Verzamel uit de Instagram-feed en eventueel brandbook:

- **Primaire kleur(en)** in hex (uit logo, terugkerende huisstijl)
- **Secundaire kleuren**
- **Typografie**: welke fonts worden gebruikt op flyers en grafische posts
- **Fotostijl**: donker/licht, hoog contrast, warm/koel, close-ups vs wide shots,
  veel mensen of weinig, gezichten of anoniem, sfeer of action
- **Logo-richtlijnen**: hoe verschijnt het logo (op flyers, in stories, als watermark)
- **Visuele patronen**: zijn er terugkerende grafische elementen (cirkels, gradients,
  glitch, glow, vintage filter, etc.)

*Optioneel: roep de impeccable skill aan als je een design-systeem-extractie wilt op
basis van de website of een mockup. Niet primair, want impeccable is gemaakt voor
frontend code-extractie. Voor pure brand-mapping is bovenstaande lijst voldoende.*

---

### Stap 4 — Interview de gebruiker

Stel deze vragen één voor één. Wacht op antwoord. Vat samen en bevestig voor je
verder gaat.

**Smaakkader:**

1. Welke vijf recente posts van dit account vind je echt raak? Geef de datum of de
   eerste regel zodat ik ze kan terugvinden. Wat maakt ze raak?
2. Welke twee tot drie posts vind je juist niet werken? Waarom niet?
3. Welke woorden of zinnen wil je dat we altijd gebruiken?
4. Welke woorden of zinnen mogen we nooit gebruiken?
5. Welke fouten maakt onze huidige social media manager soms die we niet meer willen
   zien?

**Vaste regels:**

6. Likes aan of uit standaard?
7. Welke partners taggen we altijd (venues, fotografen, sponsors)?
8. Welke DJ-handles zijn vaste prik?
9. Pinnen we announcements? Welke posttypes wel, welke niet?
10. Adverteren we standaard? Welke posttypes wel, welke niet?
11. Voegen we muziek toe aan elke post? Welke stijl muziek bij welk posttype?
12. Worden posts soms gedeeld met andere accounts (collab posts)? Met wie?

**Drive en mapstructuur:**

13. Wat is het pad in Google Drive naar de foto's van deze zaak?
14. Hoe heten de mappen (bijv. "[Zaak] [datum]" of anders)?
15. Hoe oud mogen foto's zijn voordat we ze niet meer gebruiken?
16. Worden foto's per editie verzameld of per maand of per jaar?

**Content-frequentie:**

17. Hoeveel posts per week is normaal voor deze zaak?
18. Zijn er vaste dagen (bijv. announcement op maandag, recap op zondag)?
19. Welke posttypes komen het meest voor (carrousel, reel, foto)?

---

### Stap 5 — Output genereren

Maak het bestand aan op pad `~/Desktop/Claude Co-work/brand-contexts/brand-context-[slug].md`
met onderstaande structuur. Vul alle secties in op basis van stap 1 tot en met 4.

Bestaat de folder `~/Desktop/Claude Co-work/brand-contexts/` nog niet? Maak 'm aan
voor je het bestand schrijft.

```markdown
# Brand Context: [Zaaknaam]

> Gegenereerd door brand-mapper skill op [datum]
> Organisatie: [BWC / KO / ander]
> Slug: [slug]

---

## 1. Basis

- **Naam:** [voluit]
- **Locatie(s):** [steden]
- **Instagram:** @[handle] — instagram.com/[handle]/
- **Doelgroep:** [één zin]
- **Taal:** [NL / EN / mix met verhouding]
- **Muziekstijl/concept:** [kort]

---

## 2. Tone of voice

### Wat dit account uniek maakt
[2 tot 4 zinnen, gedestilleerd uit de feed-analyse]

### Herkenbare elementen
- Signature emojis: [lijst]
- Vaste sluiting(en): [lijst]
- Vaste opener(s): [lijst]
- Terugkerende woorden: [top 15]
- Caption-lengte: [gemiddeld in regels en woorden]

### Echte voorbeelden van de feed
[3 tot 5 letterlijke captions, recent en representatief]

### Do's
[bullet list, eigen woorden van de gebruiker]

### Don'ts
[bullet list, eigen woorden van de gebruiker]

---

## 3. Visuele identity

- **Kleuren:** [hex-waarden]
- **Typografie:** [fonts of beschrijving]
- **Fotostijl:** [omschrijving]
- **Logo-gebruik:** [waar en hoe]
- **Visuele patronen:** [terugkerende elementen]

---

## 4. Content-frequentie en formules

| Dag | Posttype | Doel | Caption-formule |
|-----|----------|------|-----------------|
| [in te vullen] | | | |

- **Posts per week:** [aantal]
- **Format-verdeling:** [% carrousel / reel / foto]
- **Posting-momenten:** [tijden indien bekend]

---

## 5. Google Drive

- **Pad naar foto's:** [volledig pad]
- **Mapnaming-conventie:** [voorbeeld]
- **Hoe oud mogen foto's zijn:** [periode]

---

## 6. Vaste regels per post

- Likes: [aan / uit]
- Vaste tags: [lijst handles]
- Fotograaf taggen: [ja/nee, welke handle standaard]
- Shared met: [accounts]
- Pinnen: [welke posttypes]
- Adverteren: [welke posttypes]
- Muziek toevoegen: [ja/nee, stijl]

---

## 7. Conflicten brandbook versus live feed

[Indien van toepassing: noteer waar brandbook en live praktijk uit elkaar lopen,
en welke kant we volgen]

---

## 8. Bron-analyse

- **Aantal posts geanalyseerd:** 25
- **Periode:** [datum oudste post] tot [datum nieuwste post]
- **Brandbook gebruikt:** [ja/nee, locatie]
- **Interview afgenomen met:** [naam gebruiker]
- **Laatst bijgewerkt:** [datum]
```

---

### Stap 6 — Bevestig en lever op

1. Toon de gebruiker waar het bestand staat: `~/Desktop/Claude Co-work/brand-contexts/brand-context-[slug].md`
2. Geef een korte samenvatting van de belangrijkste bevindingen (5 bullets max)
3. Stel voor om direct een test-post te maken met de social-media-poster skill om
   de output te valideren

---

### Stap 7 — Delen met het team via de marketplace

Vraag de gebruiker:

> "Wil je deze brand-context delen met het team? Dan kopieer ik het bestand naar
> de marketplace-folder en push 'm naar GitHub. Vanaf dat moment hebben alle
> collega's met de BWC Skills Marketplace toegang tot deze context."

**Bij JA:**

1. Kopieer het bestand naar:
   `~/Desktop/Claude Co-work/BWC Skills Marketplace/online-hub-template/plugins/bwc-office-skills/brand-contexts/brand-context-[slug].md`
2. Voer uit in de terminal:
   ```bash
   cd "/Users/[user]/Desktop/Claude Co-work/BWC Skills Marketplace/online-hub-template"
   git add plugins/bwc-office-skills/brand-contexts/brand-context-[slug].md
   git commit -m "feat: brand-context voor [Zaaknaam]"
   git push
   ```
3. Bevestig dat de push gelukt is
4. Meld in de chat dat het team voortaan via een plugin-update deze context krijgt

**Bij NEE:**

- Het bestand blijft alleen lokaal. Geen probleem als 't nog WIP is.
- Wijs erop dat collega's deze zaak dan nog niet kunnen mappen met social-media-poster
  tenzij ze het bestand handmatig krijgen.

---

## Workflow-tips

- **Werk hardop.** Lees tijdens stap 1 elke 5 posts kort wat je ziet, zodat de
  gebruiker mee kan kijken en kan corrigeren als je verkeerd zit.
- **Niet alles in één run.** Als de gebruiker geen brandbook bij de hand heeft of
  Drive-pad niet weet, sla die stap over en markeer het als TODO in de output.
- **Hergebruik tussen zaken.** Als je een tweede zaak van dezelfde organisatie
  doet, vraag je ter referentie de eerste brand-context erbij en wijs op verschillen.
- **Update bestaande brand-contexts.** Bij significante feedwijzigingen kun je
  deze skill opnieuw draaien voor een al gemapte zaak. Sla dan op met `-v2` suffix
  en vraag of de oude vervangen mag worden.

---

## Wat deze skill niet doet

- Posts schrijven (dat doet social-media-poster)
- Foto's selecteren of downloaden (dat doet social-media-poster)
- Brand-context op meerdere accounts synchroniseren (handmatig of via volgende
  iteratie van deze skill)

---

## Bekende beperkingen

- Instagram-scraping vereist Chrome MCP toegang
- Brandbook-lezen werkt alleen als het in tekstvorm of bekend PDF-formaat is
- Visuele identity-extractie is observationeel, geen pixel-perfect kleurpicking
