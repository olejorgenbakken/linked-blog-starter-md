---
title: Fast Track to Accessibility for Web Developers, Core Techniques Part 1
tags:
  - accessibility
  - a11y
date: 2025-01-10
---
## The Big Concepts in Web Accessibility
Universell utforming er lovpålagt, og kan ikke være en ettertanke. Alt som er visuelt forklart må også forklares i klartekst. Å lære seg hvordan tilgjengelighetstreet fungerer vil hjelpe i forståelsen av hva hjelpeverktøyene bruker for å lese innholdet på skjermen.

Det er ordentlige folk i enden av alle problemene vi løser. Dette gjør deres hverdag enklere, bedre og mer fullkommen.
### Huskeregler
- Bruk verktøy som automatiserer prosessen, men husk at verktøyene ikke er nok.
- Test med skjermlesere.
	- Jo oftere du bruker den, jo enklere blir det.
	- Prøv å lære deg snarveiene.
	- Bruk mobilverktøyene også.
## Who is Accessibility For?

| Gruppe                             | Hjelpemidler                                                                                   |
| ---------------------------------- | ---------------------------------------------------------------------------------------------- |
| Døve                               | Undertekster for bilder og videoer.                                                            |
| Mobilitetshemmede                  | Ekstra tid ved navigering. <br>Tastaturtilgjengelighet.                                        |
| Svaksynte                          | Fargekontrast og responsiv design                                                              |
| Fargeblinde                        | Fargekontrast                                                                                  |
| Blinde                             | Tilgjengelighetstreet i nettleseren og tastaturtilgjengelighet                                 |
| Personer med nedsatt kognitiv evne | Intuitive løsninger.<br>Direkte og enkelt språk.<br>Alternative visningsvalg som video og lyd. |

Selv om mange av hjelpeverktøyene som brukes av folk med nedsatt mobilitet ikke er tastaturbaserte ender de som regel opp med å behandle informasjonen på samme måte som et tastatur.

Det er viktig å huske at folk havne i flere av kategoriene samtidig. For en person som er **døvblind må man for eksempel dekke alle kravene for både døve og for blinde, i tillegg til tilrettelegging av videoer og bilder**.

Alle vil trenge tilgjengelighetsverktøy på et eller annet tidspunkt. For eksempel sitter jeg og skriver dette notatet med nettleseren og Microsoft Word oppe samtidig på en mindre skjerm. Hadde ikke begge disse applikasjonene støttet responsivitet hadde jeg ikke kunnet gjøre jobben min på en god og effektiv måte.
## Automated Accessibility Tools
[Axe-utvidelsen for nettlesere](https://www.deque.com/axe/) kan hjelpe med å sjekke om nettsiden du jobber på oppfyller kravene til universell utforming. Den burde brukes.

**Husk å endre tilstanden på elementene, delene og sidene du ønsker å teste. Axe vil gjøre en evaluering ved innlasting, så for å sjekke om en feilhåndtering er gjort på en god måte må du laste den inn på nytt etter å ha tvunget fram en feil.**

## Keyboard Accessibility
Alle navigasjonsmønster med mus, eller berøring, må ha en ekvivalent med tastatur. 

Her er reglene for tastaturnavigasjon:
### Fokus
1. Navigasjonselementer må kunne fokuseres. Dette kan enkelt testes med tab-knappen.
2. Navigasjonselementer må kunne navigeres vekk fra.
3. Fokuserte elementer må ha en visuell fokus-tilstand.
4. Fokuserte elementer må være synlige på skjermen.
5. Fokuserte elementer må være utildekket av andre elementer.
6. Elementer som ikke har en aktiv tilstand (for eksempel tekst, bilder og tabeller) skal ikke ha fokus-tilstander.
7. Rekkefølgen på fokus-elementer må være logiske. Dette betyr som regel at rekkefølgen skal følge den visuelle rekkefølgen. **Vær obs på at det er ikke alltid er logisk å følge den visuelle rekkefølgen, ta en avgjørelse på hva som er den logiske rekkefølgen i disse tilfellene**.
8. Dynamisk innhold har samme regler for rekkefølge. For eksempel hvis du har en knapp som åpner en modal må brukeren kunne fokusere kun på innholdet i modalen, samtidig som det er mulig å lukke modalen.
### Funksjonalitet
1. Alle kontrollere i et grensesnitt må kunne betjenes med tastaturet.
2. Kontrollene burde følge konvensjoner.
### Brukerkontroll
1. Funksjonalitet skal ikke være tidsavgrenset, med mindre det er viktig for funksjonaliteten.
2. Fokusering skal ikke gjøre endringer i konteksten av det du gjør. Eksempelvis dersom du har en modal som åpnes ved at en bruker klikker på en knapp så skal ikke fokusering på knappen åpne modalen automatisk.
## Other Input Methods (Mouse, Voice, Touch, Gestures)
### Stemmestyring
Hvis nettsiden er tilgjengelig med tastatur er du nærmest garantert å ha en nettside som også er tilgjengelig med stemmestyringsverktøy. Dette er fordi stemmestyring emulerer et tastatur i bakgrunnen.
### Sveiping (gestures) og bevegelse (moDon)
Alle navigasjonsmønstre med sveiping og bevegelse må også være tilgjengelige med tastatur. I tillegg må du kunne skru av navigering med bevegelse for å sikre at mennesker med for eksempel muskelrykninger ikke navigerer feil.
### Kontakt (touch)
De samme reglene for navigasjonsmønstre med bevegelse gjelder for kontakt.

Det er samtidig noen flere ting å ta hensyn til. Den fysiske størrelsen på elementene må møte et minstekrav på 24 x 24 pixler for å møte AA-kriteriet isuksesskriteriet for «2.5.8 Target Size (Minimum)» satt etter WCAG 2.2. 
	Det finnes unntak for dette kriteriet, men hovedpoenget er å gjøre det enkelt å treffe riktig element på en gitt side.
### Mus
Navigasjon med mus er ofte ikke et problem for utviklere og designere å tenke på fordi de fleste navigerer med dem daglig. Det er allikevel viktig å huske på
1. at reglene for fysisk størrelse gjelder for mus også.
2. at funksjonalitet som bygger på dra og slipp må ha en ekvivalent uten.
## Setting up NVDA
Denne delen er relevant kun for Windows, da NVDA ikke eksisterer på Mac. På Mac brukes VoiceOver. 

Det kan være lurt å vite at det er veldig stor forskjell på bruk av skjermlesere blant utviklere, som bruker skjermlesere til kun jobb, og de som bruker dem i sin hverdag. 
	Utviklere sitter som regel på Mac med VoiceOver, mens [de fleste skjermleser-brukere sitter på en Windows maskin med enten JAWS eller NVDA](https://webaim.org/projects/screenreadersurvey10/#primary).
## Testing with NVDA
Denne delen er mer generell enn den forrige, og inneholder en del tips som er relevant for all testing med tilgjengelighetsverktøy, inkludert VoiceOver på Mac.
### Hvordan teste på en god måte
1. Bruk god tid. Det kommer til å være mye støy i starten, men du kan endre ting som du selv ønsker for å gjøre verktøyet mer på den måten du ønsker det.
2. Ikke bruk mus. Blinde ville ikke brukt mus, du burde derfor heller ikke det når du skal teste. Du kan bruke tastaturet. Mange blinde memorerer tastaturoppsettet, og kan derfor «gjette» seg fram effektivt.
### Ting å se etter mens du tester
Hør etter «names», «roles» og «value» på elementene. En søkeknapp skal si at den er et søkefelt. Dette er et av kravene for å oppnå [«4.1.2 Name, Role, Value» i WCAG 2.2](https://www.w3.org/TR/WCAG22/#name-role-value). Hør også etter tilbakemeldinger på handlingene du gjør.

> For all [user interface components](https://www.w3.org/TR/WCAG22/#dfn-user-interface-components "a part of the content that is perceived by users as a single control for a distinct function") (including but not limited to: form elements, links and components generated by scripts), the [name](https://www.w3.org/TR/WCAG22/#dfn-name "text by which software can identify a component within web content to the user") and [role](https://www.w3.org/TR/WCAG22/#dfn-role "text or number by which software can identify the function of a component within Web content") can be [programmatically determined](https://www.w3.org/TR/WCAG22/#dfn-programmatically-determinable "determined by software from author-supplied data provided in a way that different user agents, including assistive technologies, can extract and present this information to users in different modalities"); [states](https://www.w3.org/TR/WCAG22/#dfn-states "dynamic property expressing characteristics of a user interface component that may change in response to user action or automated processes"), properties, and values that can be set by the user can be [programmatically set](https://www.w3.org/TR/WCAG22/#dfn-programmatically-set "set by software using methods that are supported by user agents, including assistive technologies"); and notification of changes to these items is available to [user agents](https://www.w3.org/TR/WCAG22/#dfn-user-agents "any software that retrieves and presents web content for users"), including [assistive technologies](https://www.w3.org/TR/WCAG22/#dfn-assistive-technologies "hardware and/or software that acts as a user agent, or along with a mainstream user agent, to provide functionality to meet the requirements of users with disabilities that go beyond those offered by mainstream user agents").

Sjekk at nettsiden bruker semantiske verdier på innholdet. For eksempel landemerker (landmarks), riktig overskriftsstil i riktig kontekst, tabeller og lister.
### De elementære tastatur-snarveiene
1. **Tab** for å gå fram mellom fokus-elementer.
2. **Shift** + **Tab** for å gå tilbake
3. **Enter** for å aktivere lenker
4. **Mellomrom** for å
	1. velge inputfelter som avkrysningsbokser og radioknapper.
	2. aktivere knapper. Noen ganger fungerer også enter her.
5. **Piltastene** for å
	1. navigere i nedtrekksmenyer.
	2. navigere mellom valgmuligheter i radiogrupper.
## Screen Orientation
Ikke roter innhold automatisk fordi du mener innholdet er bedre om det blir konsumert på en gitt måte. Det er ikke sikkert brukeren kan rotere enheten de bruker.
## Semantic Structure
Semantisk struktur er et stort tema, og noe av det viktigste (om ikke det aller viktigste) du gjør som utvikler av et grensesnitt. Dette er grunnlaget for hvordan nettsiden konsumeres av brukere og verktøyene de bruker. 

### Semantiske elementer består av tre ting
1. **Name**. Dette er teksten elementet består av. For eksempel teksten i en overskrift, eller alternativ tekst til et bilde.
2. **Role**. Role sier hva slag element det er. En lenke, en overskrift og lignende.
3. **Value**. Verdien til elementet sier noe om egenskapene (property) eller tilstanden (state) til elementet.
## Page Title
Dette er det første en skjermleser leser opp på siden. Den burde være kort og konsis.

Dersom innholdet på siden endrer seg signifikant bør tittelen på siden endres, for eksempel før og etter et søk.
## Language
Alle nettsider må ha informasjon om hvilket språk en nettside er skrevet på. Dersom språket er ulikt ved et ord, setning eller seksjon kan dette programmeres for at hjelpeverktøyene får dette med seg.
## Landmarks
[Landemerker](https://www.w3.org/TR/wai-aria/#landmark_roles) er det som oversetter den intuitive visuelle fordelingen av innholdet på en side til kode. Disse er navigerbare med skjermlesere. De vanligste, som de fleste nettsider trenger er **header**, **nav**, **main** og **footer**. Flere er ikke alltid bedre.
## Headings
På samme måte som landemerker er [overskrifter](https://www.w3.org/TR/wai-aria/#heading) en måte å dele innhold på siden. Med overskrifter deler du ikke tekst på siden. Det er viktig å vite at dette ikke er stiler, men semantiske elementer som h1, h2, h3, h4, h5.
## Navigation and links
### Navigasjon mellom ulike sider
1. Putt lenkene i et **nav**-element.
2. Bruk listeformat i **nav**-elementet med bruk av en **ul** bestående av **li**-elementer. Dersom lista består av undergrupper, kan du ha ul-elementer i et li-element.
3. Hver lenke må ha meningsbærende tekst. Gjør det enkelt å skjønne hvor brukeren havner ved å klikke på lenken. Teksten må være konsekvent mellom sider.
### Navigasjon på samme side
Lenken bør ta brukeren til et element med tekst, og ikke til et tomt element.
### Generelle tips for lenker
1. Burde se ulik ut enn løpende tekst. Gjerne med en understrek.
2. Teksten i lenken bør være meningsbærende. Ikke bruk «les mer her».
## Images
Bilder må ha alternativ tekst. Vi deler bilder på nett inn i to grupper.
### Informative bilder
#### Enkle bilder
Enkle bilder er enkle å beskrive med alternativ tekst. Pass på at den alternative teksten er tilstrekkelig for å gi en blind bruker samme nivå av forståelse som en seende. Ikke vær redd for å skrive for mye om det er det som trengs, men pass på at du ikke beskriver alt som er på bildet dersom det ikke trengs. Det vil være årsaken til at du bruker et bilde som bestemmer hvor mye av bildet som må beskrives, ikke nødvendigvis motivet i bildet.
#### Komplekse bilder
Komplekse bilder som for eksempel grafer må på samme måte beskrives så en blind bruker forstår alt ved grafen. Derfor kan det være nødvendig å lage egne måter å beskrive en graf på, som for eksempel en egen tabell, en egen side eller en tekstblokk som gir all kontekst.
#### Aktive bilder
Aktive bilder er bilder som også er lenker. De fleste av disse bildene er ikoner, som bør kunne forklares ved enkeltord. Et forstørrelsesglass som aktiverer et søk burde for eksempel bare beskriver som «søk».
#### Bilder av tekst
Bilder av tekst burde inneholde teksten og stilen teksten er satt i.
#### Captcha-bilder
Captcha-bilder må alltid ha alternativer for døvblinde.
### Dekorative bilder
Beskrivelser av disse bildene er ikke nødvendige, men kan gi en viss følelse. Viktigheten av å beskrive disse bildene vil derfor variere fra konteksten. I tillegg er det personlige forskjeller i hvorvidt man ønsker å få en «følelse av en nettside». For å unngå opplesning av disse bildene kan du ha tomme alt-egenskaper, eller ha bildene som bakgrunner med CSS.

**Aldri unngå alt-egenskapen i et img-element, da skjermlesere vil lese opp filnavnet til bildet.**
## Data tables
Det viktigste å huske på med tabeller er at relasjonen mellom innholdet i kolonneoverskrifter, radoverskrifter og cellene under dem skal forklares. Dette gjøres ved å ha gode semantiske tabeller.
### Tips for tabeller
1. Gi navn til tabellene med bruk av caption-elementet.
2. Unngå overskrifter i midten av tabeller.
3. Unngå sammenkoblede celler.
4. Test tabellene med hjelpeverktøy mens du lager dem.

## Iframes
Det er ingenting feil med å bruke iframes, men husk å gi dem titler. Ellers bruker hjelpeverktøyene sidetittlene der innholdet hentes fra. Dette gir brukeren dårlig kontekst.

## Color contrast
[Reglene for kontrast i WCAG 2.2](https://www.w3.org/TR/WCAG22/#contrast-minimum) gjelder for både tekst, [navigasjonselementer og grafiske elementer som er sentrale for innholdet på siden](https://www.w3.org/TR/WCAG22/#non-text-contrast).

For navigasjonselementer gjelder reglene i alle tilstander av elementene. **De trenger derimot ikke å ha kontrast mellom hverandre.** [Tilstandene til elementene som er pålagt etter WCAG 2.2](https://www.w3.org/TR/WCAG22/#content-on-hover-or-focus) er **hover** og **fokus**.

Grafisk innhold som står sammen med annet innhold som forklarer det samme som det grafiske elementet gjør og som følger kravet om kontrast kan feile uten at det gjør noe. For eksempel kan et ikon for å symbolisere «meny» ha lavere kontrast enn tillat dersom det står meny i klartekst i samme element og teksten har høy nok kontrast til bakgrunnen.

### Unntak
1. Dekorative bilder
2. Disabled navigasjonselementer
3. Logoer
4. Innhold der lav kontrast er nødvendig for å forstå meningen med innholdet.

## Multimedia
### Video
- Videoer krever undertekst.
- Transkripsjoner trenger ikke å være kobla til tidslinjen i videoer. Disse er allikevel veldig viktige for døvblinde.
	- Audiodeskriptiv lyd til video er nyttig for å beskrive viktig informasjon om ting som skjer i videoene uten at det er sagt av noen.

Bevegende bakgrunner på nettsider kan gi enkelte brukere kvalme. Derfor bør man unngå å bruke det dersom man kan. Enkelte enheter har også mulighet til å skru av disse funksjonene på systemnivå, noe nettsiden da kan lytte til.

Tegnspråk er ikke nødvendig etter WCAG 2.2, men er nyttig for døve brukere.
### Autoplay
Automatisk avspilling uten brukerkontroller er kun lovlig i 3 sekunder for å oppnå [krav «1.4.2 Audio Control» i WCAG 2.2](https://www.w3.org/TR/WCAG22/#audio-control). Etter dette må det være mulig for brukeren å pause, stoppe eller fjerne innholdet.

> If any audio on a web page plays automatically for more than 3 seconds, either a mechanism is available to pause or stop the audio, or a mechanism is available to control audio volume independently from the overall system volume level.

## Visual flashing effects
For å møte [krav «2.3.1 Three Flashes or Below Threshold» i WCAG 2.2](https://www.w3.org/TR/WCAG22/#three-flashes-or-below-threshold) må du unngå at innhold blinker flere enn tre ganger. Hold deg helst til 0 om du kan.

> Web pages do not contain anything that flashes more than three times in any one second period, or the flash is below the general flash and red flash thresholds.

## Form Labels and Instructions
Labels er påkrevd for brukerinput.

Det samme gjelder for grupper av input-felter. For grupper skal skjermleseren da lese opp både label for gruppa den er i, og feltet brukeren står i.

I tabeller kan du bruker kolonne- og radoverskrifter som label. Pass på at begge aksene blir lest opp riktig.

Ikoner kan brukes som labels og instruksjoner dersom det er tilstrekkelig forståelig.

### Placeholders
Placeholders er ikke gode labels fordi de forsvinner når brukeren legger inn tekst i feltet.

Dersom det er viktig for designet at det ser ut som en placeholder før en bruker interagerer med elementet kan du heller flytte placeholderen fra input-feltet og over teksten som blir skrevet av brukeren. Et eksempel på dette et [tekstfeltene til Google Material versjon 3](https://m3.material.io/components/text-fields/guidelines).

**Placeholders skal nå kontrastkravene til tekst.**

### Instruksjoner
Dersom det er viktige instruksjoner knytta til måten en bruker skal fylle ut et input-felt må dette komme tydelig fram i designet og i kode. Dette bør testes grundig.

## Testing with Mobile Devices
Dette var kun instruksjoner på hvordan man skrur på, og bruker, skjermleser-verktøyene på iOS og Android.

## Concluding remarks
Oppsummering av kurset.
