## Bidrag

## Kvalitets sikring
- Se vores [Kvalitets sikring](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/quality.md) 
Guide til at få en idé om foreslået arbejdsgang

## Overholdelse
- Vi sigter efter en komplet C++11/14 overholdelse; du velkommen til at bruge denne til din fordele med dit arbejde
- Det er også klart anbefalet at bruge standard biblioteket og afhængigheds biblioteker når muligt

## Sendelse af dit arbejde
For at bidrage med dit arbejde, venligst fortsæt med følgende:

1. Fork Kovri
2. Læs vores [style guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/style.md)
3. Opret en [topic branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
4. [**Signer**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) dine commit(s)
5. Send en pull-request til branch ```master```
- På nuværende tidspunkt har vi ingen tags eftersom vi er i Alpha. For nu, kan du basere dit arbejde ud fra master.
- Commit beskeder burde være ordrige som standard, bestående af en kort emne linje (max 50 tegn), en blank linje, og detaljeret forklarende tekst som et seperat afsnit - med mindre titlen alene er forklarende nok. 
- Commit titel burde indeholde data eller et aspekt af projektet. F.eks. "HTTPProxy: implement User-Agent scrubber. Fixes #193." or "Garlic: fix uninitialized padding in ElGamalBlock".
- Hvis en særlig commit referere til et andet problem, venligst tilføj en reference. F.eks. "See #123", eller "Fixes #123". Dette ville hjælpe os med at løse tickets når vi merger ind i  ```master```.
- Generelt burde commits være [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) og diffs burde være nemme at læse. Prøv derfor ikke at blande formateringsrettelser med ikke-formateret commits.
- Kroppen af pull requesten burde indeholde en akkurat beskrivelse af hvad opdatering gør og giv begrundelse for denne opdatering (når passende). Du burde inkludere referencer til hvilken som helst diskussion som andre tickets eller chatte på IRC.

## Oplæg
For at bidrage med oplæg, venligst gennemgå vores [open issues](https://github.com/monero-project/kovri/issues) for eksisterende oplæg. Hvis hvad du foreslår ikke er der, så [open a new issue](https://github.com/monero-project/kovri/issues/new).

Selvom vores C4 dikterer at vi merger alting, så spørge vi om du åbner et oplæg for følgende grunde:

1. Et oplæg åbner op for kommunikation
2. Et oplæg viser at folk der bidrager respekterer input af alle projekt samarbejdspartnere
3. Et oplæg tillader sømløs samarbejdspartnere input i et åben forum
4. Et oplæg sparer tid hvis en samarbejdspartner arbejder på en lignende funktion/problem
5. Et oplæg forhindrer katastrofer og uheld eller tillader samarbejdspartnere at forberede på katastrofer eller uheld

ved *ikke* at åbne et oplæg forhindrer dig *ikke* i at bidrage; vi ville stadig merge hvad du PR - men et oplæg er højt anbefalet.

## TODO's
- Gør et hurtigt søg i kodebasen via ```TODO(unassigned):``` og/eller vælg et ticket og påbegynd patching!
- Hvis du oprettet en TODO, tildel det til dig selv eller skriv ind ```TODO(unassigned):```

# [Code of Conduct (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licens

Copyright (c) 2009-2015 Pieter Hintjens.

This Specification is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This Specification is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see <http://www.gnu.org/licenses>.

## Sprog

nøgleordene "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" i dette dokument fortolkes som beskrevet i RFC 2119.

## Mål

C4 er ment til at give en genbrugelig optimal samarbejdsmodel til open source software projekter. Den har disse specifikke mål:

- For at maksimere omfanget og mangfoldigheden af fælleskabet omkring et projekt, ved at reducere friktionen for nye bidragende folk og skabe en målrettet deltagelsesmodel med stærkt positivt feedback;
- At afhjælpe afhængigheder på nøglepersoner ved at adskille forskellige færdigheder, så der er en større kompetencegruppe i et hvilket som helst ønsket domæne;
- At give projektet mulighed for at udvikle sig hurtigere og mere præcist ved at øge beslutningsprocessens mangfoldighed;
- At understøtte den naturlige livscyklus for projektversioner fra eksperimentelle til stabile ved at tillade sikker eksperimentering, hurtige fejl og isolering af stabil kode;
- At reducere projektregistrets interne kompleksitet, hvilket gør det lettere for bidragydere at deltage og reducere fejlområdet;
- At håndhæve kollektiv ejerskab af projektet, hvilket øger økonomisk incitament til bidragydere og reducerer risikoen for kapring af fjendtlige enheder.

## Design

### indledende

- Projektet skal bruge git-distribueret revisionskontrolsystem.
- Projektet skal hostes på github.com eller tilsvarende, her kaldt "platformen".
- Projektet skal bruge platformsspørgsmålet.
- Projektet skal have tydeligt dokumenterede retningslinjer for kodestil.
- En "Bidragsyder" er en person der ønsker at give en patch, der er et sæt af commits der løser det klart identificerede problem.
- En "Vedligeholder" er en person, der merger patches til projektet. Vedligeholdere er ikke udviklere; deres job er at håndhæve processen.
- Bidragsydere MÅ IKKE have commit adgang til depotet med mindre de også er vedligeholdere.
- Vedligeholder SKAL have commit adgang til depotet.
- Alle, uden forskel eller diskrimination , SKAL have lige rettigheder til at blive en bidragsyder under betingelserne af denne kontrakt.

### Licens og Ejerskab
- Projektet SKAL bruge en share-alike licens, dette kunne være nogle ligesom GPLv3 eller en variant deraf (LGPL, AGPL), eller MPlv2. 
- Alle bidrag til projektets source kode ("patches") SKAL bruge den samme licens som projektet.
- Alle patches er ejet af deres forfattere. Der SKALL IKKE være nogle som helst ophavsret tildelingsproces.
- Ophavsretten i projektet SKAL ejes kollektivt af alle dens bidragydere.
- Hver bidragyder skal være ansvarlig for at identificere sig i projektbidragslisten.

### Patch krav

- Vedligeholdere og bidragydere SKAL have en Platform konto og skal bruge deres rigtige navne eller et velkendt alias.
- En patch skal være et minimalt og præcist svar på nøjagtigt et identificeret og aftalt problem.
- En patch skal overholde kode stilens retningslinjer af projektet, hvis disse er defineret.
- En patch skal overholde retningslinjerne "Evolution of Public Contracts" som defineret nedenfor.
- En patch SKAL IKKE indeholde ikke-trivial kode fra andre projekter, medmindre bidraggiveren er den oprindelige forfatter af den pågældende kode.
En patch SKAL compile rent og bestå projektets selvtest på i det mindste principmålplattformen.
- En patch commit besked BURDE bestå af en enkelt kort (mindre end 50 tegn) linje der opsummerer ændringen, eventuelt efterfulgt af en tom linje og derefter en mere grundig beskrivelse.
En "Correct Patch" er en der opfylder overstående krav.

### Udviklingsproces

- Ændring på projektet SKAL styres af mønsteret af at nøjagtigt identificere problemer og anvende minimal, præcise løsninger på disse problemer.
- For at anmode om ændringer, skal en bruger logge et problem på projektets Platform issue tracker.
- Brugeren eller bidragsgiveren SKAL skrive problemet ved at beskrive det problem, de står over for eller observerer.
- Brugeren eller bidragsgiveren SKAL søge konsensus om nøjagtigheden af deres observation og værdien af at løse problemet.
- Brugere MÅ IKKE logge funktionsanmodninger, ideer, oplæg eller løsninger til problemer, der ikke er eksplicit dokumenteret og bevisligt.
- Således SKAL projektets udgivelseshistorik være en liste over meningsfulde problemer, der er logget og løst.
- For at arbejde på et problem, SKAL en bidragsyder forke projektets depot og arbejde på deres eget forkede depot.
- For at indsende en patch skal en bidragyder oprette en platform pull request tilbage til projektet.
- En bidragsyder SKAL IKKE commite ændringer direkte til projektet.
- Hvis platformen implementerer pull request som et problem, kan en bidragsyder sende en pull request direkte uden at logge på et særskilt problem.
- For at diskutere en patch kan folk kommentere på Platform pull request, på commit eller et andet sted.
- For at acceptere eller afvise en patch, skal en vedligeholder bruge platformens interface.
- Vedligeholdere BURDE IKKE merge deres egne patches undtagen i usædvanlige tilfælde, som f.eks. Ikke-respons fra andre vedligeholdere i længere tid (mere end 1-2 dage).
- Vedligeholdere SKAL IKKE foretage værdidomme på korrekte patches.
- Vedligeholdere SKAL merge correct patches fra andre bidragsydere hurtigt.
- Bidragsyderen MÅ tagge et problem som "ready" efter han har lavet en pull request for problemet.
- Den bruger, der oprettede et problem, skal lukke problemet efter at have kontrolleret patchen, lykkes.
- Vedligeholdere SKAL bede om forbedringer af ukorrekte patches og BURDE afvise ukorrekte patches, hvis bidragsyderen ikke reagerer konstruktivt.
- Enhver bidragyder, der har værdiafgørelser på en korrekt patch, BURDE udtrykke disse via deres egne patches.
- Vedligeholdere MÅ begå ændringer til non-source dokumentation direkte til projektet

### Oprettelse af stabile udgivelser

- Projektet SKAL have en branch ("master") der altid indeholder den seneste in-progress version og altid BURDE kunne bygges.
- Projektet SKAL IKKE bruge topic branches for nogen som helst grund. Personlige forks MÅ bruge topic branches.
-For at lave en stabil udgivelse SKAL nogle forke depotet ved at kopiere det og blive vedligeholdere af dette depot.
- Forking af et projekt for stabilisering MÅ ske ensidigt og uden samtykke fra projektansvarlige.
- Et stabiliseringsprojekt SKAL opretholdes i samme proces som hovedprojektet.
- En patch til et projekt der er deklarerert "stable" SKAL være ledsaget af en reproducerbar test sag.

### Evolution af offentlige kontrakter

- Alle offentlige kontrakter (API'er eller protokoller) SKAL dokumenteres.
- Alle offentlige kontrakter BURDE have plads til udvidelse og eksperimentering.
- En patch, der ændrer en stabil offentlig kontrakt, må ikke bryde eksisterende applikationer, medmindre der er tvingende konsensus om værdien af 
at gøre dette.
- Et program, der introducerer nye funktioner til en offentlig kontrakt, BURDE gøre det ved at bruge nye navne.
- Gamle navne SKAL udlægges systematisk, ved at markere nye navne som "eksperimentelle" indtil de er stabile og derefter markere de gamle navne som "afskrevet".
- Når der er tilstrækkelig tid, skal gamle udskrevne navne mærkes "arv" og fjernes efterhånden.
- Gamle navne MÅ IKKE genbruges af nye funktioner.
- Når gamle navne fjernes, skal deres implementeringer fremkalde en undtagelse (påstand), hvis de anvendes af applikationer.

### Projekt Administration

- Projekt grundlæggerne SKAL opføre sig som administratorer for at styre sæt af projekt vedligeholdere.
- Administratorer SKAL sikre deres egen succession over tid ved at fremme de mest effektive vedligeholdere.
- En ny bidragsyder der laver en correct patch SKAL være inviteret til at blive en vedligeholder.
- Administratorer KAN fjerne vedligeholdere, der er inaktive i længere tid, eller som gentagne gange undlader at anvende denne proces nøjagtigt.
- Administratorer skal blokere eller forbyde "dårlige aktører", der forårsager stress og smerte for andre i projektet. Dette skal ske efter offentlig diskussion, med en chance for alle parter at tale. En dårlig aktør er en person, der gentagne gange ignorerer projektets regler og kultur, som er unødvendigt argumenterende eller fjendtligt, eller som er offensiv, og som ikke er i stand til selvkorrekt deres adfærd, når de bliver bedt om det af andre.

# Governance Process

![Governance Process](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
