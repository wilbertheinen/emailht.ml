---
layout: post
title: "Gmail fixt Dark Mode. Maar is het wel een echte fix?"
date: 2026-10-29
description: "Gmail laat e-maildevelopers geforceerde Dark Mode uitschakelen met een meta-tag. Maar echte ondersteuning voor prefers-color-scheme ontbreekt nog."
image: ''
tags: [Gmail, Darkmode, CSS, Apple Mail, Outlook]

---

Dark Mode in de mobiele Gmail-app is al jaren een uitdaging voor e-maildevelopers. Vooral de automatische kleurinversie kan zorgvuldig ontworpen merkkleuren, CTA's en contrasten flink veranderen.

Er is eindelijk beweging gekomen in een [langlopend issue bij Google](https://issuetracker.google.com/issues/201441498?pli=1#comment18). Alleen blijkt de gemelde fix iets anders te zijn dan waar veel developers op hoopten.

**Gmail ondersteunt niet ineens `@media (prefers-color-scheme: dark)`. We kunnen nu de geforceerde Dark Mode uitschakelen.**

## Wat heeft Google opgelost?

Google heeft voor de mobiele Gmail-apps een manier geïntroduceerd om aan te geven dat een e-mail alleen voor Light Mode is ontworpen:

```html
<meta name="color-scheme" content="light only">
```

Deze meta-tag plaats je in de `<head>` van de e-mail. Ondersteunende Gmail-apps kunnen daardoor afzien van hun automatische Dark Mode-kleurinversie, ook als de ontvanger Dark Mode gebruikt.

Dat is winst: een ontwerp kan dichter bij de bedoelde kleuren blijven. Maar het is iets anders dan ondersteuning voor een eigen Dark Mode-variant. Gmail geeft ons hiermee vooral een **opt-out** voor geforceerde Dark Mode.

## Waarom is dat niet de fix waarop we hoopten?

Bij echte ondersteuning voor `prefers-color-scheme` zouden we een aparte Dark Mode-versie kunnen ontwerpen:

```css
@media (prefers-color-scheme: dark) {
  .email-background {
    background-color: #121212 !important;
  }

  .email-text {
    color: #ffffff !important;
  }
}
```

Daarmee kun je bewust andere achtergronden, tekstkleuren, CTA's en logo's tonen. Dat werkt al jaren in Apple Mail. De mobiele Gmail-apps ondersteunen deze media query nog steeds niet op dezelfde manier.

Zoals [Litmus](https://www.litmus.com/blog/the-ultimate-guide-to-dark-mode-for-email-marketers) en [Email on Acid](https://www.emailonacid.com/blog/article/email-development/dark-mode-for-email/) beschrijven, verschillen e-mailclients sterk in hun aanpak: sommige laten kleuren ongemoeid, andere passen gedeeltelijke of volledige kleurinversie toe. Dat is iets anders dan een door de developer ontworpen Dark Mode.

## Gmail in Light Mode, Apple Mail in Dark Mode

Het wordt technisch interessant als je Gmail's automatische inversie wilt voorkomen, maar je eigen Dark Mode in Apple Mail wilt behouden.

```html
<meta name="color-scheme" content="light only">

<style>
  :root {
    color-scheme: light dark;
  }

  @media (prefers-color-scheme: dark) {
    .email-background {
      background-color: #121212 !important;
    }

    .email-text {
      color: #ffffff !important;
    }
  }
</style>
```

De meta-tag vertelt Gmail dat het ontwerp alleen Light Mode aanbiedt. De CSS-declaratie op `:root` laat Apple Mail weten dat de e-mail ook een Dark Mode-variant ondersteunt. Daardoor kunnen de eigen Dark Mode-regels daar actief blijven.

Een slimme oplossing, maar ook typerend voor e-maildevelopment: **binnen hetzelfde document geven we verschillende signalen af omdat clients die anders interpreteren.**

Dit is geen universele garantie. Het gedrag kan verschillen per appversie en accounttype. Er zijn meldingen dat de meta-tag bij niet-Google-accounts in de Gmail-app wordt verwijderd. Test daarom op echte iOS- en Android-apparaten, met de accounttypen die voor jouw doelgroep relevant zijn. Ook previewsystemen kunnen achterlopen op de daadwerkelijke Gmail-app.

## Willen we Dark Mode eigenlijk wel uitschakelen?

Daar zit voor mij de belangrijkste kanttekening.

Met `light only` behouden we meer controle over branding en rendering, maar we negeren mogelijk ook een bewuste voorkeur van de ontvanger. Iemand die Dark Mode gebruikt, krijgt dan alsnog een lichte e-mail te zien.

Vanuit toegankelijkheid en gebruikerservaring is dat niet automatisch de beste keuze. Een leesbaar contrast, herkenbare CTA's en een prettig ontwerp blijven belangrijker dan het koste wat kost behouden van exacte merkkleuren.

De meta-tag is dus een nuttige optie, geen oplossing die je zonder afweging in iedere template moet opnemen.

## En Outlook?

Apple Mail biedt al jaren mogelijkheden om Dark Mode zelf te stylen. Ook delen van het Outlook-ecosysteem bieden Dark Mode-targeting, maar de ondersteuning verschilt per versie en platform. Consistentie blijft daar een uitdaging.

## Conclusie: een stap vooruit, maar niet de eindoplossing

Google heeft wel degelijk iets verbeterd. We kunnen de geforceerde Dark Mode in ondersteunende Gmail-apps nu beïnvloeden met één meta-tag, zonder ingewikkelde kleurinversie-hacks.

Maar de oorspronkelijke wens blijft bestaan: **zelf een Dark Mode-ontwerp aanbieden via `@media (prefers-color-scheme: dark)`.**

Tot die tijd kunnen we kiezen tussen Gmail's automatische kleurbehandeling en een Light Mode-opt-out. Dat is meer controle dan voorheen, maar nog niet de controle die Apple Mail ons al jaren geeft.

**We kunnen Gmail's Dark Mode nu beter tegenhouden. Maar echt ontwerpen voor Gmail Dark Mode? Daar wachten we nog op.**

## Bronnen

- [Google Issue Tracker – Gmail, prefers-color-scheme en kleurinversie (comment 18)](https://issuetracker.google.com/issues/201441498?pli=1#comment18)
- [Litmus – Dark Mode for Email: The Definitive Guide for Marketers](https://www.litmus.com/blog/the-ultimate-guide-to-dark-mode-for-email-marketers)
- [Email on Acid – Master the Art of Dark Mode Email Design and Coding](https://www.emailonacid.com/blog/article/email-development/dark-mode-for-email/)
- [Dyspatch – Gmail Now Respects Your Color-Scheme](https://www.dyspatch.io/blog/gmail-now-respects-your-color-scheme-how-to-stop-forced-dark-mode-in-the-gmail-app/)
