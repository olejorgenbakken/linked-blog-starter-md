## Intro

Knapper starter en handling. Teksten på knappen forteller hva som vil skje når brukeren klikker på den.

## Varianter

- **Primærknapp:** brukes til den viktigste handlingen på en side - hovedhandlingen. En side kan noen ganger ha mer enn en hovedhandling, men ikke mange.
- **Sekundærknapp:** brukes til handlinger som ikke er like viktige for oss eller brukeren.
- **Tertiærknapp:** brukes til handlinger som er mindre viktige, eller som kan gi uønskede konsekvenser.
- **Ghost-knapp:** brukes til sekundære handlinger som å åpne menyer. Bruk den gjerne som triggerelement for [ContextualMenu](https://jokul.fremtind.no/komponenter/contextualmenu/)

## Lastemodus

Hvis du skal bruke lastemodus i knappen må du sørge for at `@fremtind/jkl-loader/loader.min.css` er lastet inn i klienten.

## Knappetyper

Knappene våre har et hierarki. Når brukeren har flere knapper å velge mellom, skal vi kun ha én primærknapp.

## Tekst på knapper

Knappetekster skal være så enkle og korte som mulig og skal oppfordre til handling. Bruk helst bare to ord:

## Ikoner i knapper

Knappene kan ta inn et ikon som vises til venstre eller høyre for knappeteksten. Om du ikke sender inn tekst vises kun ikonet. Som standard vises ikonet til venstre for knappeteksten.

### Knapper med kun ikon

Vær forsiktig med å bruke knapper med kun ikon, da dette krever ekstra forståelse fra brukerens side. De kan likevel være nyttige i ekspertverktøy, og i mønstre som verktøylinjer. Når du bruker en knapp med kun ikon må du huske å angi en tekstlig beskrivelse av funksjonaliteten gjennom f.eks. et [Tooltip](https://jokul.fremtind.no/komponenter/tooltip) eller `title`-attributten.

```
<Tooltip>
    <TooltipTrigger><Button variant="ghost" icon={<PenIcon />} /></TooltipTrigger>
    <TooltipContent>Rediger innhold</TooltipContent>
<Tooltip/>
```

## Knapper rendret som andre elementer

I noen tilfeller representerer en knapp et annet semantisk element, for eksempel en lenke. Knappekomponentene i Jøkul er derfor _polymorfe_, og kan ta inn en React-komponent eller et HTML-element den skal rendre ut.

```
// Rendrer en vanlig HTML-lenke til gitt href:
<Button type="primary" as="a" href="/order">
    Bestill nå
</Button>;

// Rendrer en Remix-lenke som bruker rammeverkets ruting:
import { Link } from "@remix-run/react";

<Button as={Link} to="/products">
    Se alle produkter
</Button>;
```

Knappen tar automatisk imot riktige props og riktig `ref` for komponenten som sendes inn, slik at du får typesikkerhet.

## Eksempler på bruk

Du finner et [eksempel på en primærknapp brukt i skjemakontekst](https://jokul.fremtind.no/demoer/skjemavalidering/) under Demoer. [Koden til eksempelet](https://github.com/fremtind/jokul/blob/main/portal/src/pages/demoer/skjemavalidering.tsx) finner du på GitHub.

![](https://jokul.fremtind.no/assets/documentation/button/button-primary-loading.gif)

En primærknapp som har startet en handling og nå er i lastemodus. Klikk for å se større.








Problemer
- Card definert som en lenke gjør alt innhold i carden til value. Dette er veldig mye støy for skjemlesere.
	- Særlig ille når du har bilder i cardet da alt-teksten blir en del av lenketeksten.
	- Bør hele cardet være klikkbart i det hele tatt?
- Clickable?
	- What it do?