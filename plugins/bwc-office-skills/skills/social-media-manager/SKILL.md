---
name: social-media-manager
description: >
  BWC Concepts Social Media Manager. Gebruik deze skill wanneer Tim vraagt om
  sociale media content te maken voor een BWC concept: Lizzy op Donderdag, Clear,
  Club Novia, Secret Lola, That's What Luna Said, Louder Than Lush of After 16 Hours.
  De skill analyseert live Instagram posts voor tone of voice, zoekt passende foto's
  in Google Drive, verifieert of foto's al gepost zijn, en schrijft originele captions.
  Activeer altijd wanneer Tim vraagt om een post, caption, foto's, content of een
  weekplanning voor een van de BWC concepten — ook als hij het woord "skill" niet noemt.
---

# BWC Concepts — Social Media Manager

---

## 🔧 Eerste keer? Even jezelf instellen

Deze skill is voor het hele BWC-team (meestal Marketing). Bij de eerste run bij een nieuwe gebruiker, vraag en onthoud deze waarde voor de rest van de sessie:

**BWC-e-mailadres (`{USER_EMAIL}`)** — **verplicht met `bwc` in de naam**.

- Vraag: "Wat is jouw BWC-e-mailadres voor Google Drive?"
- Valideer: het adres MOET de letters `bwc` bevatten (bijv. `kelvinbwc@gmail.com`, `ninabwc@gmail.com`, `timpoelmansbwc@gmail.com`).
- Bevat het adres geen `bwc`? → vraag opnieuw. Dit is bewust — alle BWC-werk-accounts hebben `bwc` in de naam.

Gebruik `{USER_EMAIL}` overal in de rest van deze skill waar het voorkomt.

---

## Doel
Maak complete, kant-en-klare social media content voor BWC Concepts evenementen — zodat de gebruiker alleen nog maar op "Posten" hoeft te klikken:
1. Analyseer live de laatste Instagram posts (nooit vertrouwen op opgeslagen voorbeelden)
2. Zoek passende foto's in Google Drive en download ze direct
3. Controleer of foto's al gepost zijn op Instagram
4. Sla foto's op in een overzichtelijke map met directe links voor Tim
5. Schrijf een originele caption die echt past bij het concept

---

## Werkwijze bij elke aanvraag

### Stap 1 — Begrijp de brief volledig

Zorg dat je het volgende weet voordat je begint (vraag door als iets ontbreekt):
- **Welk concept?** (Lizzy / Clear / Novia / Secret Lola / Luna / Lush / After 16 Hours)
- **Wat is de insteek?** (weekendrecap, sfeerimpressie, announcement, ticketpush, event dag, aftermovie)
- **Datum of event?** (indien relevant)
- **DJ's of artiesten?** (met Instagram-handles voor tagging)
- **Type post?** (feedpost, reel, story, carrousel)

---

### Stap 2 — Lees live de actuele Instagram posts

*Doe dit ALTIJD — vertrouw nooit op de opgeslagen voorbeelden hieronder. Die zijn een startpunt, maar de echte stijl lees je van de live feed.*

Ga naar de profielpagina van het account, haal de links op van de laatste 8-10 posts/reels, en lees elke caption. Zoek naar:
- Welke woorden en uitdrukkingen komen steeds terug?
- Hoe lang zijn captions? Hoeveel emojis?
- Hoe beginnen en eindigen posts?
- Welke sfeer en energie worden neergezet?
- Zijn er nieuwe slangwoorden of formats die niet in de voorbeelden hieronder staan?

| Concept | Instagram | URL |
|---------|-----------|-----|
| Lizzy op Donderdag | @lizzyopdonderdag | instagram.com/lizzyopdonderdag/ |
| Clear | @clear.nijmegen | instagram.com/clear.nijmegen/ |
| Club Novia | @clubnovia | instagram.com/clubnovia/ |
| Secret Lola | @secretlolaclub | instagram.com/secretlolaclub/ |
| That's What Luna Said | @thatswhatlunasaid | instagram.com/thatswhatlunasaid/ |
| Louder Than Lush | @louderthanlush | instagram.com/louderthanlush/ |
| After 16 Hours | @after16hours | instagram.com/after16hours/ |

---

### Stap 3 — Zoek passende foto's in Google Drive

Navigeer via Chrome naar Google Drive van **{USER_EMAIL}**:

**Pad naar de foto's:**
1. Ga naar `drive.google.com` (zorg dat je ingelogd bent als {USER_EMAIL})
2. Klik op **"Gedeeld met mij"** (Shared with me)
3. Open: **"BLOOM WITH COLOUR - Editie foto's"**
4. Navigeer naar **"[1] 2026"** voor de meest recente evenementfoto's

**Welke mappen gebruiken:**
- Gebruik **altijd** foto's uit mappen van 2025 of nieuwer
- De map `[1] 2026` bevat submappen per evenement (bijv. "Club Novia 21.03.2026", "That's What Luna Said 25.01.2026")
- 2025-materiaal staat direct in de root van "BLOOM WITH COLOUR - Editie foto's" (niet in een aparte map)
- Gebruik géén foto's uit oudere mappen

**Hoe zoeken:**
- Open relevante evenementmappen die passen bij het concept of de sfeer van de brief
- Bekijk de foto's en selecteer 4-6 opties die passen bij de brief
- Bij een weekendrecap: zoek in de mappen van het meest recente evenement van dat concept
- Let op de mapnamen — ze bevatten de conceptnaam en datum

**Richtlijnen per concept:**
- **Lizzy / Luna:** volle zalen, close-ups van knappe mensen, dansende mensen, gezelligheid, sfeerbeelden
- **Clear:** sfeervolle donkere beelden, DJ-shots, energieke dansende mensen, blauwe/koele sfeer
- **Novia / Secret Lola:** volle zalen, DJ-shots, knappe mensen, luxe sfeer; cocktails voor Lola
- **Lush / After 16 Hours:** energieke beelden, volle zalen, enthousiaste mensen

**Controleer op dubbelen:**
1. Ga terug naar het Instagram-account
2. Scroll door de **laatste 30 posts** en bekijk de gebruikte beelden
3. Vergelijk je geselecteerde foto's visueel met wat al gepost is
4. Als je twijfelt over een foto: zet een ⚠️ bij die foto en meld het aan Tim

---

### Stap 3b — Download de geselecteerde foto's

Het doel van deze stap: Tim hoeft niks meer op te zoeken of te downloaden — alles staat klaar. Doe dit altijd, ook als Tim er niet expliciet om heeft gevraagd.

**Hoe downloaden vanuit Google Drive via de browser:**
1. Open elke geselecteerde foto in Google Drive (klik erop zodat hij vergroot wordt weergegeven)
2. Klik op de drie puntjes (⋮) rechtsboven → kies **"Downloaden"**
3. De download start automatisch
4. Herhaal voor elke geselecteerde foto (doorgaans 4-6 stuks)

**Organiseer de downloads:**
- Maak een nieuwe map aan in de Cowork-werkmap met de naam:
  `[Concept] - [Datum] - Klaar om te posten`
  Voorbeeld: `Club Novia - 24.03.2026 - Klaar om te posten`
- Verplaats alle gedownloade foto's naar deze map
- Als een bestandsnaam onduidelijk is (bijv. `IMG_3847.jpg`), hernoem dan naar `foto-1.jpg`, `foto-2.jpg`, etc.
- Noteer voor elke foto welke caption-variant er het beste bij past

**Geef Tim directe links** naar elke foto via `computer://` links in Stap 5, zodat hij ze met één klik kan openen en uploaden naar Instagram.

---

### Stap 4 — Schrijf een originele caption

Gebruik de live-analyse uit Stap 2 als basis. Schrijf **nooit** een kopie of template.
Kopieer geen bestaande captions — gebruik ze uitsluitend als inspiratie voor toon, energie en ritme.

Schrijf **2-3 varianten:**
- Een korte versie (1-3 regels, voor story of minimalistische feed)
- Een middellange versie (4-7 regels, standaard feedpost)
- Een uitgebreide versie (voor announcements of speciale edities, als de brief dat vraagt)

Geef per variant aan:
- Of het meer geschikt is voor feed of story
- Welke geselecteerde foto('s) er het beste bij passen
- Of er DJ's of locaties getagd moeten worden

---

### Stap 5 — Presenteer het resultaat

Geef Tim een volledig kant-en-klaar overzicht — hij hoeft alleen nog maar te posten:

**📁 Foto's (gedownload en klaar)**
Geef voor elke foto een directe `computer://` link. Voorbeeld:
- [foto-1.jpg](computer:///sessions/trusting-affectionate-clarke/mnt/Claude%20Co-work/Club%20Novia%20-%2024.03.2026%20-%20Klaar%20om%20te%20posten/foto-1.jpg) ✅ — Past het beste bij variant B
- [foto-2.jpg](computer://...) ✅ — Goede alternatief voor variant A
- [foto-3.jpg](computer://...) ⚠️ — Vergelijkbaar met een eerder gepost beeld, controleer zelf

Geef ook de maplink zodat Tim alles in één keer kan openen.

**✍️ Caption-varianten**
Geef alle 2-3 opties, elk met een korte toelichting over geschiktheid (feed/story) en de beste fotokoppeling.

**📋 Checklist voor Tim — vóór het posten**
Maak een korte checklist op basis van de vaste regels voor dat concept:
- [ ] Likes uitzetten
- [ ] DJ's taggen: [handles invullen]
- [ ] Shared met Rolluik: ja / nee
- [ ] Fotograaf taggen: ja / nee
- [ ] Adverteren: ja / nee
- [ ] Pinnen: ja / nee
- [ ] Muziek toevoegen aan de post

---

## Concepten & Stijlgids

*Deze voorbeelden zijn een startpunt voor begrip. Lees altijd eerst de live feed (Stap 2) voor de actuele stijl.*

---

### 1. Lizzy op Donderdag
**Muziek:** Disco / Groovy House | **Locatie:** Rolluik Nijmegen (elke do) + reizend concept
**Doelgroep:** Studenten 18-24 | **Taal:** Nederlands

**Wat Lizzy Lizzy maakt:**
Schrijf alsof je een berichtje stuurt naar je beste vriendin. Warm, enthousiast, een beetje overdreven — en dat is precies goed. Lizzy-captions zijn nooit generiek. Ze zitten vol met herkenbare studentensituaties en een uitnodigende energie. De afsluiting is altijd "X" of "Xxx" — nooit meer, nooit minder.

**Herkenbare elementen:**
- Vet caps voor stadsnamen bij reizende edities: 𝐁𝐑𝐄𝐃𝐀, 𝐃𝐄𝐍 𝐇𝐀𝐀𝐆
- Woorden: "lieverds", "sjanssen", "losse heupjes", "knappe mensen", "vipers staan koud"
- Bewuste overdrijving: "heeel veel drankjes", "sjansennnn"
- Emojis: 🪩 😎 🙌🏼 🫦 💥 🌶️ 🧡 🔥

**Echte captions (gelezen van de live feed):**
```
Nog een paar uurtjes tot we weer lekker kunnen dansen en sjansennnn! 🪩😎🙌🏼
De vipers staan koud, tot vanavond! Xxx
```
```
𝐁𝐑𝐄𝐃𝐀 𝐀𝐑𝐄 𝐘𝐎𝐔 𝐑𝐄𝐀𝐃𝐃𝐃𝐘𝐘? 😎
Vanavond knappe mensen, losse heupjes en heeel veel drankjes in @clubbaronbreda! 🫦
Tot vanavond lieverds! X
```
```
𝐇𝐀𝐏𝐏𝐘 𝐁𝐃𝐀𝐘 𝐖𝐈𝐋𝐋𝐄𝐌 👑
De verjaardag van onze koning vieren we natuurlijk niet stilletjes...
Op Koningsnacht nemen we de Molenstraat over met Lizzy festival. 😎
Oranje fits aan, drankje in je hand en proosten op de verjaardag van de koning 🧡
Tot dan en dikke vette X
```

---

### 2. Clear
**Muziek:** Hardhouse, Trance & Eurodance | **Locatie:** Rolluik, laatste zaterdag van de maand
**Doelgroep:** Studenten 18-26 | **Taal:** Nederlands

**Wat Clear uniek maakt:**
Donker, mysterieus, poëtisch — geïnspireerd door Sub Cultuur stijl. Clear vertelt een verhaal in plaats van te schreeuwen. Langzame opbouw, ellipsen voor spanning, blauw thema. Weinig emojis, veel sfeer. Laat ruimte voor de verbeelding.

**Herkenbare elementen:**
- Aanspreekvorm: "Lieve nachtvrienden"
- Ellipsen (…) voor dramatisch effect
- Beeldend taalgebruik: "dampende club", "glijden door de nacht", "harde kick"
- Emojis spaarzaam: 💙 🌀 💨
- Cliffhangers: "Een debuut waarvan je niet wist dat je deze nodig had…"

**Echte captions:**
```
Lieve nachtvrienden! Een nieuwe stad… met een oude bekende!
RAMSES komt onze dampende club compleet nat maken.
We glijden door de nacht heen met heerlijke platen, blauwe cirkels en een harde kick.
Een debuut waarvan je niet wist dat je deze nodig had…
Drop 'm in je agenda, deze mis je niet.
```
```
Clear gaat een uitstapje maken…. 04.04.26
Ready? 💙
```
```
Maandag. We zijn nog niet helemaal geland…
We blikken terug, maar blijven nooit te lang hangen.
Want daar, net om de hoek, ligt alweer de volgende te wachten 💨💨
Regel je plek.
```

---

### 3. Club Novia
**Muziek:** House | **Locatie:** Club Novia, Molenstraat Nijmegen
**Doelgroep:** 21+ | **Taal:** Engels (ALTIJD — ook al zijn alle bezoekers Nederlands)

**Wat Novia uniek maakt:**
Minder is meer. Novia hoeft niet hard te praten — de kwaliteit spreekt voor zich. Kort, luxe, zelfverzekerd. Sluit af met "Cheers, X Novia" of gewoon "❤️". Tag de fotograaf.

**Herkenbare elementen:**
- Kan heel kort zijn: "Novia in March. ❤️" is een complete, perfecte post
- Emojis spaarzaam: ❤️ 🔥 🙌
- Fotograaf taggen: "📽️ @photographer & Tim"
- "Cheers, X Novia" of "❤️" als afsluiting

**Echte captions:**
```
Novia in March. ❤️
```
```
Closed the weekend the right way with @nigel.tn & @robstillekens.
Enjoy your Sunday and see you next weekend at your beloved Club Novia ❤️
Cheers, X Novia
📽️ @jort.graph & Tim
```

---

### 4. Secret Lola
**Muziek:** House | **Locatie:** Club Novia, elke vrijdag
**Doelgroep:** 23+, luxe | **Taal:** Engels (ALTIJD)

**Wat Secret Lola uniek maakt:**
Minimalistisch tot op het bot. Luxueus, sexy, zelfverzekerd. Een artiest beschrijf je niet met hype, maar met elegantie. Sluit altijd af met "See you at Secret Lola. ❤️".

**Herkenbare elementen:**
- Vaste sluiting: "See you at Secret Lola. ❤️"
- Minimalistisch: "March at Secret Lola." is een volledige, correcte caption
- Artiest beschrijving verfijnd: "known for his refined taste and feel for the floor"
- Weinig tot geen emojis

**Echte captions:**
```
March at Secret Lola.
```
```
On April 10th, @armas.dj hosts his own night at Secret Lola.
Known for his refined taste and feel for the floor, he takes charge of the night
with a sound that moves effortlessly from start till late.
Alongside him: @gfreaxx @giovanna.music_ @_oliverdj @alxsofficial

See you at Secret Lola. ❤️
```

---

### 5. That's What Luna Said
**Muziek:** Urban & Nostalgic Anthems | **Locatie:** Rolluik, 3e donderdag van de maand
**Doelgroep:** 18+ | **Taal:** Nederlands (soms een enkel Engels woord)

**Wat Luna uniek maakt:**
Energetisch, FOMO-gedreven, maar ook met een gevoel van saamhorigheid en nostalgie.
Luna-captions gaan over de belofte van een avond vol nummers die je "woord voor woord kent". 🫦 is de signature emoji — zonder die emoji is het geen Luna-post.

**Herkenbare elementen:**
- Signature emoji: 🫦 (altijd aanwezig)
- Vetgedrukte caps voor hype: 𝐍𝐈𝐉𝐌𝐄𝐆𝐄𝐍, 𝐌𝐀𝐀𝐊 𝐉𝐄 𝐊𝐋𝐀𝐀𝐑.
- Woorden: "meezingen zonder schaamte", "heupen los", "tunes die je woord voor woord kent"
- FOMO-sluitingen: "Dit wil je niet missen.", "Zorg dat je erbij bent…"
- Datum als slotakkoord: "04.04.2026 see you there." of eenvoudiger "xx"

**Echte captions:**
```
𝐍𝐈𝐉𝐌𝐄𝐆𝐄𝐍, 𝐌𝐀𝐀𝐊 𝐉𝐄 𝐊𝐋𝐀𝐀𝐑. 𝐖𝐄 𝐆𝐀𝐀𝐍 𝐄𝐑 𝐇𝐀𝐑𝐃 𝐓𝐄𝐆𝐄𝐍𝐀𝐀𝐍. 🫦
Een nacht met de tunes die je woord voor woord kent, heupen los en meezingen zonder schaamte.
Zorg dat je erbij bent… Dit wil je niet missen. 💕
04.04.2026
```
```
MISSED US? 🫦
21 maart: blok 'm alvast, want dit wordt een nacht om niet te vergeten.
Zelfde energie, nieuwe herinneringen.
Zie ik je in @club_circle? 💕
```
```
Zondag = nagenieten. 🫦
Gister was weer precies wat het moest zijn.
Te veel meegezongen, te laat naar huis en nul spijt.
Tot de volgende xx
```
```
HET IS BIJNA ZOVER! 🫦
Morgen is het geen voorpret meer. Geen plannen meer. Geen 'we zien wel'.
Morgen is het showtime ;)
```
```
Woensdagmodus: aftellen… ⏳
Zaterdagmodus: losgaan zonder rem! 🫦
```

---

### 6. Louder Than Lush
**Muziek:** Nostalgic hits | **Locatie:** Rolluik
**Doelgroep:** Studenten 18-24 | **Taal:** Mix Nederlands en Engels (bewust door elkaar)

**Wat Lush uniek maakt:**
Warm, girly, intiem — alsof je je beste vriendinnen een berichtje stuurt. De vaste catchphrase "louder than your memories" hoort erbij. Sluit altijd af met "XX" (twee hoofdletters). Roze emojis domineren.

**Herkenbare elementen:**
- Vaste sluiting: "XX"
- Catchphrase: "louder than your memories"
- Woorden: "liefjes", "same sound, same vibe", "Lush season", "Round 2 is loading"
- Emojis: 🩷 💕 🩵 💋 ✨ 🥰 😍 👀 ☁️
- Mix Nederlands/Engels is gewenst, niet een fout

**Echte captions:**
```
Lush season isn't over yet 👀
10/04 zijn we terug 💋 Same sound, same vibe 🫦
Tot snel liefjes XX
```
```
Beloofd is beloofd 👀
De tweede editie van Lush 😍 Na een eerste, volle club avond met de knapste
en gezelligste mensen zijn wij ready voor part two 🥰
Vrijdag 10 april is Lush, once again, louder than your memories 🩷
Be there!! ✨ See you soon 🩵 XX
```
```
Jullie geduld wordt bijna beloond 👀
Vanavond gaan we even terug naar toen ✨
De nummers die je nooit bent vergeten ☁️
The friends you came with, the memories you'll leave with 💘
Lush starts tonight 😍
```
```
It's a wrap!! 😍 De eerste editie van Lush 🩵
But we're far from done 😉 We might be back sooner than you think.. ✨
Stay tuned XX
```

---

### 7. After 16 Hours
**Muziek:** Divers | **Locaties:** Multiple steden (Arnhem, Nijmegen, Enschede — groeiend)
**Taal:** Nederlands

**Wat After 16 Hours uniek maakt:**
Hype, urgentie, schaarste. Tickets zijn het onderwerp — zorg dat mensen het gevoel hebben dat ze nu moeten handelen anders missen ze de boot. Vetgedrukte caps voor stad en titel.

**Herkenbare elementen:**
- Vetgedrukte Unicode-caps voor steden: 𝗔𝗥𝗡𝗛𝗘𝗠, 𝗡𝗜𝗝𝗠𝗘𝗚𝗘𝗡
- SOLD OUT communicatie: 𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 = 𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 💥
- Emojis: 🔥 💥 👀 💨 🎟️ ✨
- Urgentiewoorden: "dit wil je niet missen", "wacht niet te lang", "be readyyy"
- Ellipsen voor spanning: "en dat ging snel… 👀"

**Echte captions:**
```
𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 = 𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 💥
De early birds voor Nijmegen & Arnhem zijn officieel uitverkocht… en dat ging snel. 👀
Maar geen stress. De volgende tickets zijn nu live.
Wil je erbij zijn? Dan is dit je moment.
Wacht niet te lang… je ziet wat er gebeurt. 💨🎟️
```
```
𝗗𝗜𝗧 𝗚𝗔𝗔𝗧 𝗦𝗡𝗘𝗟… 💨
De early birds voor Nijmegen & Arnhem zijn bijna uitverkocht.
En geloof ons… dit wil je niet missen.
Fix je ticket nu het nog kan 👀✨🎟️
Link in bio
```
```
𝗘𝗡𝗦𝗖𝗛𝗘𝗗𝗘… 𝗭𝗜𝗝𝗡 𝗝𝗨𝗟𝗟𝗜𝗘 𝗞𝗟𝗔𝗔𝗥? 🔥
Zet 'm alvast in je agenda, want dit wil je niet missen!
Be readyyy! 🎟️
```

---

## Google Drive — Mapstructuur

**Pad:** Gedeeld met mij → BLOOM WITH COLOUR - Editie foto's

```
BLOOM WITH COLOUR - Editie foto's/
├── [1] 2026/                          ← Gebruik dit voor meest actuele foto's
│   ├── Club Novia 21.03.2026/
│   ├── Club Novia 20.03.2026/
│   ├── Club Novia 30.01.2026/
│   ├── Club Novia 25.01.2026/
│   ├── That's What Luna Said 25.01.2026/
│   ├── One Night In The Theatre 09.03.2026/
│   └── DJEFFERSON & friends presskit/
├── LOD Kerstspecial 27.12.25/         ← 2025 materiaal staat in de root
├── That's What Luna Said 27-12-25/
├── LOD Tilburg + Tobias Camman 5.12.2025/
├── Club Novia - Capron 6.12.2025/
├── BWC socials foto's/
└── ... (meer 2025 mappen in de root)
```

**Navigatiestrategie:**
1. Zoek eerst in `[1] 2026` — meest actueel
2. Als dat niet genoeg relevante foto's oplevert: zoek in 2025-mappen in de root (herkenbaar aan datum in mapnaam, bijv. "27.12.25")
3. Gebruik NOOIT mappen zonder duidelijke datum als ze ouder lijken dan 2025

---

## Contentplanning per concept

*Gebaseerd op diepte-analyse van alle 7 BWC Instagram-accounts (januari–maart 2026). Alle posts handmatig geanalyseerd. Gebruik dit als vaste basis bij weekplanningen en caption-schrijven.*

---

### Lizzy op Donderdag — 2-3x per week
**Signature emojis:** 🫦 😎 🔥 🪩 💥 🌸 | **Taal:** Nederlands | **Sluiting:** altijd "X" of "Xxx"
**Content mix:** 60% carrousel, 40% reel | **Geen hashtags** — alleen @venue en @artist tags

**Wekelijks patroon (Nijmegen donderdag als basis):**

| Dag | Feed | Timing | Formule |
|-----|------|--------|---------|
| Ma | Recap vorig weekend + teaser deze week (carrousel) | 09:00 | "Goeeedemorgen sunshine's 🌞 / [recap] / Tot [dag]! X" |
| Wo | Hype buildup richting donderdag (carrousel of reel) | 20:00 | "Nog een paar uurtjes... / [sfeer] / Tot vanavond lieverds! X" |
| Do | Same-day hype of externe stad aankondiging | 17:00 | "[STAD] ARE YOU READYYY? 😎 / [sfeer + venue] / Be there X" |
| Vr/Za | Externe stad event (indien van toepassing) | — | Reel met CAPS stadsnaam |
| Zo | Weekend reflectie + preview volgende week | 12:00 | "Fijn weekend lieve mensen! 🌸 / [terugblik] / Donderdag again X" |

**Externe steden formule (3-7 dagen vooruit):**
- Opener: "[𝐒𝐓𝐀𝐃] ARE YOU READYYY? 😎" (vetgedrukte Unicode caps)
- Body: "Vanavond knappe mensen, losse heupjes en heeel veel drankjes in @[venue]! 🫦"
- Sluiting: "Tot vanavond lieverds! X" of "Be there X"
- Tag altijd: @venue + @dj handles

**Terugkerende woorden:** "lieverds", "sjanssen", "losse heupjes", "knappe mensen", "dikke house platen", "zweterige dansvloeren", "heeel veel drankjes", "vipers staan koud"

**Vaste getagde venues:** @rolluiknijmegen, @clubbaronbreda, @club_circle, @clubpoema, @joli.denhaag

---

### Clear — gemiddeld 2,5x per week (maandelijks event, laatste zaterdag)
**Signature emojis:** 💙 🌀 💨 🩵 | **Taal:** Mix Nederlands/Engels, poëtisch | **Geen hashtags**
**Content mix:** 80% carrousel, 15% reel, 5% foto | **Caption lengte:** 50-150 woorden

**Maandelijkse crescendo (10-daagse opbouw per event):**

| Timing | Type | Formule |
|--------|------|---------|
| -10 dagen | Carrousel | DJ announcement + general teaser |
| -8 dagen | Carrousel | "De eerste namen zijn daar 👀💙 [genres] komen samen op één vloer. Dit is nog maar het begin…" |
| -7 dagen | Carrousel | Setting/venue beschrijving: "Dit is de setting. Licht. Energie. Beweging." |
| -5 dagen | Carrousel | Complete lineup: "[Namen]. Een line-up die geen pauze kent. [Genre] op volle kracht. 🌀" |
| -3 dagen | Carrousel | Poëtische buildup: "De opbouw… de spanning… Je voelt het al in de zaal voordat het gebeurt." |
| -1 dag | Reel (video) | Urgentie: "Morgen gebeurt het 🩵 Early birds? Gone… Dit is je laatste kans 💨" |
| Event dag | Carrousel | "Vanavond komt alles samen… Zorg dat je op tijd bent. Tot straks 💙" (post om ~20:00) |
| +1 dag | Carrousel | Korte recap: "Wauw. Dankjewel [stad] 💙" |
| +2 dagen (ma) | Carrousel | Reflectie + volgende event teaser: "Maandag. We zijn nog niet helemaal geland… 💨💨 Want daar, net om de hoek, ligt alweer de volgende te wachten." |

**DJ profiel formule (150-250 woorden):**
- Opening: "Sommige DJ's draaien platen, @[dj] bouwt momenten 💙"
- Achtergrond: origine, sound, specifieke genres
- Energie: "Pure energie, euforische pieken"
- Contrast: "Geen standaard set, maar een [unieke omschrijving]"
- CTA: "Laatste [X] early birds nu in de shop! Link in bio."

**Terugkerende zinnen:** "De spanning hangt al tussen de muren", "tickets vliegen", "dit is je laatste kans", "bouwt momenten", "glijden door de nacht", "harde kick", "lieve nachtvrienden"

---

### Club Novia — ~1x per week
**Signature emoji:** ❤️ ❣️ 🔥 🛫 | **Taal:** Engels (ALTIJD) | **Sluiting:** "X Novia" of "Cheers, X Novia"
**Content mix:** 75% carrousel, 25% reel | **Captions:** zeer kort (3-54 woorden)

| Dag | Type | Formule |
|-----|------|---------|
| Ma/Di | Lineup aankondiging (carrousel) | "On [datum], @dj hosts his own night at Club Novia. Along side him: @[guests]. [Genre] behind the Novia decks all night long." |
| Do/Vr | Weekend hype (carrousel of reel) | "Weekend mood: ON. 🔥 See you at Club Novia this weekend." of live clip: "02:30 live with @dj 🛫" |
| Zo na event | Recap (carrousel) | "Closed the weekend the right way with @dj1 & @dj2. Enjoy your Sunday and see you next weekend at your beloved Club Novia ❤️ / Cheers, X Novia" |
| Begin maand | Maandelijkse identity post | "Novia in [Month]. ❤️" (met fotograaf credit: "📽️ @jort.graph & Tim") |

**Vaste formules:**
- Recap: "Closed the weekend the right way with @dj. … see you next weekend at your beloved Club Novia ❤️ Cheers, X Novia 📽️ @photographer & Tim"
- Maandpost: "Novia in [Month]. ❤️" — dit is een complete, perfecte caption
- Live moment: "[tijd] live with @dj [emoji]"

---

### Secret Lola — 2x per week (elke vrijdag)
**Vaste sluiting:** "See you at Secret Lola. ❤️" | **Taal:** Engels (ALTIJD) | **Stijl:** minimalistisch, luxe
**Content mix:** 90% carrousel, 10% reel | **Captions:** 2 types (zie onder)

**Twee caption-types — gebruik altijd één van deze twee:**

**Type 1 — DJ Host Night aankondiging (150-250 woorden, 1-2 weken vooruit):**
```
On [datum], @dj hosts his own night at Secret Lola.
[Elegante persoonsbeschrijving — 2-3 zinnen over sound en stijl].
[Eventueel: speciale sfeer of verwachting].
Alongside him: @guest1 @guest2 @guest3

See you at Secret Lola. ❤️
```

**Type 2 — Korte teaser of recap (10-30 woorden):**
```
The weekend starts right here. Tonight, we dance at Secret Lola. See you soon. ❤️
```
```
Still thinking about last weekend. See you next Friday at Secret Lola's. ❤️
```
```
March at Secret Lola.
```

**Weekpatroon (vrijdag als eventdag):**

| Dag | Post | Formule |
|-----|------|---------|
| Di | DJ host night aankondiging (1-2 weken vooruit) | Type 1 formule |
| Do | Weekend teaser | "The weekend starts right here. Tonight, we dance at Secret Lola. ❤️" |
| Za/Zo | Recap of volgende week teaser | "Still thinking about last weekend. See you next Friday ❤️" |

**Terugkerende beschrijvingstaal:** "refined taste and feel for the floor", "a sound that moves effortlessly from start till late", "known for his [eigenschap]", "hosts his very own night", "get ready to dance the night away with the finest house music"

---

### That's What Luna Said — 2-3x per week (3e donderdag van de maand)
**Signature emoji:** 🫦 (aanwezig in ~90% van posts) + 💋 🌹 ❤️ | **Taal:** Nederlands | **Sluiting:** "xx" of "xxx"
**Content mix:** 80% carrousel, 15% reel, 5% foto | **Stijl:** flirty, speels, dubbele betekenissen

**Maandelijkse opbouw (event = 3e donderdag):**

| Timing | Dag | Formule |
|--------|-----|---------|
| -14 dagen | Vrijdag | "Fijn weekend lieverdsss💋 [datum] zorg dat je ready bent!" |
| -10 dagen | Maandag | "Hoe was je weekend? Maak je alvast klaar voor [datum]…🌹 Wie zien we daar?••" |
| -7 dagen | Maandag | "WE ARE BACK 💋 [datum] blok 'm alvast, want dit wordt er eentje voor in de boeken… Meezingen zonder schaamte, dansen zonder rem…" |
| -5 dagen | Woensdag | "Hee lieverds, [datum] belooft een avond te worden die je wilt meemaken.🌹 Zien we je?" |
| -2 dagen | Donderdag | "Hebben jullie je outfit al klaargezet voor [dag]? ❤️ [datum] BE READY xx" |
| -1 dag | Vrijdag | "MORGEN. IS. HET. ZOVER. 🔥 Ben jij er klaar voor… of ben jij er écht KLAAR VOOR?! xxx" |
| Event dag | Zaterdag | "Zaterdagavond: goede plannen en slechte keuzes. Wie zien we vanavond?💋" |
| +1 dag | Zondag | "Zondag = nagenieten. 🫦 Gister was weer precies wat het moest zijn. Te veel meegezongen, te laat naar huis en nul spijt. Tot de volgende xx" |
| +2 dagen | Maandag | "Maandag = nagenieten met een lichte kater. 🫦 Geen stem, geen spijt. Wie voelt 'm ook?" |
| Tussenweeks | Woensdag | "Woensdagmodus: aftellen… 🫦 Zaterdagmodus: losgaan zonder rem! 💋" |

**Vaste caption-openers:** "NIJMEGEN, MAAK JE KLAAR.", "WE ARE BACK 💋", "MORGEN. IS. HET. ZOVER. 🔥", "Hee lieverds,", "Fijn weekend lieverdsss"
**Terugkerende woorden:** "lieverdsss", "slechte keuzes", "meezingen zonder schaamte", "losgaan", "nagenieten", "brakjes", "goede energie", "Be ready"

---

### Louder Than Lush — dagelijks pre-launch, 1-2x/week post-launch
**Vaste sluiting:** "XX" (twee hoofdletters, altijd) | **Taal:** Mix Nederlands/Engels (bewust door elkaar)
**Content mix:** 70% foto, 15% reel, 15% carrousel | **Stijl:** girly, nostalgisch, "main character energy"

**Lancerings- en eventcyclus:**

| Fase | Timing | Formule |
|------|--------|---------|
| Teaser fase | 3-4 weken voor | "Something Lush is coming 🌸 / No skips, just hits / Save the date, trust us! 🌟" |
| Countdown | Dagelijks -14 tot -2 | "[X] daagjes!! / XX" of "Nog héél even 😍 / [X] more days, let's count down together 💙 / XX" |
| Reveal | -10 dagen | Reel: "[STAD], listen up! This one's louder than your memories 🌸 / Lush neemt de nacht over met club music… / Dress cute. Lose your voice. See you when the lights go low. 💙" |
| Lineup | -4 dagen | Carrousel: "De Club Lush Line-Up! 🥰✨☁️🩷 / Nog maar [X] nachtjes slapen 😇 / XX" |
| Finale hype | -1 dag | "Morgen is het zo ver 👀 / De eerste/volgende nacht van Lush 💙 / Deze wil je niet missen!! / XX" |
| Event dag | Dag zelf | "Jullie geduld wordt bijna beloond 💋 / Vanavond gaan we even terug naar toen ✨ / Lush starts tonight 😍" |
| Wrap-up | +1 dag | "It's a wrap!! 😍 De [x]e editie van Lush 💙 / But we're far from done 😉 / Stay tuned XX" |
| Tease vol. 2 | +2 weken | "Lush season isn't over yet 🔥 / [datum] zijn we terug 💋 / Same sound, same vibe 💋 / XX" of "Round 2 is loading 👀 / Same energy, new edition 💋✨ / [datum] / XX" |

**Signature teksten:** "louder than your memories", "Dress cute. Lose your voice.", "white girl anthems", "throwbacks only, regrets later", "The friends you came with, the memories you'll leave with"
**Signature emojis:** 💙 🩷 🌸 ✨ ☁️ 😍 👀 💋 XX

---

### After 16 Hours — 1-2x per week normaal, burst van 3-4x/week bij ticketlaunches
**Signature emojis:** 💨 🎟️ 🔥 👀 ✨ ❤️‍🔥 | **Taal:** Nederlands | **Stijl:** direct, urgent, CAPS-heavy
**Content mix:** ~100% carrousel | **Steden:** Nijmegen (meest), Arnhem, Enschede

**Terugkerende post-types:**

| Type | Formule |
|------|---------|
| Alle datums reveal | "𝗛𝗘𝗧 𝗔𝗙𝗧𝗘𝗟𝗟𝗘𝗡 𝗞𝗔𝗡 𝗕𝗘𝗚𝗜𝗡𝗡𝗘𝗡! Alle datums staan online! Waar ga jij heen? 😚 [Stad] opgelet! [Dag] om [tijd] gaat de ticketsale live! 🎟️" |
| Ticketsale launch | "𝗙𝗜𝗝𝗡 𝗪𝗘𝗘𝗞𝗘𝗡𝗗 𝗚𝗘𝗛𝗔𝗗? De ticketsale van [𝗦𝗧𝗔𝗗] is gestart en gaat hard! 💨 [Volgende stad] om [dag+tijd] gaan de tickets voor [stad] online!" |
| Urgentie / bijna uitverkocht | "𝗗𝗜𝗧 𝗚𝗔𝗔𝗧 𝗦𝗡𝗘𝗟… 💨 De early birds voor [stad] zijn bijna uitverkocht. En geloof ons… dit wil je niet missen. Fix je ticket nu het nog kan 👀✨🎟️ Link in bio" |
| Sold out | "𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 = 𝗦𝗢𝗟𝗗 𝗢𝗨𝗧 💥 De early birds voor [stad] zijn officieel uitverkocht… en dat ging snel. 👀 Maar geen stress. De volgende tickets zijn nu live." |
| Pre-event hype | "DOE EEN F*CKING POSE VOOR ME! Nog [X] uurtjes en we gaan met meer dan [X] knappe mensen [STAD] omver blazen 😮‍💨" |
| Event recap | "𝗪𝗔𝗧 𝗘𝗘𝗡 𝗔𝗩𝗢𝗡𝗗 ❤️‍🔥 Afgelopen [dag] was écht alles… jullie energie, die dansmoves, de sfeer 💋 Wij hebben genoten!" |
| Datum wijziging | "⚠️ 𝗗𝗔𝗧𝗨𝗠 𝗪𝗜𝗝𝗭𝗜𝗚𝗜𝗡𝗚! [Event naam] zal plaatsvinden op [nieuwe datum]. De kaartverkoop start [dag] om [tijd] uur! ❤️" |
| Weekend vibes | "Het is weer weekenddd ❤️‍🔥 En we hebben de beste After Hours [muziek] voor jullie klaargezet… Welke zet jij als eerste aan?" |

**Multi-city staggered launch patroon:**
1. Arnhem eerste (meest gevestigd)
2. Nijmegen tweede (~2 dagen later)
3. Enschede derde (~4 dagen later)
4. Gecombineerde posts voor finale push (alle 3 steden samen)

**Caps format voor steden:** 𝗔𝗥𝗡𝗛𝗘𝗠, 𝗡𝗜𝗝𝗠𝗘𝗚𝗘𝗡, 𝗘𝗡𝗦𝗖𝗛𝗘𝗗𝗘
**Vaste partners:** @driekleinezusjes / @driegezusters (partner event), @club_circle (Arnhem), @aspenvalleyenschede (Enschede)

---

## Frequentie & Format overzicht

| Concept | Posts/week | Primair format | Caption lengte | Taal |
|---------|-----------|----------------|----------------|------|
| Lizzy | 2-3 | Carrousel + reel | Kort (2-5 regels) | NL |
| Clear | 2-3 | Carrousel | Middel-lang (50-150 woorden) | NL/EN mix |
| Club Novia | ~1 | Carrousel | Zeer kort (3-54 woorden) | EN |
| Secret Lola | 2 | Carrousel | Lang (DJ) of zeer kort (teaser) | EN |
| Luna | 2-3 | Carrousel | Kort-middel (3-8 regels) | NL |
| Lush | Dagelijks pre-launch, 1-2 daarna | Foto | Kort (2-5 regels) | NL/EN mix |
| After 16 Hours | 1-2 (burst bij launch) | Carrousel | Direct (3-6 regels) | NL |

---

## Vaste regels voor alle accounts
- **Likes staan altijd uit** bij alle BWC posts
- **Shared met Rolluik** bij Lizzy en Clear posts
- **Tag altijd alle DJ's** die die avond draaien (zodat zij kunnen reposten)
- **Fotograaf taggen** bij Novia posts: "📽️ @photographer"
- **Voeg altijd een passend nummer toe** aan de post
- **Pin announcements** in de feed (Lizzy, Clear)
- **Adverteer announcements** (Lizzy, Clear, After 16 Hours)
- Voor **Secret Lola announcements**: shared met Novia + Novia-logo op de post
- **Controleer of foto al eerder gepost is** — altijd vermelden aan Tim

---

## Kaya Club — Bonus concept
**Muziek:** Urban / R&B | **Locatie:** Club Circle, Arnhem
**Doelgroep:** Studenten 18-24 | **Taal:** Nederlands
**Tone of voice:** Identiek aan Lizzy — studentikoos, informeel, warm
**Kleuren:** Paars, roze, groen (neon)
