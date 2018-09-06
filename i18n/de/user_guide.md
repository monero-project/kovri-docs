# So, du hast Kovri installiert. Was nun?

## Schritt 1. Öffnen deiner NAT/Firewall
1. Wähle einen Port zwischen ```9111``` und ```30777```
2. **Speichere diesen Port in deiner Konfigurationsdatei** (`kovri.conf`)
3. Bohre ein Loch in deine NAT/Firewall, um eingehende TCP/UDP-Verbindungen zu diesem Port zuzulassen (Wenn du keinen Zugriff hast, beachte die folgenden Hinweise)

Hinweise:

- Wenn du den Port nicht speicherst, wird kovri zufällig bei jedem Start einen neuen generieren (du hast auch die Möglichkeit, den Port mit dem Flag `--port` bei jedem Start zu übergeben).
- Wenn du keinen Zugang zu deinem NAT hast, verwende die Laufzeitoption `--enable-upnp` oder schalte die Option in `kovri.conf` ein.
- **Teile deine Portnummer mit niemandem, da dies deine Anonymität beeinträchtigen wird!**

## Schritt 2. (Empfohlen) Operative Sicherheit (Opsec)

- Erwäge, einen eigenen `kovri`-Benutzer zu erstellen und führe kovri nur mit diesem Benutzer aus
- Wenn du Linux nutzt, denke über die Verwendung eines gehärteten Kernels nach (wie etwa [grsec](https://en.wikibooks.org/wiki/Grsecurity) mit RBAC)
- Nachdem du die entsprechenden Ressourcen in deinem kovri-Datenpfad installiert hast, solltest du eine angemessene Zugriffssteuerung (Access Control) einstellen mit [setfacl](https://linux.die.net/man/1/setfacl), [umask](https://en.wikipedia.org/wiki/Umask) oder was auch immer dein Betriebssystem als ACL (Access Control List) verwendet
- Teile deine Portnummer mit niemandem, da dies deine Anonymität beeinträchtigen wird!

**Hinweis: Deinen Datenpfad für Linux/OSX/Windows findest du in kovri.conf**

## Schritt 3. Kovri konfigurieren

Für eine vollständige Liste der Optionen:

```bash
# Linux / macOS / *BSD
$ cd ~/bin && ./kovri --help
```

```bash
# Windows (PowerShell / MSYS2)
$ cd "C:\Program Files\Kovri" ; ./kovri.exe --help
```

Für vollständige Optionen mit Details:

- `kovri.conf` Konfigurationsdatei für Router und Client
- `tunnels.conf` Konfigurationsdatei für Client-/Server-Tunnel

## Schritt 4. (Optional) Tunnel einrichten

Kurz gesagt, *Client-Tunnel* sind Tunnel, über die du Verbindungen zu anderen Diensten herstellst. *Server-Tunnel* werden verwendet, wenn du Dienste hostest, sodass sich andere Personen mit deinem Dienst (Website, SSH, etc.) verbinden können.

Du hast standardmäßig Client-Tunnel für IRC (Irc2P) und E-Mail (i2pmail) eingerichtet. Zum Hinzufügen/Entfernen von Client-Tunneln, siehe `tunnels.conf`.

Beim Erstellen von Server-Tunneln musst du *dauerhafte private Schlüssel* erzeugen, die für dein Ziel verwendet werden. Entferne dafür das Kommentarzeichen bei bzw. schreibe `keys = your-keys.dat` und ersetze `your-keys` mit einem geeigneten Namen. **Teile deine private `.dat`-Datei mit niemandem (hier besteht eine einzige Ausnahme und zwar, falls du Multihoming einsetzen möchtest) und stelle sicher, dass du eine Sicherungskopie der Datei erstellst!**

Nach der Einrichtung wird dein [Base32](https://getmonero.org/resources/moneropedia/base32-address)- und [Base64](https://getmonero.org/resources/moneropedia/base64-address)-codiertes Ziel in deinem Log angezeigt, nachdem du kovri gestartet hast. Du findest diese Codierungen auch in einer Textdatei zusammen mit der `.dat`-Datei in deinem kovri-Datenpfad im `client/keys`-Ordner. Das codierte Ziel in den **Textdateien** `.dat.b32.txt` und `.dat.b64.txt`kann gefahrlos an andere weitergegeben werden, damit sie sich mit deinem Dienst verbinden können.

Beispiel:

- Private Schlüsseldatei: `client/keys/your-keys.dat`
- Öffentliche [Base32](https://getmonero.org/resources/moneropedia/base32-address): `client/keys/your-keys.dat.b32.txt`
- Öffentliche [Base64](https://getmonero.org/resources/moneropedia/base64-address): `client/keys/your-keys.dat.b64.txt`

**Hinweis: Deinen Datenpfad für Linux/OSX/Windows findest du in kovri.conf**

## Schritt 5. (Optional) Registrieren deiner neuen [Eepsite](https://getmonero.org/resources/moneropedia/eepsite)

**Halt! Bis [#498](https://github.com/monero-project/kovri/issues/498) gelöst ist, solltest du deinen Dienst nur bei Kovri registrieren und *nicht* bei stats.i2p!**

- Öffne einen Request mit `[Subscription Request] your-host.i2p` (ersetze your-host.i2p mit deinem gewünschten Hostnamen) im [Kovri-Issue-Tracker](https://github.com/monero-project/kovri/issues)
- Füge im Text des Requests den Inhalt deiner öffentlichen, im vorherigen Schritt erwähnten, `.txt`-Datei ein
- Nach einer Überprüfung werden wir deinen Host hinzufügen und das Abonnement signieren
- Fertig!

## Schritt 6. Kovri ausführen
```bash
$ cd build/ && ./kovri
```
- Warte etwa 5 Minuten, damit der Bootstrap-Vorgang ins Netzwerk abgeschlossen ist, bevor du versuchst, Dienste zu nutzen

## Schritt 7. Sich uns auf IRC anschließen
1. Starte deinen [IRC-Client](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Richte deinen Client ein, um eine Verbindung mit Kovris IRD-Port (Standardeinstellung: 6669) herzustellen. Das wird dich mit dem Irc2P-Netzwerk (I2Ps IRC-Netzwerk) verbinden
3. Trete `#kovri` und `#kovri-dev` bei

## Schritt 8. Auf einer I2P-Website browsen (Garlic-Site/Eepsite)
1. Starte einen Browser deiner Wahl (vorzugsweise einen Browser, der der Verwendung von Kovri gewidmet ist)
2. Konfiguriere deinen Browser, indem du [diese Anleitungen](https://geti2p.net/de/about/browser-config) durchliest, **aber anstelle von Port 4444 und 4445**, ändere den HTTP-Proxy-Port zu **4446** und den SSL-Proxy-Port *auch* zu **4446**
3. Besuche http://check.kovri.i2p

Hinweise:

- **Genau wie bei Tor braucht man kein SSL, um gefahrlos und sicher das Netzwerk zu nutzen**
- SSL-Site-Support und Outproxy-Dienst sind derzeit nicht implementiert
- Wenn dir jemand eine .i2p-Adresse gibt, die nicht in deinem Adressbuch enthalten ist, nutze den Dienst `Jump` auf http://stats.i2p/i2p/lookup.html
- In hosts.txt in deinem Datenverzeichnis findest du eine Liste mit Standardseiten, die du leicht besuchen kannst
- Insgesamt befinden sich HTTP-Proxy und die Adressbuchimplementierung in der Entwicklung und sind noch nicht voll funktionstüchtig

## Schritt 9. Viel Spaß!
- Lies mehr über Kovri in der [Moneropedia](https://getmonero.org/resources/moneropedia/kovri).
- Öffne deine Feature-Requests oder melde Bugs in unserem [Issue-Tracker](https://github.com/monero-project/kovri/issues)
- Lerne mehr über das I2P-Netzwerk auf der [Java-I2P-Website](https://geti2p.net/en/docs)

# Container-Optionen

## Snapcraft

Verwende auf Linux-Systemen snapcraft für eine einfache Bereitstellung.

### Schritt 1. Das Kovri-Quellen-Repo herunterladen

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### Schritt 2. snapcraft installieren

- Beziehe dich auf das Paketverwaltungsprogramm deiner Distribution für snapcraft und [snapd](https://snapcraft.io/docs/core/install)

Auf Ubuntu einfach Folgendes ausführen:
```bash
$ sudo apt-get install snapcraft
```

### Schritt 3. Den Snap erstellen

```bash
$ cd kovri/ && snapcraft && sudo snap install *.snap --dangerous
```
Hinweis: Das Flag --dangerous wird nur benötigt, weil der snap nicht signiert wurde (du hast es jedoch selbst erstellt, das sollte also kein Problem sein)

### Schritt 4. Kovri mit snapcraft ausführen

```bash
$ snap run kovri
```

## Docker

### Schritt 1. Docker installieren
Die Installation von Docker ist nicht in diesem Dokument enthalten. Weitere Informationen findest du hierzu in der [Docker-Dokumentation](https://docs.docker.com/engine/installation/)

### Schritt 2. Firewall konfigurieren / öffnen

Das Docker-Image kommt mit den Standardeinstellungen von Kovri, kann aber, wie in den vorhergehenden Abschnitten erläutert, konfiguriert werden.

Du solltest einen zufälligen Port auswählen und diesen Port öffnen (siehe vorhergehende Abschnitte).

### Step 3. Ausführen

#### Standardeinstellungen
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

#### Benutzerdefinierte Einstellungen
Wo `./kovri-settings/` sowohl `kovri.conf` als auch `tunnels.conf` enthält.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
