# Ok, hai appena installato Kovri. E adesso?

## Step 1. Apri il tuo NAT/Firewall
1.  Scegli una porta tra ```9111``` e ```30777``` (ovviamente questa non dovrà interferire con altre applicazioni)
2. **Salva la porta scelta nel tuo file di configurazione** (`kovri.conf`)
3. Configura il tuo NAT/Fifewall per consentire ad esso di accettare le connessioni TCP/UDP in entrata dalla porta specificata (Guarda le note qui sotto se non hai accesso)

Note:

- **Non condividere il tuo numero di porta con nessuno altrimenti il tuo anonimato sarà compromesso!**
- Se non salvi la porta, Kovri ne rigenererà una nuova ad ogni avvio (hai anche la scelta di indicare la porta con `--port` ad ogni avvio).
- Se non hai accesso al tuo NAT, segui le istruzioni in [BUILDING](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/building.md) per il tuo SO.

## Step 2. Configurare Kovri

Per una lista completa di opzioni, digitare:

```bash
$ ./kovri --help
```

Per le opzioni scritte in maniera dettagliata:

- `kovri.conf` file di configurazione per il router e il client
- `tunnels.conf` file di configurazione per il client/server tunnel

## Step 3. Eseguire Kovri
```bash
$ cd build/ && ./kovri
```

- Aspettare più o meno 5 minuti (il tempo di attesa può variare a seconda del tuo compuer) per entrare nella rete prima di tentare di usare servizi

## Step 4. Unisciti a noi su IRC
1. Avvia il tuo [client IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Imposta il tuo client per connettersi con la porta IRC di Kovri (default 6669). Questo ti collegherà al network Irc2P (I2P's IRC network)
3. Entra in  `#kovri` e `#kovri-dev`

## Step 5. Navigare su un sito I2P (garlic-site/eepsite)
1. Apri un browser (preferibilmente un browser cha abbia il supporto per Kovri)
2. Configura il browser usando [questa guida](https://geti2p.net/en/about/browser-config) **invece di usare la porta 4444 e 4445** cambia la porta HTTP proxy a **4446** e *anche* la porta SSL proxy a **4446**
3. Se tutto è stato configurato correttamente, dovresti vedere un sito come [questo](http://check.kovri.i2p)

Note:

- **Come con Tor, una persona non ha bisogno di SSL per usare in sicurezza la rete**
- Il supporto dei siti con SSL e il servizio outproxy non sono correntemente implementati
- Se qualcuno ti da un indirizzo .i2p che non è nella tua rubrica,  usa il servizio  `Jump` [qui](http://stats.i2p/i2p/lookup.html)
- Guarda nel file hosts.txt nella tua cartella, troverai una lista di siti default che puoi facilmente visitare 
- In generale, il proxy HTTP e l'implementazione della rubrica sono in sviluppo e non ancora complete

## Step 6. Hosta il tuo garlic-service (garlic-site/eepsite)
- leggi `tunnels.conf` per imparare come impostare un server tunnel che punti al servizio che stai hostando

## Step 7. Buon divertimento!
- Leggi di più su Kovri nella [Moneropedia](https://getmonero.org/knowledge-base/moneropedia/kovri.html).
- Apri la richiesta per la tua feature o reporta un bug nel nostro [issues tracker](https://github.com/monero-project/kovri/issues)
- Approfondisci a riguardo del network I2P sul [java I2P website](https://geti2p.net/en/docs)

# Alternativamente, Docker

## Step 1. Installa Docker
L'installazione di Docker va oltre lo scopo di questo documento, per favore leggi la [documentazione di docker](https://docs.docker.com/engine/installation/)

## Step 2. Configurare / Aprire Firewall

L'immagine di Docker arriva con quella default di Kovri, ma può essere configurata come spiegato nelle sezioni precedenti.

Dovresti scegliere una porta casuale e usare quella porta (guarda sezioni precedenti)

## Step 3. Avviare

### Impostazioni di default
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

### Impostazioni personalizzate
Dove `./kovri-settings/` contiene `kovri.conf` e `tunnels.conf`.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
