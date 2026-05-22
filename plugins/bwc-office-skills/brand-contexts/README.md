# Brand Contexts

> Centrale opslag voor alle brand-context bestanden gegenereerd door de `brand-mapper` skill.

## Wat staat hier

Per nachtzaak of concept één markdown-bestand met de volledige brand-mapping:

- Tone of voice
- Voorbeeldcaptions
- Visuele identity
- Drive-pad en mapnaming
- Vaste regels voor posten
- Frequentie en formules

Bestandsnaamconventie: `brand-context-[slug].md`

Voorbeelden:
- `brand-context-aspen-valley-arnhem.md`
- `brand-context-fifth-avenue.md`
- `brand-context-lizzy-op-donderdag.md`

## Hoe werkt het

**Schrijven (door `brand-mapper` skill):**
1. Skill schrijft eerst naar de lokale werkmap: `~/Desktop/Claude Co-work/brand-contexts/`
2. Aan het einde van een run vraagt de skill of het bestand gedeeld moet worden met het team
3. Bij ja: skill kopieert het bestand naar deze folder en commit + pusht naar GitHub
4. Updates komen automatisch binnen bij iedereen die de marketplace heeft geinstalleerd

**Lezen (door `social-media-poster` skill):**
1. Skill zoekt eerst in `~/Desktop/Claude Co-work/brand-contexts/` (lokaal, meest recent)
2. Vindt 'ie daar niets, dan kijkt 'ie hier (deze folder, marketplace-shared)
3. Bestaat het ook hier niet: skill vraagt om eerst `brand-mapper` te draaien

## Onderhoud

- Bestanden hier worden door het team gebruikt. Pas niet zomaar aan zonder overleg.
- Voor structurele wijzigingen: draai brand-mapper opnieuw voor die zaak (versie-suffix `-v2`).
- Houd bestandsnaam consistent met de slug die je in social-media-poster gebruikt.
