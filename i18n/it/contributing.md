## Garanzia di qualità
- Leggi [Quality Assurance](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/quality.md) per farti un'idea riguardo le nostre attività.

## Conformità
- Puntiamo alla completa conformità con C++11/14; utilizzalo liberamente per svolgere il tuo lavoro.
- È altamente consigliato l'utilizzo delle librerie standard e delle relative dipendenze quando possibile.

## Modalità di invio del tuo lavoro
Per inviare i tuoi contributi, ti chiediamo di procedere con la seguente modalità:

1. Fork Kovri
2. Leggi la nostra [style guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/style.md)
3. Crea un [topic branch](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
4. [**Firma**](https://git-scm.com/book/en/v2/Git-Tools-Signing-Your-Work) i tuoi commit.
5. Invia una pull-request al branch ```master```
   - Poichè siamo in una fase pre-alfa non abbiamo tag. Per il momento, puoi sviluppare il tuo lavoro al di fuori del master.
   - I commit devono essere verbose di default, costituiti da una breve spiegazione (50 caratteri al massimo), una riga vuota, e una spiegazione dettagliata in paragrafi separati, a meno che il titolo stesso non sia già chiaro di per sé.
   - Il titolo del commit dovrebbe iniziare con la categoria o l'aspetto del progetto. Ad esempio, "HTTPProxy: implementazione dello User-Agent scrubber. Fixes #193." oppure "Garlic: fix dell'errore di avvio del padding nel ElGamalBlock".
   - Aggiungi un riferimento nel caso in cui un commit faccia riferimento ad un altro problema. Ad esempio "Vedi #123", or "Fix #123". Questo ci aiuterà a risolvere i ticket quando arriveranno in ```master```.
   - In generale, i commits devono essere [atomic](https://en.wikipedia.org/wiki/Atomic_commit#Atomic_commit_convention) e i diffs devono essere di facile lettura. Per questo motivo, ti chiediamo di non mischiare fix formattati con commit non formattati.
   - Il corpo della richiesta pull dovrebbe contenere una descrizione dettagliata del funzionamento della specifica patch e della motivazione/giustificazione per la sua introduzione (se necessaria). Dovresti includere i riferimenti relativi a qualsiasi discussione come altri ticket o chat in IRC.

## Proposte
Prima di inviare una proposta fai riferimento a [issue aperte](https://github.com/monero-project/kovri/issues) per controllare se sia già presente. Nel caso in cui non ci sia procedi pure ad [aprirne una nuova](https://github.com/monero-project/kovri/issues/new).

Nonostante i nostri dettami C4 che prevedono di unificare il tutto, ti chiediamo di iviare una proposta per i motivi seguenti:

1. Una proposta apre alla comunicazione.
2. Una proposta mostra rispetto per il lavoro svolto dagli altri contributori.
3. Una proposta permette di avere soluzione di continuità delle differenti modifiche in maniera accessibile.
4. Una proposta fa risparmiare tempo ad un altro collaboratore che si sta occupando della medesima feature o del medesimo fix. 
5. Una proposta evita catastrofi e contrattempi oppure prepara tutti i collaboratori a catastrofi e contrattempi.
*Non* aprire una proposta *non* ti impedirà di contribuire; procederemo comunque al merge di ciò che hai prodotto - ma, in ogni caso, una proposta è altamente consigliata.

## TODO's
- Fai una veloce ricerca nel codebase per ```TODO(unassigned):```, scegli un ticket e inizia a patchare!
- Se crei un TODO, comincia a lavorarci tu oppure scrivi ```TODO(unassigned):```

# [Code of Conduct (22/C4.1)](http://rfc.zeromq.org/spec:22)

## Licenza

Copyright (c) 2009-2015 Pieter Hintjens.

Questo Documento è considerato software libero; è possibile diffonderlo e modificarlo secondo i termini della GNU General Public License pubblicata dalla Free Software Foundation; sia la versione 3 che le precedenti (a propria discrezione).

Questo Documento è distributito con la speranza che sia utile, ma SENZA GARANZIA ALCUNA; privo anche della garanzia implicita di COMMERCIABILITA' o di IDONEITA' AD UN PARTICOLARE SCOPO. Consulta la GNU (General Public License) per maggiori dettagli.

Dovresti ricevere una copia della GNU (General Public License) insieme a questo prodotto; in caso contrario, consulta <http://www.gnu.org/licenses>.

## Scelta di linguaggio

Le parole chiave "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", e "OPTIONAL" sono da interpretare come descritto nel RFC 2119 (fai riferimento alla versione in inglese di questo documento).

## Obiettivi

C4 ha lo scopo di fornire un modello di collaborazione ottimale utilizzabile nei progetti open source. Gli obiettivi specifici sono:

- Massimizzare la scalarità e la diversificazione della comunità che partecipa ad un progetto, smorzando l'attrito coi nuovi Collaboratori e creando un modello di partecipazione di scala con forti feedback positivi;
- Ridurre la dipendenza da invidui chiave separando le competenze in maniera tale da avere il più ampio pool di competenze possibile in ogni ambito richiesto;
- Permettere di sviluppare il progetto più rapidamente e in maniera più efficace, aumentando la diversità del processo decisionale;
- Gestire il naturale ciclo di vita delle differenti versioni del progetto, da sperimentale a stabile, consentendo una sperimentazione sicura, una rapida individuazione dell'errore e l'isolamento del codice stabile. 
- Ridurre la complessità delle repository del progetto, semplificando la partecipazione dei contributori e riducendo la possibilità di errore;
- Rafforzare il concetto di proprietà collettiva, che aumenta l'incentivo economico e riduce la possibilità di distruzione da parte di entità ostili.

## Design

### Preliminari

- Il progetto DEVE utilizzare il sistema di revisione di git.
- Il progetto DEVE essere caricato su github, o altra piattaforma equivalente.
- Il progetto DEVE utilizzare il Platform issue tracker.
- Il progetto DEVE avere chiaramente espresse le linee guida del codice.
- Il "Contributore" è una persona che vuole inviare una patch, un set di commit volti a risolvere un problema chiaramente identificato.
- Un "Manutentore" è una persona che si occupa del merge delle patch. I Manutentori non sono sviluppatori; il loro compito è di rafforzare il processo.
- I Contributori NON DEVONO avere accesso alle repository, a meno che non siano anche Manutentori.
- I Manutentori DEVONO avere il commit di accesso alle repository.
- Tutti, senza alcuna discriminazione o distinzione, hanno uguale diritto di diventare Contributori secondo i termini di questo contratto.

### Licenza e proprietà

- Il progetto DEVE utilizzare una share-alike license, come la GPLv3 o una variante di questa (LGPL, AGPL), oppure la MPLv2.
- Tutti i Contributori operanti sul codice sorgente del progetto DEVONO utilizzare la medesima licenza.
- Tutte le patch sono di proprietà degli autori. NON DEVE esserci alcuna assegnazione di copyright.
- I copyright del progetto DEVONO essere posseduti da tutti i contributori in maniera collettiva.
- Ogni contributore DEVE identificarsi all'interno della lista Contributori.

### Requisiti delle patch

- Mantenitori e Contributori DEVONO avere una account Platform e devono utilizzare i loro nomi reali oppure degli alias ben conosciuti.
- La patch DEVE essere una risposta minimale ed accurata al problema identificato.
- Il codice della patch DEVE attenersi alle linee guida del progetto, nel caso queste siano espresse.
- La patch DEVE attenersi alle linee guida dell'"Evoluzione dei Public Contract" definite qui sotto.
- La patch NON DEVE contenere porzioni di codice di altri progetti, eccezione fatta nel caso il Contributore ne sia l'autore originale.
- La patch DEVE compilarsi in maniera pulita e superare il project self-tests almeno nella target-platform principale.
- Il messaggio del commit DEVE essere costituito da un breve commento (massimo di 50 caratteri) che riassume la modifica, con la possibilità di aggiungere una spiegazione più approfondita preceduta da una linea vuota. 
- La "patch perfetta" è quella che risponde a tutti i requisiti precedenti.

### Processo di sviluppo

- I cambiamenti al progetto DEVONO essere guidati con l'obiettivo di una precisa identificazione dei problemi e con la scelta di soluzioni minimali ed accurate.
- Per richiedere un cambiamento, l'utente DEVE aprire un log del problema nell'apposita Platform.
- L'utente o il Contributore DEVE cercare il consenso altrui attraverso una accurata osservazione e valutazione della modalità di risoluzione del problema.
- L'utente o il Contributore DEVONO descrivere il problema che hanno osservato.
- Gli utenti NON DEVONO aprire log per richieste di funzionalità, suggerimenti, idee o soluzioni a problemi che non sono esplicitamente documentati e provati.
- In questo modo la release history DEVE essere una lista di log giustificati e risolti.
- Per lavorare alla risoluzione di un problema, il Contributore DEVE fare un fork alla repository e quindi lavorare su quella repository.
- Per inviare una patch, il Contributore DEVE creare una Platform pull request verso il progetto principale.
- Il Contributore NON DEVE inviare commit di cambiamento direttamente nel progetto principale.
- Se la Platform implementa una richiesta di pull riguardo ad un problema, il Contributore PUO' avere la possibilità di lavorarci senza aprire un log separato.
- Per discutere riguardo ad una patch, le persone POSSONO commentare sulla richiesta di pull nella Platform, nel commit o in qualunque altro posto.
- Per accettare o respingere una patch, il Manutentore DEVE utilizzare l'interfaccia della Platform.
- Il Manutentore NON DEVE fare il merge delle sue stesse patch se non in casi eccezionali, come il non ricevere alcuna risposta dagli altri Manutentori per un lungo periodo di tempo (più di 1-2 giorni).
- I Manutentori NON DEVONO fare valutazioni alle le patch corrette.
- I Manutentori DEVONO fare il merge delle patch degli altri Contributori rapidamente.
- Il Contributore PUO' usare il tag "ready" dopo aver fatto la richiesta di pull per un problema.
- L'utente che ha aperto un problema DEVE provvedere a chiuderlo dopo aver controllato che la patch sia risolutiva.
- I Manutentori DEVONO chiedere miglioramenti per le patch non corrette e respingerle completamente nel caso in cui il Contributore non abbia un atteggiamento costruttivo.
- Qualunque Contributore abbia ricevuto commenti di valutazione alla sua patch corretta DEVE aggiungerli alla sua stessa patch.
- I Manutentori POSSONO inviare commit di cambiamento direttamente nel progetto.

### Creazione della Release Stabile

- Il progetto DEVE avere un branch ("master") che deve incorporare tutte le versioni più recenti in fase di sviluppo e deve essere sempre build.
- Il progetto NON DEVE utilizzare branch topic per nessuna ragione.Fork personali possono utilizzare i topic branch.
- Per produrre una release stabile l'utente DEVE fare un fork della repository copiandola e diventandone un manutentore.
- Fare un fork del progetto per stabilizzarlo PUO' essere effettuato in maniera unilaterale senza il consenso dei Manutentori di esso.
- Un progetto di stabilizzazione DEVE essere condotto secondo lo stesso processo del progetto principale.
- Una patch per un progetto di stabilizzazione DEVE essere dichiarata "stabile" e correlata da un test riproducibile.

### Evoluzione dei Public Contract

- Tutti i Public Contract (APIs o protocolli) DEVONO essere documentati.
- Tutti i Public Contract DEVONO poter essere sviluppati e testati.
- Una patch che modifica un Public Contract stabile NON DEVE compromettere il funzionamento di altre applicazioni a meno che non ci sia un forte consenso nel fare ciò.
- Una patch che introduce nuove funzionalità ad un Public Contract DOVREBBE utilizzare un nuovo nome.
- Le vecchie nomenclature DOVREBBERO essere deprecate in maniera sistematica aggiungendo espressioni come "sperimentale (experimental)" finchè non sono stabili, di conseguenza le nomenclature deprecate dovranno essere aggiornate con "deprecato (deprecated)".
- Trascorso un sufficiente periodo di tempo, le vecchie nomenclature DOVREBBERO essere aggiornate a "legacy" ed eventualmente eliminate.
- Le vecchie nomenclature NON DEVONO essere riutilizzate.
- Quando le vecchie nomenclature sono state rimosse, la loro implementazione DEVE generare una eccezione (assertion) se utilizzato dalle applicazioni.

### Project Administration

- I fondatori del progetto DEVONO agire come Amministratori nella gestione dei Manutentori.
- Gli Amministratori DOVREBBERO assicurare che avvenga un ricambio promuovendo i Manutentori migliori.
- Un nuovo Contributore che produce una patch risolutiva DOVREBBE essere invitato a diventare Manutentore.
- Gli Amministratori POSSONO rimuovere Manutentori inattivi per lunghi periodi di tempo o che falliscono ripetutamente nell'applicare questo processo in maniera accurata.
- Gli Amministratori DOVREBBERO bloccare o bannare coloro che provocano stress o sentimenti negativi negli altri partecipanti al progetto. Questo DEVE essere fatto dopo una discussione pubblica, in cui viene data la possibilità di esprimersi a tutte le parti coinvolte. Un cattivo collaboratore è colui che ignora ripetutamente le regole e lo spirito del progetto, che è inutilmente aggressivo e offensivo durante le discussioni e che è incapace di modificare e migliorare il proprio comportamento nonostante le richieste altrui.

# Processo di Governance

![Governance Process](https://getmonero.org/blog/assets/2015-year-in-review/governance-process.jpg)
