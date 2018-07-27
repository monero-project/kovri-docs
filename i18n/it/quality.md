Il seguente modello riguarda il flusso di lavoro sul controllo di qualità. Posto che tutte le fasi devono essere, in ultima istanza, portate a termine, è possibile lavorare individualmente a ciascuna di esse.

## Prima fase: Revisione di base

- Tutto il codice deve rispettare le linee guida per i collaboratori
- Evidenziare le aree che necessitano di un miglioramento, sia esso concettuale o a livello di codice
- Creare liste di cose da fare, e, ove possibile, distribuire i compiti

## Seconda fase: Revisione della specifica /  Implementazione / Documentazione del codice

- Revisionare completamente la specifica per ogni modulo (Streaming, I2PControl, etc.)
  - Il codice deve essere in-line; ogni parte della specifica deve mantenere lo stesso livello di anonimato fornito da java I2P, o raggiungere un livello superiore
  - Rifattorizzare/implementare/correggere quando/dove necessario
- Assicurarsi che l'implementazione sia conforme a C++11/14
  - Rivedere la seconda fase in caso di bisogno
- Risolvere tutti i punti presenti nelle liste di cose da fare
- Ove possibile, annotare il codice con commenti in-line e doxygen
  - Il codice dovrebbe essere compreso tanto da programmatori esperti che da programmatori principianti
  - Il codice dovrebbe guidare il lettore a una migliore comprensione di I2P
    - Data la complessità di I2P, il nostro codice dovrebbe essere non tanto un supplemento, quanto una versione autonoma della documentazione (questo potrebbe sembrare ridondante, ma comporta dei notevoli vantaggi in termini di manutenzione e durata del software)

## Terza fase: Revisione crittografica / Ispezione della sicurezza

- Assicurarsi che la crittografia sia aggiornata e propriamente implementata
- Stabilire quali sono i vettori di attacco conosciuti
  - Tenere questi vettori a mente mentre si scrivono i test di sicurezza
- Cercare di violare Kovri in ogni modo possibile
  - Riparare i danni apportati
- Utilizzare, ove possibile, librerie ben scritte e di fiducia
  - Astenersi dallo scrivere codici artigianali, ad hoc, nello stile "Sono sicuro che ne so molto di più della comunità"
- Chiedere una seconda opinione a uno o più colleghi prima di passare alla fase successiva

## Quarta fase: Risoluzione dei bug / Test / Profiling

- Risolvere i bug e i problemi principali
- Scrivere unità di test per ogni modulo
  - Eseguire i test. Eseguirli di nuovo
  - Revisionare i risultati dei test. Correggere o rifattorizzare ove necessario
- Assicurarsi che l'automazione venga eseguita su base regolare
  - valgrind, doxygen, clang-format
  - Correggere o rifattorizzare ove necessario

## Quinta fase: Consultazioni

- Consultarsi con i colleghi e con la comunità
  - Le consultazioni dovrebbero tenersi pubblicamente per mezzo di incontri, ticket, e/o IRC
- Accettare tutti i feedback, e, in risposta, produrre risultati tangibili
- Se soddisfatti, procedere alla fase successiva, altrimenti ripetere questa fase (o ripartire da una fase precedente)

## Sesta fase: Ripetere il ciclo dall'inizio
