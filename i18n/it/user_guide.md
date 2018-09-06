# Ok, hai appena installato Kovri. E adesso?

## Step 1. Apri il tuo NAT/Firewall
1.  Scegli una porta compresa tra ```9111``` e ```30777``` (prestando attenzione che non interferisca con altre applicazioni)
2. **Salva la porta scelta nel file di configurazione** `kovri.conf`
3. Configura il tuo NAT/Fifewall in modo che accetti le connessioni TCP/UDP in entrata dalla porta specificata (Vedi le note qui sotto se non hai accesso)

Note:

- **Non condividere il numero della porta con nessuno altrimenti il tuo anonimato sarà  compromesso!**
- Se non salvi la porta, Kovri ne rigenererà  una nuova ad ogni avvio (puoi anche indicare la porta con `--port` ad ogni avvio).
- Se non hai accesso al tuo NAT, segui le istruzioni in [BUILDING](https://github.com/monero-project/kovri-docs/blob/master/i18n/it/building.md) per il tuo Sistema Operativo.

## Step 2. (Consigliato) Sicurezza operazionale
- Valuta la creazione di un utente nel SO designato per l'utilizzo di ```kovri``` e usa kovri esclusivamente con quello
- Se si sta usando Linux, considerare la possibilità di utilizzare un "hardened kernel" (ad esempio [grsec](https://en.wikibooks.org/wiki/Grsecurity) assieme a RBAC)
- Dopo aver installato le risorse opportune nel percorso dati di kovri, considera l'installazione di un controllo di accesso adeguato con [setfacl](https://linux.die.net/man/1/setfacl), [umask](https://en.wikipedia.org/wiki/Umask) o quanto utilizzato dal tuo SO per l'ACL

Nota: guarda in kovri.conf per individuare il percorso dati Linux/OSX/Windows

## Step 3. Configurare Kovri

Per la lista completa di opzioni, digitare:

```bash
# Linux / macOS / *BSD
$ cd ~/bin && ./kovri --help
```

```bash
# Windows (PowerShell / MSYS2)
$ cd "C:\Program Files\Kovri" ; ./kovri.exe --help
```

Per le opzioni scritte in maniera dettagliata:

- `kovri.conf` (file di configurazione per il router e il client)
- `tunnels.conf` (file di configurazione per il client/server tunnel)

## Step 4. Eseguire Kovri
```bash
$ cd build/ && ./kovri
```

- Aspettare più o meno 5 minuti (l'attesa può variare a seconda del computer utilizzato) per entrare nella rete prima di tentare di usare i servizi

## Step 5. Unisciti a noi su IRC
1. Avvia il tuo [client IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Imposta il tuo client per la connessione alla porta IRC di Kovri (default ```6669```). Questo ti connetterà  al network Irc2P (I2P's IRC network)
3. Entra in  `#kovri` e `#kovri-dev`

## Step 6. Navigare su un sito I2P (garlic-site/eepsite)
1. Avvia un browser (preferibilmente un browser dedicato all'uso di Kovri)
2. Configura il browser prescelto usando [questa guida](https://geti2p.net/en/about/browser-config). **Invece di usare la porta 4444 e 4445** cambia la porta HTTP proxy a **4446** e *anche* la porta SSL proxy a **4446**
3. Se tutto è stato configurato correttamente, dovresti riuscire a visualizzare un sito come [questo](http://check.kovri.i2p)

Note:

- **Come con Tor, un utente non ha bisogno di SSL per usare in sicurezza la rete**
- Il supporto dei siti con SSL e il servizio Outproxy non sono correntemente implementati
- Se ricevi da qualcuno un indirizzo .i2p che non è nella tua rubrica,  usa il servizio  `Jump` [qui](http://stats.i2p/i2p/lookup.html)
- Guardando nel file hosts.txt nella tua cartella, troverai una lista di siti default che puoi facilmente visitare
- In generale, il proxy HTTP e l'implementazione della rubrica sono in sviluppo e non ancora complete

## Step 7. Hosta il tuo garlic-service (garlic-site/eepsite)
- leggi `tunnels.conf` per imparare come impostare un server tunnel che punti al servizio che stai hostando

## Step 8. Buon divertimento!
- Leggi di più su Kovri nella [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html).
- Apri la tua richiesta per nuove feature o segnala un bug nel nostro [issues tracker](https://github.com/monero-project/kovri/issues)
- Approfondisci l'argomento Network I2P sul [sito java I2P](https://geti2p.net/en/docs)

# Opzioni Container

## Snapcraft
Su sistemi Linux, puoi sfruttare Snapcraft per una facile implementazione.

## Step 1. Scarica la repository Kovri
```$ git clone --recursive https://github.com/monero-project/kovri```

## Step 2. Installa snapcraft
- Si consiglia di fare riferimento al package manager per snapcraft e [snapd](https://snapcraft.io/docs/core/install) della tua distribution

Su Ubuntu, digitare ed eseguire:
```$ sudo apt-get install snapcraft```

## Step 3. Crea lo snap
```$ cd kovri/ && snapcraft && sudo snap install *.snap --dangerous```

Nota: il parametro --dangerous è richiesto solo perché lo snap non è stato firmato (ma l'hai compilato personalmente, dunque non ci dovrebbero essere problemi)

## Step 4. Esegui Kovri con snapcraft
```$ snap run kovri```

# Alternativamente, Docker

## Step 1. Installa Docker
L'installazione di Docker va oltre lo scopo di questo documento, per favore fai riferimento alla [documentazione di docker](https://docs.docker.com/engine/installation/) per saperne di più

## Step 2. Configurare / Aprire Firewall

L'immagine di Docker arriva con quella default di Kovri, ma può essere configurata come spiegato nelle sezioni precedenti.

Dovresti scegliere una porta casuale e usare quella porta (guarda sezioni precedenti)

## Step 3. Avviare

### Impostazioni di default:
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

### Impostazioni personalizzate
Quando `./kovri-settings/` contiene `kovri.conf` e `tunnels.conf`:
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
