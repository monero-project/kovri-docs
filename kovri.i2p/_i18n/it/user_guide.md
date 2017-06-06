# Ok, ho appena installato Kovri. E adesso?

## Step 1. Apri il tuo NAT/Firewall
1.  Scegli una porta tra ```9111``` e ```30777``` (ovviamente questa non dovrà interferire con altre applicazioni)
2. **Salva la porta scelta nel tuo file di configurazione** (`kovri.conf`)
3. Configura il tuo NAT/Fifewall per consentire ad esso di accettare le connessioni  TCP/UDP in entrata dalla porta (Guarda le note qui sotto se non hai accesso)

Note:

- **Non condividere il tuo numero di porta con nessuno altrimenti la tua anonimità sarà compromessa!**
- Se non salvi la porta, Kovri ne rigenererà una nuova ad ogni avvio (hai anche la scelta di indicare la porta con `--port` ad ogni avvio).
- Se non hai accesso al tuo NAT, segui le istruzioni in [BUILDING](https://github.com/monero-project/kovri/blob/master/doc/BUILDING.md) per il tuo OS. 

## Step 2. Configurare Kovri

Per una lista completa di opzioni, digitare:

```bash
$ ./kovri --help
```

Per le opzioni scritte in maniera dettagliata:

- `kovri.conf` file di configurazione per il router e il client
- `tunnels.conf` file di configurazione per il client/server tunnels

## Step 3. Eseguire Kovri
```bash
$ cd build/ && ./kovri
```

- Aspettare 5 minuti (il tempo di attesa può variare a seconda del tuo compuer) per entrare nella rete prima del tentativo di usare servizi

## Step 4. Unisciti al canale IRC
1. Avvia il tuo [IRC client](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Imposta il tuo client per connettersi con la porta IRC di kovri (default 6669). Questo ti collegherà al network Irc2P (I2P's IRC network)
3. Entra in  `#kovri` e `#kovri-dev`

## Step 5. Navigare su un sito I2P (garlic-site/eepsite)
1. Apri un browser (preferibilmente un browser cha abbia il supporto a kovri)
2. Configura il browser usando questa guida [these instructions](https://geti2p.net/en/about/browser-config) **invece di usare la porta 4444 e 4445** cambia la porta HTTP proxy a **4446** e la porta SSL proxy a **4446**
3. Se tutto è stato configurato correttamente, dovresti vedere un sito come questo http://check.kovri.i2p

Note:

- **Come Tor, una persona non ha bisogno di SSL per usare in sicurezza la rete**
- Il supporto dei siti con SSL non è stato implementato
- Se qualcuno ti da un indirizzo .i2p che non è nel tuo address book,  usa il servizio  `Jump` http://stats.i2p/i2p/lookup.html
- Guarda nel file hosts.txt , dovresti trovare alcuni siti che potresti visitare
- Overall, HTTP Proxy and address book implementation are in development and not yet feature-complete

## Step 6. Host your own garlic-service (garlic-site/eepsite)
- Read `tunnels.conf` to learn how to set a server tunnel to point to the service you are hosting

## Step 7. Enjoy!
- Read more about Kovri in the [Moneropedia](https://getmonero.org/knowledge-base/moneropedia/kovri).
- Open your feature requests or report bugs on our [issues tracker](https://github.com/monero-project/kovri/issues)
- Learn more about the I2P network on the [java I2P website](https://geti2p.net/en/docs)

# Alternatively, Docker

## Step 1. Install Docker
Installing Docker is outside the scope of this document, please see the [docker documentation](https://docs.docker.com/engine/installation/)

## Step 2. Configuring / Open Firewall

The docker image comes with the defaults of kovri, but can be configured as explained in earlier sections.

You should choose a random port and open that port (see earlier sections).

## Step 3. Running

### Default Settings
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

### Custom Settings 
Where `./kovri-settings/` contains `kovri.conf` and `tunnels.conf`.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
