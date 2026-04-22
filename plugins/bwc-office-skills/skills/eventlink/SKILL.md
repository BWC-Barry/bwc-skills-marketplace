---
name: eventlink
description: >
  BWC Concepts Eventlink skill — maakt automatisch ticketlinks en/of gastenlijstlinks aan in Weeztix en voegt ze toe aan het Google Doc "Ticketlinks BWC". Gebruik deze skill wanneer Tim vraagt om een ticketlink of gastenlijstlink aan te maken voor een event, wanneer hij zegt "maak een link aan voor [event]", "voeg [event] toe aan Weeztix", of "update Ticketlinks BWC voor [event]". Activeer ook proactief als Tim een eventnaam en datum noemt in combinatie met een venue (Club Novia, Rolluik, etc.). Werk altijd stap voor stap via de browser.
---

# BWC Eventlink Skill

Je maakt ticketlinks en/of gastenlijstlinks aan in Weeztix en zet ze daarna in het Google Doc "Ticketlinks BWC".

---

## 🔧 Eerste keer? Even jezelf instellen

Deze skill is voor het hele BWC-team. Bij de eerste run bij een nieuwe gebruiker, vraag en onthoud deze waarde voor de rest van de sessie:

**BWC-e-mailadres (`{USER_EMAIL}`)** — **verplicht met `bwc` in de naam**.

- Vraag: "Wat is jouw BWC-e-mailadres voor Google Drive / Gmail?"
- Valideer: het adres MOET de letters `bwc` bevatten (bijv. `kelvinbwc@gmail.com`, `ninabwc@gmail.com`, `timpoelmansbwc@gmail.com`).
- Bevat het adres geen `bwc`? → vraag opnieuw. Dit is bewust — alle BWC-werk-accounts hebben `bwc` in de naam.

Gebruik `{USER_EMAIL}` overal in de rest van deze skill waar het voorkomt.

---

## Wat je nodig hebt van Tim (vraag dit vooraf als het nog niet gegeven is)

1. **Eventnaam** — zoals hij in Weeztix en het document komt te staan (Tim geeft dit altijd zelf aan)
2. **Datum** — dag, datum, maand en jaar van het event
3. **Venue** — welke locatie (bepaalt in welke Weeztix-account je werkt)
4. **Type link(s)** — gastenlijst, ticketlink, of beide

Als een van deze punten ontbreekt, vraag het dan vóórdat je begint.

---

## Stap 0: Controleer het Google-account in de browser

Navigeer naar `https://myaccount.google.com` en controleer of je bent ingelogd als **{USER_EMAIL}**. Zo niet, switch eerst naar dat account via `https://accounts.google.com/AccountChooser?Email={USER_EMAIL}`.

---

## Stap 1: Open Weeztix en kies de juiste account

Ga naar `https://app.weeztix.com`. Je komt in het dashboard.

Klik rechtsboven op de account-naam om van account te wisselen. Kies de juiste op basis van de venue:

| Venue | Weeztix account |
|---|---|
| Club Novia (Nijmegen) | **Club Novia x BWC** |
| Rolluik (Nijmegen) — Lizzy, Clear, Lush, Luna | **Rolluik x BWC** |
| Club Circle (Arnhem) — Kaya | **Club Circle** |
| Lizzy buiten Nijmegen (Den Haag, Utrecht, etc.) | **Bloom with Colour concepts** |
| After Hours (Drie gezusters) | **Drie gezusters x BWC** |

> **Let op:** Momenteel heeft Tim alleen bewerkingsrechten voor **Club Novia x BWC**. Voor andere accounts zal hij eerst toestemming moeten vragen aan zijn baas. Meld dit als de gevraagde venue niet Club Novia is.

---

## Stap 2: Maak een nieuw evenement aan

1. Klik op **"+ Maak nieuw evenement"**
2. Kies **Standaard** als event type
3. Vul de eventgegevens in:
   - **Eventnaam:** precies zoals Tim het heeft opgegeven
   - **Locatie:** de juiste venue (bijv. "Club Novia")
   - **Start evenement:** datum van het event om **23:00**
   - **Einde evenement:** volgende dag om **05:00**
   - **Capaciteit:** Ongelimiteerd
   - Alle overige velden: leeg laten
4. Klik **Opslaan**

---

## Stap 3: Voeg het tickettype toe

Je komt nu in het ticket-configuratiescherm.

### Voor een GASTENLIJST:
- **Naam:** `Guestlist (entrance before 00:30)`
- **Ticketcapaciteit:** Ongelimiteerd (tenzij Tim anders aangeeft)
- **Type:** Gastenlijst
- **Beschikbaar vanaf:** huidige datum en tijdstip (nu)
- **Beschikbaar tot:** dag van het event om **23:00**
- Klik op het volgende scherm: zet **"Publiek beschikbaar" UIT**
- Klik **Opslaan**

### Voor een TICKETLINK (betaald):
- **Naam:** zoals door Tim opgegeven (bijv. "Early Bird", "Regular", etc.) — vraag dit als het niet duidelijk is
- **Prijs:** zoals door Tim opgegeven
- **Ticketcapaciteit:** Ongelimiteerd (tenzij anders aangegeven)
- **Beschikbaar vanaf:** nu
- **Beschikbaar tot:** dag van het event om **23:00**
- Klik **Opslaan**

---

## Stap 4: Maak de Shop aan (dit genereert de deelbare link)

1. Ga naar het **"Shops"** scherm
2. Klik op **"New shop"**
3. Vul de shopnaam in volgens dit formaat:
   - Voor gastenlijst: `Gastenlijst [eventnaam] [datum als DD.MM.YYYY]`
   - Voorbeeld: `Gastenlijst Secret Lola presents Gino le Noir & Friends 27.03.2026`
   - Voor ticketlink: `Tickets [eventnaam] [datum als DD.MM.YYYY]`
4. Laat de **beschrijving leeg**
5. Klik op **"Tickets"** (onder de beschrijving)
6. Kies het juiste tickettype door op **"Kies"** te klikken (bijv. "Guestlist (entrance before 00:30)")
7. Klik op **"Toepassen"**
8. Terug in het shopscherm: klik **Opslaan**
9. Klik nog een keer **Opslaan** in het shopoverzicht

---

## Stap 5: Kopieer de link

Na het opslaan verschijnt de deelbare shop-link (formaat: `https://weeztix.shop/[code]`). Kopieer deze link.

Als er zowel een gastenlijst- als een ticketlink gemaakt moet worden, herhaal dan stap 3 en 4 voor elk type en kopieer beide links.

---

## Stap 6: Update het Google Doc "Ticketlinks BWC"

1. Open het document via Google Drive (account: {USER_EMAIL}):
   - URL: `https://docs.google.com/document/d/1xzblT-6OmZukkpVfv8rOtDhr6Ufs0hei/edit`
2. Zoek de juiste plek in het document op basis van de maand en het weeknummer
3. Voeg het event toe in dit formaat:

```
[Dag] [Datum] [Maand] [Jaar]: [Eventnaam]
    - GASTENLIJST: [weeztix.shop/link]
    - TICKETLINK: [weeztix.shop/link]   ← alleen als van toepassing
```

Zorg dat de opmaak overeenkomt met de rest van het document (vetgedrukte eventnaam, bullet-indentatie voor de links).

4. Sla het document op (Ctrl+S of automatisch opgeslagen door Google Docs)

---

## Stap 7: Bevestig aan Tim

Geef een korte samenvatting:
- Welk event is aangemaakt
- Welke link(s) zijn gegenereerd (kopieer ze ook letterlijk in je antwoord)
- Dat het document is bijgewerkt

---

## Aandachtspunten

- **Altijd vragen** als de eventnaam, datum, venue of type link niet expliciet zijn opgegeven — gok niet
- **Geen toegang?** Als het gevraagde Weeztix-account niet toegankelijk is, meld dit direct en stop. Tim vraagt dan zelf toestemming bij zijn baas.
- **Dubbel controleren:** Check in het document of het event er al in staat voordat je iets aanmaakt — om dubbele links te voorkomen
- **Weeknummer:** Gebruik de weekindeling die al in het document staat om de juiste plek te vinden
