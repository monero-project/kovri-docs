## Bidragelse

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
- På nuværende tidspunkt har vi ingen tags eftersom vi er i pre-alpha. For nu, kan du basere dit arbejde ud fra master.
- Commit beskeder burde være ordrige som standard, bestående af en kort emne linje (max 50 tegn), en blank linje, og detaljeret forklarende tekst som et seperat afsnit - med mindre titlen alene er forklarende nok. 
- Commit titel burde indeholde data eller et aspekt af projektet. F.eks. "HTTPProxy: implement User-Agent scrubber. Fixes #193." or "Garlic: fix uninitialized padding in ElGamalBlock".
- Hvis en særlig commit referere til et andet problem, venligst tilføj en reference. F.eks. "See #123", or "Fixes #123". This will help us resolve tickets when we merge into ```master```.
- Generelt burde commits være [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) og diffs burde være nemme at læse. Prøv derfor ikke at blande formateringsrettelser med ikke-formateret commits.
- Kroppen af pull requesten burde indeholde en akkurat beskrivelse af hvad opdatering gør og giv begrundelse for denne opdatering (når passende). Du burde inkludere referencer til hvilken som helst diskussion som andre tickets eller chatte på IRC.

## Forslag
For at bidrage med forslag, venligst gennemgå vores [open issues](https://github.com/monero-project/kovri/issues) for eksisterende forslag. Hvis hvad du foreslår ikke er der, så [open a new issue](https://github.com/monero-project/kovri/issues/new).

Selvom vores C4 dikterer at vi merger alting, så spørge vi om du åbner et forslag for følgende grunde:

1. Et forslag åben op for kommunikation
2. Et forslag viser at folk der bidrager respekterer input af alle projekt samarbejdspartnere
3. Et forslag tillader sømløs samarbejdspartnere input i et åben forum
4. Et forslag sparer tid hvis en samarbejdspartner arbejder på en lignende funktion/problem
5. Et forslag forhindrer katastrofer og uheld eller tillader samarbejdspartnere at forberede på katastrofer eller uheld

ved *ikke* at åbne et forslag forhindrer dig *ikke* i at bidrage; vi ville stadig merge hvad du PR - men et forslag er højt anbefalet.

## TODO's
- Gør et hurtigt søg i kodebasen via ```TODO(unassigned):``` og/eller vælg et ticket og start opdatering!
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
- At afhjælpe afhængigheder på nøglepersoner