---
layout: post
title: "Gaat Gmail eindelijk prefers-color-scheme ondersteunen?"
date: 2026-10-29
description: "Een mogelijke Gmail Dark Mode-fix, de verschillen tussen e-mailclients en een slimme workaround voor Apple Mail en Gmail."
image: ''
tags: [Gmail, Darkmode, CSS, Apple Mail, Outlook]

---

Dark Mode in de mobiele Gmail-app is al jaren een uitdaging voor e-maildevelopers. Waar Apple Mail ons met `@media (prefers-color-scheme: dark)` controle geeft over de weergave, bepaalt Gmail op iOS en Android grotendeels zelf wat er met onze kleuren gebeurt.

Maar daar lijkt mogelijk iets te veranderen.

## Er gebeurt iets bij Gmail

In [Google's Issue Tracker](https://issuetracker.google.com/issues/201441498#comment18) staat een issue over **`prefers-color-scheme` en automatische kleurinversie in de Gmail-app voor iOS en Android**. Bij het issue is een fix gemeld.

Dat is nog geen garantie dat Gmail binnenkort volledige ondersteuning voor de media query krijgt. De daadwerkelijke werking moet eerst in de apps worden getest. Maar het is een interessante ontwikkeling voor iedereen die HTML-e-mails bouwt.

## Waarom Dark Mode zo lastig blijft

Zoals [Litmus](https://www.litmus.com/blog/the-ultimate-guide-to-dark-mode-for-email-marketers) en [Email on Acid](https://www.emailonacid.com/blog/article/email-development/dark-mode-for-email/) beschrijven, gebruiken e-mailclients verschillende benaderingen:

- **No color changes:** de interface wordt donker, maar de e-mail behoudt zijn kleuren.
- **Partial color invert:** bepaalde achtergronden en tekstkleuren worden automatisch aangepast.
- **Full color invert:** zowel lichte als donkere kleuren kunnen worden geïnverteerd.

Daarnaast ondersteunen sommige clients **developer-controlled Dark Mode**: je kunt dan zelf stijlen aanbieden via een media query. Dat is geen vierde inversiemethode, maar een mogelijkheid om de weergave bewust te sturen.

Automatische inversie kan merkkleuren, CTA's, logo's en contrasten veranderen. Met ondersteuning voor `prefers-color-scheme` kun je bijvoorbeeld schrijven:

```css
@media (prefers-color-scheme: dark) {
  .email-background {
    background-color: #111111 !important;
  }

  .email-text {
    color: #ffffff !important;
  }
}
```

Het verschil is belangrijk: **Dark Mode ontwerpen in plaats van Dark Mode achteraf repareren.**

## Apple Mail laat zien hoe het kan

Apple Mail ondersteunt al jaren het gebruik van `prefers-color-scheme`. Met de juiste declaraties kun je een eigen Dark Mode-variant aanbieden:

```html
<meta name="color-scheme" content="light dark">
<meta name="supported-color-schemes" content="light dark">

<style>
  :root {
    color-scheme: light dark;
    supported-color-schemes: light dark;
  }
</style>
```

Vervolgens kun je met `@media (prefers-color-scheme: dark)` specifieke tekst- en achtergrondkleuren, CTA's en zelfs alternatieve logo's instellen.

## Een interessante workaround voor Gmail en Apple Mail

Een creatieve techniek is om de HTML-meta-informatie en de CSS-declaratie bewust verschillend in te stellen:

```html
<meta name="color-scheme" content="light only">

<style>
  :root {
    color-scheme: light dark;
  }

  @media (prefers-color-scheme: dark) {
    /* Eigen Dark Mode-styling */
  }
</style>
```

Het idee: met `light only` probeer je Gmail zijn automatische Dark Mode-behandeling te laten beperken, terwijl Apple Mail via de CSS-declaratie nog steeds de eigen Dark Mode-stijlen kan toepassen.

**Let op:** dit is een clientafhankelijke workaround, geen gegarandeerde oplossing voor iedere Gmail-versie. Test de uiteindelijke e-mail op iOS en Android en controleer ook het gedrag in Apple Mail.

Het is tegelijk een mooi voorbeeld van de huidige complexiteit: we geven binnen één HTML-document verschillende signalen af omdat mailclients die verschillend interpreteren.

## Waarom ondersteuning in Gmail belangrijk zou zijn

Voor e-maildevelopers zou betrouwbare ondersteuning betekenen dat we:

- Merkkleuren en contrasten bewuster kunnen beheren.
- CTA's en logo's specifiek voor Dark Mode kunnen ontwerpen.
- Minder client-specifieke workarounds nodig hebben.
- Dark Mode als vaste variant in een modulair e-mail design system kunnen opnemen.
- De toegankelijkheid en voorspelbaarheid van e-mailweergave kunnen verbeteren.

## En Outlook dan?

Ook delen van het Outlook-ecosysteem, waaronder Outlook.com, bieden mogelijkheden om Dark Mode-styling te targeten. De ondersteuning verschilt echter per versie en platform. Naast media queries worden in bepaalde Outlook-clients bijvoorbeeld selectors als `[data-ogsc]` gebruikt.

De uitdaging is dus niet simpelweg dat Microsoft geen Dark Mode ondersteunt, maar dat de implementatie binnen het Outlook-landschap niet overal consistent is.

## Zijn we er bijna?

Een gemelde fix in Google's Issue Tracker is nog geen officiële bevestiging van volledige `prefers-color-scheme`-ondersteuning in de Gmail-app. Maar als Gmail daadwerkelijk meer controle gaat bieden, kan dat een belangrijke stap zijn richting voorspelbaardere Dark Mode-e-mails.

Apple Mail laat al jaren zien wat mogelijk is. Hopelijk volgt Gmail, en wordt de ondersteuning binnen Outlook uiteindelijk ook consistenter.

**Minder tijd besteden aan het bestrijden van Dark Mode, en meer tijd aan het ontwerpen ervan.**

## Bronnen

- [Google Issue Tracker – prefers-color-scheme en Gmail Dark Mode](https://issuetracker.google.com/issues/201441498#comment18)
- [Litmus – Dark Mode for Email: The Definitive Guide for Marketers](https://www.litmus.com/blog/the-ultimate-guide-to-dark-mode-for-email-marketers)
- [Email on Acid – Master the Art of Dark Mode Email Design and Coding](https://www.emailonacid.com/blog/article/email-development/dark-mode-for-email/)
