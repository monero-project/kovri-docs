# Ofte stillede spørgsmål

## indholdsfortegnelse
- Generelle spørgsmål
  - Hvad er Kovri?
  - Hvem udvikler Kovri?
  - Hvordan ville Kovri hjælpe Monero?
  - Hvorfor skulle jeg hente Kovri i stedet for I2P?
  - Hvad gør Kovri, og hvad gør den ikke for dig?
  - Hvornår er alphaen
  - Hvad fokusere udviklingsteamet på lige nu?
  - Hvad er den nuværende brugbarhed af Kovri og hvilken privatliv tilbyder den?
  - Hvordan kan jeg få fat i udviklerne af Kovri?
  - Kovri vs i2pd
  - Hvorfor skulle jeg bruge Kovri i stedet for i2pd
  - Hvad er de største forskelle mellem Kovri og ip2d?
  - Hvorfor forkede i fra i2pd
  - Hvad var de vendepunkter, der førte til forking fra i2pd (og hvorfor er der to i2pd depoter: en på Bitbucket og en på GitHub)?
  - Brug af Kovri
  - Jeg har fundet en sikkerhedsfejl! Jeg har fundet en bug! Hvad gør jeg?
  - Hvorfor viser min log mig en dato/tid forskellig for min tidszone?
  
  ## Generelle spørgsmål
  
  [Kovri](https://getmonero.org/resources/moneropedia/kovri.html) er en gratis, decentraliseret, anonymitetsteknologi udviklet af [Monero](https://getmonero.org).

I øjeblikket baseret på [I2P](https://getmonero.org/resources/moneropedia/i2p.html)'s åbne specifikationer, bruger Kovri både [garlic encryption](https://getmonero.org/resources/moneropedia/garlic-encryption.html) og [garlic routing](https://getmonero.org/resources/moneropedia/garlic-routing.html) for at oprette et privat, beskyttet overlay-netværk over internettet. Dette overlay-netværk giver brugerne evnen til at *effektivt* skjule deres geografiske lokation og internet IP adresse.

Essentielt, *dækker* Kovri en applikations internet traffik for at gøre det anonymt i netværket.

Kovri er en sikkerheds-fokuseret router, der er fuldt kompatibel med I2P netværket. En alpha version af Kovri er i udvikling.

### Hvem udvikler Kovri?
Kovri er et open-source projekt, som betyder at det afhænger af fælleskabets bidrag. De ledende udviklere på dette projekt er [anonimal](https://github.com/anonimal), som du kan stille spørgsmål til via Kovri IRC kanalerne [#kovri](irc://chat.freenode.net/#kovri), [#kovri-dev](irc://chat.freenode.net/#kovri-dev), og hans [Twitter konto](https://twitter.com/whoisanonimal).

Kovri bliver udviklet under paraplyen af  [The Monero Project](https://github.com/monero-project), hvilket er et andet open-source projekt der udvikler [Monero mønten](https://getmonero.org) og [Open Alias](https://openalias.org). Forholdet mellem The Monero Project og Kovri er en gensidig fordel, hvor Kovri søger at integrere sig i Monero-netværket, og Monero leverer en strøm af udviklere og ressourcer til Kovri-udvikling.

### Hvordan ville Kovri hjælpe Monero?
Monero er en sikker, privat, usporlig og fungibel cryptocurrency, der som standard har privatlivets fred, og bruger sådanne teknologier som stealth adresser, RingCT og ring signaturer for at skjule modtager, beløb og afsender henholdsvis. Nogle potentielle svagheder i Monero lækker IP-adressen, der sender en transaktions- og korrelationsangreb.

Kovri vil blive implementeret i den officielle Monero tegnebog, så alle transaktioner vil blive sendt via det Kovri anonyme netværk, der skjuler den IP-adresse, hvorfra transaktionen stammer fra. I fremtiden vil alle transaktioner blive dirigeret gennem Kovri som standard, selvom downloading af blockchainen stadig vil være gennem clearnettet for effektivitet.

### Hvorfor skulle jeg bruge Kovri i stedet for I2P?
[I2P] (https://geti2p.net) er et godt projekt, men der var et par ting, som vi følte var nødvendige for at tilpasse teknologien til Monero. For det første er I2P udviklet i Java, og vi mente, at udviklingen af en router i C++ ville hjælpe koden med at være hurtig og let.

For det andet, mens Java-implementeringen af I2P er fantastisk, kommer den med en masse ekstra funktioner, som vi ikke føler er nødvendige for, at Monero-applikationen kan bruges. Så vi besluttede at starte fra bunden og lave en router, der KUN er en router. Denne bare-ben-tilgang er perfekt til Monero, og er også gode nyheder for andre, der ønsker at lave I2P-applikationer. De har mulighed for at bruge en letvægtsrouter uden alt overskud, mens andre brugere der har brug for disse ekstrafunktioner, vil kunne bruge Java-implementeringen. Det er en win-win for alle.

### Hvad gør Kovri nu?
- Tillader dig at blive en node på I2P netværket
- Skjuler din fysiske lokation fra siden du besøger
- Anonymiserer dig på IRC og tillader anonym Email
- Tillader dig at hoste anonyme hjemmesider eller servicer
- Giver finansiering til udviklere, hackere, forskere via FFS og HackerOne
- Målsætninger for streng kodekvalitet og dev standarder

### hvilke udviklinger har Kovri planer for til fremtiden?
- Behandling af Monero transaktioner over I2P
- GUI for forbedret konfiguration og brugbarhed
- Biblioteks API og bindinger til eksterne apps/biblioteker
- Firefox udvidelse for nemt at få adgang til hjemmesider
- Hjemmeside udvikling (getkovri.org/kovri.i2p)
- Omfattende dokumentation fra ELI5 til udvikler

### Hvad gør Kovri ikke for dig?
- Ofrer din sikkerhed for bagliggende motiver
- Give en indviklet, smertefuld webbrugerflade
- Kræver myndigheder for netværk
- Adgang til internet hjemmesider via en "outproxy"
- Kræver en performance-dræbende Java VM
- Går med din hund eller favorit kæledyr og betaler dine skatter

### Hvad er det nuværende stadie af Kovri?
Kovri er i aktiv udvikling og er i øjeblikket i en Alpha fase. Det er * ikke * endnu integreret med Monero, men udover flere kerneegenskaber udvikler vi en [client](https://github.com/monero-project/kovri/issues/351) og [core](https://github.com/monero-project/kovri/issues/350) API for monero, og andre applikationer som de kan bruge

Men bare fordi vi er i Alpha betyder det ikke, at du ikke kan bruge Kovri. I øjeblikket kan du bruge Kovri til at oprette forbindelse til (og deltage) i I2P-netværket, browse eepsites, oprette forbindelse til IRC og køre klient -og servertunneler.

### Hvornår er alphaen?
En alpha release er i værkerne, der skal udgives (vi håber !!) inden udgangen af 2017. Når vi er i alfa, begynder arbejdet straks på beta-udgivelsen, hvilket kræver: en fuldt implementeret API, opløsning til vigtige kvalitetssikringsproblemer og forskellige fejlrettelser.
### Hvad fokusere udviklingsteamet på lige nu?
Lige nu fokuserer vi på alting der står på vores [issues tracker](https://github.com/monero-project/kovri/issues/). De dækker hovedparten af hvad vi skal afslutte før vi udgiver en officiel alpha release.

### Hvad er den nuværende brugbarhed af Kovri og hvilken privatliv tilbyder den?
Kovri er anvendelig i det omfang, hvad `./kovri --help` har at tilbyde. Kovri har i øjeblikket ingen interaktion med Monero. Med hensyn til privatlivets fred har vi etableret mange sikkerhedsproblemer siden starten, men vi beder dig om at huske på, at vi stadig er i Alpha.

Der er stadig meget kode at dække, så forvent ikke en stærk garanti for anonymitet som med Tor, eller Java I2P. Disse projekter har 10+ års forskning og implementeringserfaring, og vi er lige begyndt.

Du er velkommen til at spille rollen som udvikler og eksperimentere med Kovri, men kun hvis du ** ikke ** sætter dig selv i fare, da der altid er risiko for mulig deanonymisering på grund af at vi er i Alpha ( dette er ikke unikt for Kovri).

### Hvordan kan jeg få fat i udviklerne af Kovri?
Læs vores [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Kovri vs i2pd

### Why should I use Kovri instead of i2pd?

- Sikkerhed: vores fokus er på at sikre softwaren; ikke [at skynde os at blive færdige](https://github.com/monero-project/kovri/issues/65) bare for at have en release
- Kvalitet; du støtter bestræbelser på at sikre en kvalitets kodebase, der vil stå tidstesten. Dette omfatter alle aspekter af kodevedligeholdenhed
- Monero: du vil støtte en krypto-valuta, der holder stærkt fat i konsevering af folks privatliv og anonymitet samtidig med at du øger både dit privatliv og din anonymitet

### Hvad er de største forskelle mellem Kovri og ip2d?

- - Vi leverer et [Forum Funding System] (https://forum.getmonero.org/8/funding-required) for funktioner / udvikling.
- Vi fokuserer på at skabe en ["sikker som standard"](http://www.openbsd.org/security.html), let vedligeholdelig, mere sandsynligt at blive revideret I2P router. Dette vil medføre omkostningerne ved at droppe mindre anvendte funktioner, som findes i de andre routere, men kernefunktionalitet og en API vil være helt intakte. Ved at oprette en mindre, effektiv "bare-bens" router, vil vi give udviklere og forskere mere tid til sikkerhedsrevision og mere tid til at stille spørgsmålstegn ved I2P-design og specifikationer.
- Vi fokuserer på at implementere en intuitivt, udviklervenligt API til enhver applikation til at oprette forbindelse til og bruge I2P-netværket; dette inkluderer monero.
- Vi giver både slutbrugere og udviklere en [kvalitetssikring](https://github.com/monero-project/kovri/issues/58) og [udviklingsmodel](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/contributing.md) for at give bedre software til alle.
- Vi vil implementere alternative reseeding muligheder, så brugerne kan bruge [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) i stedet for HTTPS som reseed.
- Vi vil implementere udvidet funktionalitet * (skjult tilstand + deaktiveret indgående) * for at give anonymitet for dem, der bor i lande med ekstreme forhold eller dem, der firewalles af carrier-grade NAT eller DS-Lite.
- Vi vil altid skabe et velkomment miljø for samarbejde.

### Hvorfor forkede i fra i2pd

Vi forkede på baggrund af flere grunde

- - Vi ønskede en robust, sikker og levedygtig C ++-implementering af I2P-netværket; og i2pd leverede ikke
- Vi ønskede et positivt fællesskab, der opfordrede til samarbejde til forbedring af softwaren; ikke negativ, narcissistisk ære
- Vi ønskede en ledende udvikler, der kunne lede. ikke en der ville ignorere anmodninger om ansvarlig afsløring eller halen mellem benene og løbe, når de står overfor samarbejdskonflikt

### Hvad var de vendepunkter, der førte til forking fra i2pd (og hvorfor er der to i2pd depoter: en på Bitbucket og en på GitHub)?

* Så begyndte dramaet af i2pd *.

I begyndelsen / midten af 2015 skød en af udviklerne med push privilegier på GitHub en commit (s), som i2pds første forfatter ikke kunne lide. I stedet for at arbejde sammen om at løse problemet, tog forfatteren i2pd til Bitbucket, og slettede ** alle ** eksisterende git historik, og gjorde sig selv den eneste bidragyder af softwaren. Han lovede da aldrig at vende tilbage til Irc2P.

Disse handlinger fornærmede mange i I2P-fællesskabet, herunder udviklerne, og afsluttede næsten C ++-projektet.

I efteråret 2015 kom anonimal, som ikke ville se alles arbejde gå i spilde, og genoplivede projektet gennem egne og igangværende udvikling. Der blev derefter givet en åben invitation til alle de resterende aktive udviklere til at mødes og diskutere i2pds fremtid. I2pds første forfatter viste sig aldrig, men mødet viste tilsyneladende at rasle i2pd's fjer til det punkt, hvor han [modangreb]https://github.com/PurpleI2P/i2pd/issues/279) og begyndte at arbejde på GitHub igen - men denne gang inden for en `` `openssl``` branch (som viste sig at være Bitbucket-depotet) i stedet for det fællesskabs-kørte `` `master``` branch.

Da denne slags uregelmæssige adfærd ville kun skade I2P-netværket og projektet som helhed, de tilbageværende udviklere fortsatte med at have [flere vigtige møder] (https://github.com/monero-project/kovri/issues/47) og satte fundamentet for hvad der nu er Kovri.

## Brug af Kovri

### Jeg har fundet en sikkerhedsfejl! Jeg har fundet en fejl! Hvad gør jeg?
- Sikkerhedsfejle: læs vores [README](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs: Læs vores [Udviklerguide](https://github.com/monero-project/kovri-docs/blob/master/i18n/da/developer_guide.md)
  
### Hvorfor viser min log mig en dato/tid forskellig for min tidszone?
Logfiler registreres i UTC for at beskytte dit privatliv. Ved at bruge UTC har du bedre mulighed for at uploade logs, til at dele dem med udviklere eller fællesskabet uden at påvirke din anonymitet.
