# Domande Frequenti (e risposte)

## Cos'è Kovri?
Kovri è una sicura, privata e intracciabile implementazione router in C++ della rete anonima I2P. Da un fork di i2pd, Kovri è diventato un'unica implementazione I2P, attivamente sviluppata e guidata dalla community, con tanti miglioramenti, fix di sicurezza e nuove caratteristiche rispetto al suo predecessore.

Leggi di più su Kovri nella [Moneropedia](https://getmonero.org/resources/moneropedia/kovri).

## Qual è lo stato attuale di Kovri?
Kovri è attivamente sviluppato e correntemente nella fase Alpha. Kovri *non* è ancora integrato con Monero ma, oltre a varie features principali, stiamo sviluppando un [client](https://github.com/monero-project/kovri/issues/351) e un [core](https://github.com/monero-project/kovri/issues/350) API da usare per Monero e altre applicazioni.

Correntemente, puoi usare Kovri per connetterti (e partecipare) al network I2P: naviga eepsites, connettiti a IRC, apri un client e tunnel servers.

## Quando sarà la vostra prima release?
Una release alpha è prevista per inizio 2017. Quando la qualità avrà raggiunto un livello sufficente alto e l'API sarà completamente implementata, Kovri diventerà un beta software.

## Perchè i miei log mostrano una data/ora diversa dalla mia timezone?
I logs sono registrati in UTC per proteggere la tua privacy. Usando UTC, puoi caricare file di log da condividere con gli sviluppatori della community senza compromettere il tuo anonimato.

## Su cosa si sta concentrando attualmente il team di sviluppatori?
Correntemente, ci stiamo concentrando su tutto ciò che è listato nel nostro [issues tracker](https://github.com/monero-project/kovri/issues/). Copre molto di quello che dobbiamo finire prima di una release ufficiale (alpha, beta o maggiore).

## Kovri è usabile, parzialmente usabile o non è raccomandato l'utilizzo per forte privacy al momento?
Kovri può essere utilizzato secondo quanto il comando ```./kovri --help``` ha da offire. Kovri non ha attualmente alcuna interazione con Monero. Riguardo alla privacy, abbiamo sistemato molti problemi di sicurezza fin dall'inizio ma siamo ancora in Alpha.

C'è ancora molto codice da coprire quindi non aspettarti una forte garanzia d'anonimato come con tor o persino java I2P. Questi progetti hanno 10+ anni di ricerche e implementazioni - e noi abbiamo appena iniziato.

Sentiti libero di giocare il ruolo dello sviluppatore e sperimentare/giocare con Kovri ma solo se **non** essere anonimo non ti mette in pericolo - c'è sempre il rischio di una possibile deanonimizzazione a causa dell'essere in Alpha (questo non vale solo per Kovri).

## Informazioni per contattare Kovri?
leggi il nostro [README](https://github.com/monero-project/kovri/blob/master/README.md).

## Perchè dovrei usare Kovri invece di i2pd?
- Sicurezza: il nostro obbiettivo è quello di rendere il nostro software sicuro; non di [fare le cose frettolosamente](https://github.com/monero-project/kovri/issues/65) solo per fare uscire una release
- Qualità: stai supportando gli sforzi per assicurare un codebase di qualità che supererà il test del tempo. Questo include tutti gli aspetti della mantenibilità del codice
- Monero: supporterai una cryptomoneta che fa della preservazione della privacy e dell'anonimità un vanto, incrementandole entrambe

## Quali sono le più grandi differenze tra Kovri e i2pd?

- Abbiamo un [Forum Funding System](https://forum.getmonero.org/8/funding-required) per features/sviluppo.
- Siamo concentrati nella creazione di un router I2P ["sicuro di default"](http://www.openbsd.org/security.html), facilmente mantenibile con più possibilità di reviews. Questo a costo di abbandonare le funzionalità meno utilizzate in altri routers, ma le funzionalità principali e le API rimarranno pienamente intatte. Creando un router più piccolo, efficente ed essenziale, forniremo a sviluppatori e ricercatori più tempo per audit di sicurezza e per mettere in discussione il design I2P e le sue specifiche.
- Siamo concentrati nell'implementare un'intuitiva, developer-friendly API per qualsiasi applicazione per connettersi e usare il network I2P, questo include Monero.
- Forniamo sia agli utenti finali che agli sviluppatori una [garanzia di qualità](https://github.com/monero-project/kovri/issues/58) e un [modello di sviluppo](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/contributing.md) in modo da fornire un software migliore a tutti/e.
- implementeremo un'opzione di reseeding alternativa così gli utenti potranno utilizzare [Pluggable Transports](https://www.torproject.org/docs/pluggable-transports.html.en) invece di HTTPS per il reseeding.
- Implementeremo funzionalità estese *(modalità nascosta + inbound disabilitato)* per fornire anonimità a coloro che vivono in nazioni con condizioni estreme o per chi è sotto firewall da carrier-grade NAT o DS-Lite.
- Creeremo sempre un ambiente di collaborazione amichevole.
- Daremo sempre ascolto ai tuoi feedback e faremo del nostro meglio per migliorare Kovri!

## Perchè vi siete separati da i2pd?

Abbiamo eseguito una fork per almeno questi motivi:

- Volevamo una robusta, sicura e viabile implementazione C++ del network I2P; e i2pd non la forniva
- Volevamo una community positiva in grado di incoraggiare collaborazione per il miglioramento del software; non negativa, narcisitica, in cerca di gloria
- Volevamo un capo sviluppatore che sapesse comandare; non qualcuno che ignorasse richieste di divulgazione responsabile o che  rifiuti il confronto in caso di conflitti con i collaboratori

## Quali sono stati i motivi principali che hanno portato a "forkare" da i2ps (e perchè ci sono due repository: una su Bitbucket e l'altra su GitHub)?

*Così cominciò il dramma i2pd*.

A inizio/metà 2015, uno degli sviluppatori con privilegi nella repository di GitHub ha "spinto" un "commit" che non è piaciuto al primo autore di i2pd. Invece di lavorare insieme per risolvere il problema, detto autore trasferì i2pd su Bitbucket, eliminò **tutta** la cronologia di git, e si è nominato unico 'contributore' del software. Promise poi che non sarebbe mai tornato su Irc2P.

Queste azioni hanno offeso molti nella community di I2P, inclusi gli sviluppatori, e quasi mise fine al progetto C++.

Nella primavera del 2015 arrivò anonimal, che non volendo vedere il lavoro di tutti venir sprecato, ha ravvivato il progetto tramite contributi propri. Venne mandato un invito a tutti gli sviluppatori attivi rimasti per riunirsi e discutere il futuro di i2pd. Il primo autore di i2pd non si è mai presentato, ma l'atto di riunirsi ha scrollato la ruggine dalle ali di i2pd abbastanza da farlo [ritrattare](https://github.com/PurpleI2P/i2pd/issues/279) e ricominciare a collaborare di nuovo su GitHub - ma questa volta con un ramo ```openssl``` (che si è poi rivelato essere la repository di Bitbucket) invece del ramo ```master``` guidato dalla community.

Capendo che questo comportamento avrebe solo fatto male al network I2P e all'intero progetto, gli sviluppatori rimasti hanno continuato a riunirsi in [vari meeting importanti](https://github.com/monero-project/kovri/issues/47) costruendo le fondamenta di quello che adesso è Kovri.

## Ho trovato una vulnerabilità! Ho trovato un bug! Cosa devo fare?
- Vulnerabilità: vedi il nostro [LEGGIMI](https://github.com/monero-project/kovri/blob/master/README.md)
- Bugs: leggi la nostra [Guida per sviluppatori](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/developer_guide.md)
