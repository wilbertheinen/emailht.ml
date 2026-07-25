---
layout: post
title: "Het uitfaseren van Classic Outlook: Wat betekent dit voor HTML- en CSS-ontwikkeling van e-mails?"
date: 2026-07-25
description: Van Handmatig Coderen naar Slimmer Produceren
image: '/images/outlook-email-development.png'
tags: [outlook, html, css, emaildevelopment, microsoft]
---

# Oktober 2026: Het uitfaseren van Classic Outlook en de impact op HTML- en CSS-ontwikkeling van e-mails

**Oktober 2026 markeert een belangrijke mijlpaal voor e-mail developers.** Microsoft zet vanaf deze periode een volgende grote stap in de uitfasering van Classic Outlook. Daarmee komt langzaam een einde aan een tijdperk waarin de Microsoft Word-rendering engine jarenlang de grootste uitdaging vormde voor HTML-e-mailontwikkeling.

Voor veel organisaties zal Classic Outlook nog enige tijd beschikbaar blijven, maar de koers is duidelijk: **New Outlook wordt de standaard**. Dat heeft grote gevolgen voor de manier waarop e-mailtemplates worden ontworpen, ontwikkeld en onderhouden.

## Waarom Classic Outlook zo problematisch was

Classic Outlook gebruikte de Microsoft Word-engine om HTML te renderen. Deze engine ondersteunt slechts een beperkt deel van HTML en CSS.

Daardoor waren e-mail developers jarenlang afhankelijk van technieken zoals:

- Tabellen voor vrijwel iedere layout
- VML voor achtergrondafbeeldingen, knoppen en gradients
- MSO conditional comments
- Inline CSS
- Extra wrapper-tabellen voor positionering
- Outlook-specifieke spacing-hacks

Een relatief eenvoudige hero-banner kon hierdoor tientallen extra regels code bevatten die uitsluitend bedoeld waren voor Outlook.

## Oktober 2026: een belangrijk omslagpunt

Vanaf **oktober 2026** stimuleert Microsoft organisaties nadrukkelijk om over te stappen op New Outlook. Hoewel Classic Outlook niet direct overal zal verdwijnen, wordt het steeds duidelijker dat nieuwe investeringen zich moeten richten op de moderne Outlook-client.

Voor e-mailteams betekent dit dat het moment is aangebroken om kritisch naar bestaande templates te kijken.

Vragen die steeds relevanter worden zijn:

- Hoeveel Outlook-specifieke code bevatten onze templates?
- Welke componenten gebruiken nog VML?
- Welke hacks kunnen op termijn verdwijnen?
- Hoe maken we onze componenten eenvoudiger onderhoudbaar?

## De overstap naar New Outlook

New Outlook maakt geen gebruik meer van de Word-rendering engine. In plaats daarvan gebruikt Microsoft dezelfde renderingtechnologie als Outlook op het web (Outlook Web App).

Dat betekent dat New Outlook zich veel meer gedraagt als moderne clients zoals:

- Outlook.com
- Gmail
- Apple Mail
- Yahoo Mail

Hierdoor wordt de ondersteuning voor moderne HTML en CSS aanzienlijk beter.

## Wat betekent dit voor e-mail developers?

### Minder Outlook-specifieke code

De grootste winst zit in het verdwijnen van Outlook-hacks.

Denk bijvoorbeeld aan:

- Geen VML-knoppen meer nodig
- Minder conditional comments
- Minder dubbele code
- Minder Outlook-only tabellen
- Minder uitzonderingen in componenten

Templates worden hierdoor overzichtelijker, kleiner en eenvoudiger te onderhouden.

## Minder VML

VML (Vector Markup Language) werd jarenlang gebruikt voor onder andere:

- Achtergrondafbeeldingen
- Hero-secties
- Afgeronde knoppen
- Gradiënten

Een typische VML-sectie was vaak groter dan de HTML die hij ondersteunde.

Naarmate Classic Outlook verder verdwijnt, kunnen deze VML-oplossingen stap voor stap uit de templates worden verwijderd.

Dat levert op:

- Minder HTML
- Kleinere e-mails
- Minder onderhoud
- Snellere ontwikkeling
- Betere leesbaarheid van templates

## Meer ruimte voor moderne CSS

Hoewel e-mails altijd beperkingen zullen houden, biedt New Outlook aanzienlijk meer mogelijkheden.

Voorbeelden zijn:

- Betere ondersteuning voor `border-radius`
- Consistentere padding en margins
- Betrouwbaardere achtergrondafbeeldingen
- Modernere spacing
- Minder renderingverschillen

Daardoor kunnen developers eenvoudiger componenten bouwen die zich in meerdere clients hetzelfde gedragen.

## Wordt e-mail development ineens makkelijk?

Nee.

Er blijven grote verschillen bestaan tussen e-mailclients.

Zo gelden nog steeds beperkingen zoals:

- Gmail verwijdert bepaalde CSS uit `<head>`
- JavaScript wordt vrijwel nergens ondersteund
- CSS Grid blijft beperkt bruikbaar
- Sommige clients behandelen media queries nog altijd anders

Outlook was echter jarenlang verantwoordelijk voor een groot deel van de complexiteit. Juist daarom voelt de overgang naar New Outlook voor veel developers als een enorme stap vooruit.

## Tijd om technische schuld af te bouwen

Veel organisaties beschikken inmiddels over honderden templates waarin Outlook-specifieke oplossingen diep zijn verweven.

Oktober 2026 is daarom een uitstekend moment om een moderniseringsslag te starten.

Een mogelijke aanpak:

1. Inventariseer alle Outlook-specifieke componenten.
2. Meet welke Outlook-versies nog daadwerkelijk worden gebruikt.
3. Ontwikkel nieuwe componenten zonder VML waar mogelijk.
4. Houd oude componenten tijdelijk beschikbaar voor organisaties die Classic Outlook nog gebruiken.
5. Bouw de technische schuld gefaseerd af.

## AI profiteert mee

Een bijkomend voordeel van deze ontwikkeling is dat AI veel beter overweg kan met moderne code.

Wanneer templates minder VML, nested tabellen en Outlook-specifieke uitzonderingen bevatten, kunnen AI-tools zoals GitHub Copilot en ChatGPT:

- Sneller componenten genereren
- Beter refactoren
- Renderingproblemen eenvoudiger analyseren
- Betere optimalisatievoorstellen doen
- Documentatie grotendeels automatisch genereren

Een eenvoudigere codebase maakt AI daarmee nog waardevoller binnen het ontwikkelproces.

## Conclusie

De veranderingen die Microsoft in **oktober 2026** doorvoert rondom Classic Outlook vormen een belangrijk kantelpunt voor de e-mailindustrie.

Hoewel de overgang nog meerdere jaren zal duren, is de richting duidelijk. Minder afhankelijkheid van de Word-rendering engine betekent minder hacks, minder VML en eenvoudiger onderhoudbare templates.

Voor e-mail developers biedt dit een unieke kans om bestaande componenten opnieuw te ontwerpen, technische schuld af te bouwen en de basis te leggen voor een modernere, toekomstbestendige e-mailcodebase.