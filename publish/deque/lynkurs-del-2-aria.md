---
title: Fast Track to Accessibility for Web Developers, Core Techniques Part 2
tags:
  - accessibility
  - a11y
date: 2025-01-24
---
## Om ARIA
ARIA brukes for å utvide [de semantiske mulighetene til html-elementer](https://www.w3.org/WAI/ARIA/apg/example-index/).

ARIA er til primært for blinde og døvblinde.

Delvis ARIA-implementasjon er dårligere enn ingen ARIA. Dersom du vet at du trenger det må du sette deg inn i [mønstrene de har laget](https://www.w3.org/WAI/ARIA/apg/patterns/).

**Dersom det finnes en semantisk HTML er det smartest å bruke den. Native er alltid bedre.**

### Role
Når du setter på en rolle med aria overskriver du de semantiske verdiene som var definert fra før. Å endre rollen vil ikke endre den visuelle visningen av elementet.

```diff
- <p role="img">
- <div role="img">
- <span role="img">
- <table role="img">
+ <img />
```

`role="presentation"` skrur av semantisk mening ved et element. Dette burde ikke brukes på elementer en bruker skal "tab"-e til.

**Du kan ikke finne opp egne roller for elementer.** 

### Names/Label
Navnet til en lenker (og mange andre elementer) vil være teksten i den. Dette kan fort skape problemer (se Jøkul-cards):
![](Pasted%20image%2020250124112647.png)
For skjema-elementer er det `label`-elementet og koblingen med `for="element"` og `id="element"` som gir navn til elementet.

## Aria-label
- `aria-label` overskriver navnet til elementet. Denne er usynlig for seende.
- `aria-labelledby` beskriver hvor navnet til elementet er. aria-labelledby kan være flere enn ett ord, men: **dersom du har en labelledby egenskap med mellomrom vil disse kombineres for å gi deg labelen**. Teksten du refererer til med labelledby er som regel synlig på siden et sted.
	- `aria-describedby` fungerer på samme måte, og brukes for å gi instrukser utover det label gjør.

### Hva blir det endelige navnet på elementet dersom du har både navn, tittel, aria-label og aria-labelledby?
I følge [spesifikasjonen for navne- og beskrivelsesutregning](https://www.w3.org/TR/accname-1.1/) er hierarkiet sånn:
1. aria-labelledby
2. aria-label
3. navnet i elementet
4. tittel

**NB: Et ikke-semantisk element kan ikke ha label.**

Dynamiske aria-verdier er brukt flittig i [mønstrene beskrevet tidligere](https://www.w3.org/WAI/ARIA/apg/patterns/).

### aria-hidden
`aria-hidden` er med få unntak ikke riktig metode for å skjule noe for en bruker.

## Keyboard mønster
ARIA har noen metoder som blir brukt for å gjøre kryssplattform-opplevelsen bedre for keyboard brukere. Her er noen tips.

### Tabindex
- tabindex="0" legger til et element i den [naturlige rekkefølgen av elementer](#Naturlig%20rekkefølge%20av%20elementer) av "tabbable" elementer. Ikke gjør dette med ikke-interagerbare elementer
- tabindex="-1" gjør at et element kan få fokus. Mye brukt for for eksempel modaler og dialoger. Dette setter du på headingen i det respektive elementet.
- ikke sett tabindex til noe annet enn 0. Det skaper flere problemer enn det løser fordi du blir tvunget til å ha full oversikt over alle tab-bare elementer på siden.

### Naturlig rekkefølge av elementer
Den naturlige rekkefølgen av elementer er det samme som rekkefølgen i DOM-en.

### Ikke send fokus rundt på siden unaturlig
Unntaket er modaler og dialoger. Her bør du stoppe brukeren fra å tabbe utenfor.

## Modaler
En overskrift burde få fokus i modalen eller dialogen du sender fokus til. Dette kan du gjøre med de nevnte måtene for `aria-labelledby` på heading-elementet i modalen.

### Når modalen lukkes
Send fokus til et logisk sted. Hvor dette er vil variere med kontekst.

### Radiogrupper
- Du skal ikke kunne tabbe til alle radioelementene i en gruppe
- Navigasjonen i radiogruppa skal skje med piltastene, ikke tab
- Dersom noe er valgt skal det valgte elementet skal få fokus, ikke det første

### Tablister
En tab-liste bør virke helt som en radiogruppe. 

*Du kan også bruke piltaster som ikke velger tabben automatisk, men dette er ikke anbefalt.*

## Lage egne metoder
Ikke gjør det dersom det finnes eksisterende måter. Dersom det ikke finnes gode alternativer kan du lage egne, men da må det være veldig intuitivt for de aller fleste brukere.

## Disabled state
`aria-disabled="true"` er anbefalt metode for å vise disabled state, fordi det ikke fjerner elementet fra tab-lista. 

Dersom du kun setter disabled="true" på for eksempel et skjemaelement eller en knapp vil den fjernes, og dermed ikke kunne finnes av tilgjengelighetsverktøy.

## aria-live
Ved å gjøre et element aria-live vil tilgjengelighetsverktøy følge med på endringer i teksten i elementet. Dersom du ikke endrer teksten i, men bare stil på elementet vil dette med andre ord ikke fanges opp.

- `aria-live="assertive"` leses med en gang, mens
- `aria-live="polite"` leses ved et logisk tidspunkt. Den puttes i en kø og venter på tidspunktet den kan leses opp.
- `role="alert"` vil bli en aria-live automatisk

### Regler for aria-live
- `aria-live` elementer må som nevnt starte tomme
- `aria-live` elementet burde lastet ved sideinnlasting for å sikre at tilgjengelighetsverktøyene har fått det med seg
- Ikke flytt fokus til aria-live elementer. Velg enten eller.
- Hold meldingen så kort som mulig
- Test med en skjemleser

## Regler for tidsgrenser
En bruker må kunne stoppe, forlenge eller endre tidsavgrensningene du setter. Det finnes noen unntak for tidsavgrensede hendelser som billettsalg, dersom det er nødvendig for systemet eller tidsavgrensinga er lengre enn 20 timer.

# Ressurser
- [Hvordan lage gode skjemaer](https://www.w3.org/WAI/tutorials/forms/)
- [Videogjennomgang av et godt eksempel på et skjema (krever innlogging)](https://dequeuniversity.com/class/fast-track-for-web-developers-advanced/form-validation-and-feedback).