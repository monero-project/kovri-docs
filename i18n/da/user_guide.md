# Så du har installere Kovri, hvad nu?

## Trin 1. Åben din NAT/Firewall
1. Vælg en port mellem ```9111``` og ```30777```
2. **Gem denne port til din konfigurationsfil** (`kovri.conf`)
3. Prik et hul i din NAT/Firewall for at tillade indkomne TCP/UDP forbindelser til den port (Se notater nedenunder hvis du ikke har adgang)

Noter:

- Hvis du ikke gemmer porten ville Kovri tilfældigt generere en ny en ved hver opstart (Du har også muligheden for at vælge en port med `--port` flaget på hver opstart)
- Hvis du ikke har adgang til din NAT, se instruktionerne i [building guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/building.md) til dit OS.
- **Del ikke dit port nummer med nogen da det ville påvirke din anonymitet!**

## Trin 2. (Anbefalet) Operationel sikkerhed

- Overvej at oprette en `kovri` bruger og kør kun kovri ved brug af brugeren.
- Hvis du bruger Linux, overvej en hardened kernel (så som [grsec](https://en.wikibooks.org/wiki/Grsecurity) med RBAC)
- Efter du har installeret de passende ressourcer i din kovri datasti, overvej%%%%%%%%%%%
- Del aldrig dit port nummer med nogen da det ville påvirke din anonymitet!

**Note: Se kovri.conf for at finde din datasti til Linux/OSX/Windows**

## Trin 3. Konfigurer Kovri, opsætning af tunneller

For en fuld liste af muligheder:

```bash
$ ./kovri --help
```

For komplette løsninger med detaljer: 

- `kovri.conf` konfigurationsfil for router og klient
- `tunnels.conf` konfigurationsfil for klient/server tunneller

## Trin 4. (Valgfri) Opsætning af tuneller

Kort sagt, *klient tunneller* er tuneller som du bruger til at forbinde til andre servicer og *Server tunneller* bliver brugt når du hoster et service(r) (og andre folk forbinder sig til dit service).

Som standard, ville du have klient tunneller opsat til IRC (Irc2P) og email (i2pmail). For at tilføje/fjerne klient tunneller, se `tunnels.conf`.

Når du opretter server tunneller, ville du blive nødt til at oprette *persistent private keys*. For at gøre det, uncomment eller opret `keys = your-keys.dat` og erstat `your-keys` med et passende navn. **Del ikke din private `.dat` fil med nogen, og lav en backup!**

Når opsat, ville din [Base32 address](https://getmonero.org/resources/moneropedia/base32-address) blive vist i din log efter du starter Kovri. Du kan også finde adressen i en tekst fil samt den private nøgler fil i din Kovri datasti i `client/keys` mappen. Adressen i denne `.txt` tekst fil er sikker at videregive så andre kan forbinde sig til dit service.

Eksempel:

- Private nøgler fil: `client/keys/your-keys.dat`
- Offentlig [Base32](https://getmonero.org/resources/moneropedia/base32-address)/[Base64](https://getmonero.org/resources/moneropedia/base64-address) addresse: `client/keys/your-keys.dat.txt`

**Note: Se kovri.conf for at finde din datasti til Linux/OSX/Windows**

## Trin 5. (Valgfri) Registrer din nye [eepsite](https://getmonero.org/resources/moneropedia/eepsite)

**Stop! indtil [#498](https://github.com/monero-project/kovri/issues/498) er løst, og overvej kun at registrere dit service med Kovri og *ikke* stats.i2p!** 

- Open en request med `[Subscription Request] your-host.i2p` (Erstat your-host.i2p med dit ønskede hostnavn) på [Kovri issue tracker](https://github.com/monero-project/kovri/issues)
- I request body, indsæt indholdet af din offentlige `.txt` fil der blev nævnt in de tidligere skridt
- Efter gennemgang, ville vi tilføje din host og tilmelde abonnomentet
- Færdig!

## Trin 6. Køre Kovri
```bash
$ cd build/ && ./kovri
```
- Vent 5 minutter eller deromkring for at blive selvopstartet til netværket før  du prøver at bruge servicer

## Trin 7. Join os på IRC
1. Start din [IRC klient](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Opsæt din klient til at forbinde til kovri's IRC port (standard 6669). Denne ville forbinde dig til Irc2p netværket (I2P's IRC netværk)
3. Join `#kovri` og `#kovri-dev`

## Trin 8. Gennemse en I2P hjemmeside (garlic-site/eepsite)
1. Start en valgfri browser op (helst en browser hengivet til kovri brug)
2. Konfigurer din browser ved at læse [disse instruktioner](https://geti2p.net/en/about/browser-config) **men i stedet for port 4444 og 4445* skift HTTP proxy port til **4446** og SSL proxy port *også* til **44446**
3. Besøg http://check.kovri.i2p

Noter:

- **Ligesom med Tor behøver man ikke SSL for at bruge netværket sikkert**
- SSL side understøttelse og outproxy service er på nuværende tidspunkt ikke implementeret
- Hvis nogen giver dig en .i2p adresse der ikke er i din adressebog, så brug `Jump` servicet på http://stats.i2p/i2p/lookup.html
- Kig igennem hosts.txt i din datasti for at se en liste af standard sider du nemt kan besøge
- Samlet set, HTTP Proxy og adressebog implementationen er i udvikling og ikke endnu feature-komplette

## Trin 9. God fornøjelse!
- Læs mere om Kovri på [Moneropedia](https://getmonero.org/resources/moneropedia/kovri).
- Åben dine feature requests eller report bugs på vores [issues tracker](https://github.com/monero-project/kovri/issues)
- Lær mere om I2P netværket på [java I2P websiden](https://geti2p.net/en/docs)

# Container muligheder

## Snapcraft

På Linux systemer, brug snapcraft for nem implementering.

### Trin 1. Hent Kovri's source depot

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### Trin 2. Installer snapcraft

- Se din distrubitions package manager til snapcraft og [snapd](https://snapcraft.io/docs/core/install)

På Ubuntu, bare kør:
```bash
$ sudo apt-get install snapcraft
```

### Trin 3. Opret snappet

```bash
$ cd kovri/ && snapcraft && sudo snap install *.snap --dangerous
```
Note: --dangerous flaget er nødvendigt fordi snappet ikke er blevet signeret (Du har dog bygget det selv, så dette burde ikke være nødvendigt)

### Trin 4. Kør Kovri med snapcraft

```bash
$ snap run kovri
```

## Docker

### Trin 1. Installer Docker
Installering af Docker er ude for anvendelsesområdet af denne dokumentation, se venligst [docker dokumentationen](https://docs.docker.com/engine/installation/)

### Trin 2. Konfigurering / Åben Firewallen

Docker billedet kommer med standarderne af Kovri, men kan blive konfigureret som forklaret i de tidligere sektioner.

Du burde vælge en tilfældig port og åbne den port (Se tidligere sektioner).

### Trin 3. At køre Kovri

#### Standardindstillinger
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

#### Brugerdefinerede indstillinger
Hvor `./kovri-settings/` indeholder `kovri.conf` og `tunnels.conf`.
```bash
KOVRI_PORT=