# So, Sie haben Kovri installiert. Was nun?

## Schritt 1. Öffnen Sie Ihre NAT/Firewall
1. Wählen Sie einen Port zwischen ```9111``` und ```30777```
2. **Speichern Sie diesen Port in Ihrer Konfigurationsdatei** (`kovri.conf`)
3. Bohren Sie ein Loch in Ihre NAT/Firewall, um eingehende TCP/UDP-Verbindungen zu diesem Port zuzulassen (Wenn Sie keinen Zugriff haben, beachten Sie die folgenden Hinweise)

Hinweise:

- Wenn Sie den Port nicht speichern, wird kovri zufällig bei jedem Start einen neuen generieren (Sie haben auch die Möglichkeit, den Port mit dem Flag `--port` bei jedem Start zu übergeben).
- Wenn Sie keinen Zugang zu Ihrem NAT haben, lesen Sie die Anweisungen für Ihr Betriebssystem im [Erstellungsleitfaden](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/building.md)
- **Teilen Sie Ihre Portnummer mit niemandem, da dies Ihre Anonymität beeinträchtigen wird!**

## Schritt 2. (Empfohlen) Betriebssicherheit (Opsec)

- Erwägen Sie, einen festgelegten `kovri`-Benutzer zu erstellen und führen Sie kovri nur mit diesem Benutzer aus
- Wenn Sie Linux nutzen, denken Sie über die Verwendung eines gehärteten Kernels nach (wie etwa [grsec](https://en.wikibooks.org/wiki/Grsecurity) mit RBAC)
- Nachdem Sie die entsprechenden Ressourcen in Ihrem kovri-Datenpfad installiert haben, sollten Sie eine angemessene Zugriffssteuerung (Access Control) einstellen mit [setfacl](https://linux.die.net/man/1/setfacl), [umask](https://en.wikipedia.org/wiki/Umask) oder was auch immer Ihr Betriebssystem als ACL (Access Control List) verwendet
- Teilen Sie Ihre Portnummer mit niemandem, da dies Ihre Anonymität beeinträchtigen wird!

**Hinweis: Ihren Datenpfad für Linux/OSX/Windows finden Sie in kovri.conf**

## Schritt 3. Kovri konfigurieren, Tunnel einrichten

Für eine vollständige Liste der Optionen:

```bash
$ ./kovri --help
```

Für vollständige Optionen mit Details:

- `kovri.conf` Konfigurationsdatei für Router und Client
- `tunnels.conf` Konfigurationsdatei für Client-/Server-Tunnel

## Schritt 4. (Optional) Tunnel einrichten

Kurz gesagt, *Client-Tunnel* sind Tunnel, über die Sie Verbindungen zu anderen Diensten herstellen, und *Server-Tunnel* werden verwendet, wenn Sie Dienste hosten (und andere Personen sich mit Ihrem Dienst verbinden).

Sie haben standardmäßig Client-Tunnel für IRC (Irc2P) und E-Mail (i2pmail) eingerichtet. Zum Hinzufügen/Entfernen von Client-Tunneln, siehe `tunnels.conf`.

Beim Erstellen von Server-Tunneln müssen Sie *persistente private Schlüssel* erzeugen. Entfernen Sie dafür das Kommentarzeichen bei bzw. schreiben Sie `keys = your-keys.dat` und ersetzen Sie `your-keys` mit einem geeigneten Namen. **Teilen Sie Ihre private `.dat`-Datei mit niemandem und stellen Sie sicher, dass Sie eine Sicherungskopie erstellen!**

Nach der Einrichtung wird Ihre [Base32-Adresse](https://getmonero.org/resources/moneropedia/base32-address) in Ihrem Log angezeigt, nachdem Sie kovri gestartet haben. Sie finden die Adresse auch in einer Textdatei zusammen mit der privaten Schlüsseldatei in Ihrem kovri-Datenpfad im `client/keys`-Ordner. Die Adresse in dieser `.txt`-Textdatei kann gefahrlos weitergegeben werden, damit sich andere Personen mit Ihrem Dienst verbinden können.

Beispiel:

- 
- Private Schlüsseldatei: `client/keys/your-keys.dat`
- Öffentliche [Base32](https://getmonero.org/resources/moneropedia/base32-address)-/[Base64](https://getmonero.org/resources/moneropedia/base64-address)-Adresse: `client/keys/your-keys.dat.txt`

**Hinweis: Ihren Datenpfad für Linux/OSX/Windows finden Sie in kovri.conf**

## Schritt 5. (Optional) Registrieren Sie Ihre neue [Eepsite](https://getmonero.org/resources/moneropedia/eepsite)

**Halt! Bis [#498](https://github.com/monero-project/kovri/issues/498) gelöst ist, sollten Sie Ihren Dienst nur bei Kovri registrieren und *nicht* bei stats.i2p!**

- Öffnen Sie einen Request mit `[Subscription Request] your-host.i2p` (ersetzen Sie your-host.i2p mit Ihrem gewünschten Hostnamen) im [Kovri-Issue-Tracker](https://github.com/monero-project/kovri/issues)
- Fügen Sie im Text des Requests den Inhalt Ihrer öffentlichen `.txt`-Datei, die im vorherigen Schritt erwähnt wurde, ein
- Nach einer Überprüfung werden wir Ihren Host hinzufügen und das Abonnement signieren
- Fertig!

## Schritt 6. Kovri ausführen
```bash
$ cd build/ && ./kovri
```
- Warten Sie etwa 5 Minuten, damit der Bootstrap-Vorgang ins Netzwerk abgeschlossen ist, bevor Sie versuchen, Dienste zu nutzen

## Schritt 7. Schließen Sie sich uns auf IRC an
1. Starten Sie Ihren [IRC-Client](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Richten Sie Ihren Client ein, um eine Verbindung mit Kovris IRD-Port (Standardeinstellung: 6669) herzustellen. Das wird Sie mit dem Irc2P-Netzwerk (I2Ps IRC-Netzwerk) verbinden
3. Treten Sie `#kovri` und `#kovri-dev` bei

## Schritt 8. Auf einer I2P-Website browsen (Garlic-Site/Eepsite)
1. Starten Sie einen Browser Ihrer Wahl (vorzugsweise einen Browser, der der Verwendung von Kovri gewidmet ist)
2. Konfigurieren Sie Ihren Browser, indem Sie [diese Anleitungen](https://geti2p.net/de/about/browser-config) durchlesen, **aber anstelle von Port 4444 und 4445**, ändern Sie den HTTP-Proxy-Port zu **4446** und den SSL-Proxy-Port *auch* zu **4446**
3. Besuchen Sie http://check.kovri.i2p

Hinweise:

- **Genau wie bei Tor braucht man kein SSL, um gefahrlos und sicher das Netzwerk zu nutzen**
- SSL-Site-Support und Outproxy-Dienst sind derzeit nicht implementiert
- Wenn Ihnen jemand eine .i2p-Adresse gibt, die nicht in Ihrem Adressbuch enthalten ist, nutzen Sie den Dienst `Jump` auf http://stats.i2p/i2p/lookup.html
- In hosts.txt in Ihrem Datenverzeichnis finden Sie eine Liste mit Standardseiten, die Sie leicht besuchen können
- Insgesamt befinden sich HTTP-Proxy und die Adressbuchimplementierung in der Entwicklung und sind noch nicht voll funktionstüchtig

## Schritt 9. Viel Spaß!
- Lesen Sie mehr über Kovri in der [Moneropedia](https://getmonero.org/resources/moneropedia/kovri).
- Öffnen Sie Ihre Feature-Requests oder melden Sie Bugs in unserem [Issue-Tracker](https://github.com/monero-project/kovri/issues)
- Lernen Sie mehr über das I2P-Netzwerk auf der [Java-I2P-Website](https://geti2p.net/en/docs)

# Container-Optionen

## Snapcraft

Verwenden Sie auf Linux-Systemen snapcraft für eine einfache Bereitstellung.

### Schritt 1. Das Kovri-Quellen-Repo herunterladen

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### Schritt 2. snapcraft installieren

- Beziehen Sie sich auf das Paketverwaltungsprogramm Ihrer Distribution für snapcraft und [snapd](https://snapcraft.io/docs/core/install)

Auf Ubuntu einfach Folgendes ausführen:
```bash
$ sudo apt-get install snapcraft
```

### Schritt 3. Den Snap erstellen

```bash
$ cd kovri/ && snapcraft && sudo snap install *.snap --dangerous
```
Hinweis: Das Flag --dangerous wird nur benötigt, weil der snap nicht signiert wurde (Sie haben es jedoch selbst erstellt, das sollte also kein Problem sein)

### Schritt 4. Kovri mit snapcraft ausführen

```bash
$ snap run kovri
```

## Docker

### Schritt 1. Docker installieren
Die Installation von Docker ist nicht in diesem Dokument enthalten. Weitere Informationen finden Sie hierzu in der [Docker-Dokumentation](https://docs.docker.com/engine/installation/)

### Schritt 2. Firewall konfigurieren / öffnen

Das Docker-Image kommt mit den Standardeinstellungen von Kovri, kann aber wie in vorhergehenden Abschnitten erläutert konfiguriert werden.

Sie sollten einen zufälligen Port auswählen und diesen Port öffnen (siehe vorhergehende Abschnitte).

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
