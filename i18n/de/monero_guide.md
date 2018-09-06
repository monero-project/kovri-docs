# Monero über Kovri

## Erste Schritte

1. Folge den Anleitungen zum Kompilieren und/oder Installieren von [Kovri](https://github.com/monero-project/kovri) & [Monero](https://github.com/monero-project/monero)
2. Sieh das [Benutzerhandbuch](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/user_guide.md) in der Sprache deiner Wahl durch
3. Konfiguriere Kovri-Server- und -Client-Tunnel für die Verbindung mit `monerod`-Nodes über das I2P-Netzwerk

## Kovri-Server-Tunnel

Konfiguriere zunächst einen Server-Tunnel auf einem Node.

Infos zum Einrichten eines Server-Tunnels sind in der Datei `tunnels.conf` in deinem Datenverzeichnis. Um dein Datenverzeichnis zu finden, siehe `kovri.conf`.

```
[XMR_P2P_Server]
type = server
address = 127.0.0.1
port = 28080
in_port = 28080
keys = xmr-p2p-keys.dat
;white_list =
;black_list =
```

Diese Konfiguration öffnet einen Kovri-Listener auf dem standardmäßigen Testnet-P2P-Port von `monerod`. Lese als nächstes im [Benutzerhandbuch](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/user_guide.md), wie man die Base32-Zieladresse erhält.

Falls du bereits deinen Kovri-Router gestartet hast, führe `$ kill -HUP $(pgrep kovri)` aus, um den neuen Tunnel zu laden. Eine drastischere Möglichkeit besteht darin, einen harten Neustart durchzuführen, durch Stoppen und Starten von Kovri.

## Kovri-Client-Tunnel

Jetzt, wo der Server-Tunnel eingerichtet ist, kannst du die Einrichtung des Client-Tunnels durch Zeigen auf den Server-Tunnel starten.

Beispiel:

```
[XMR_Client]
type = client
address = 127.0.0.1
port = 24040
dest = dein-kopiertes-server-ziel.b32.i2p
dest_port = 28080
keys = xmr-client-keys.dat
```

Wiederhole den Prozess für jeden Node, den du mittels Kovri verbinden möchtest.

Falls du bereits deinen Kovri-Router gestartet hast, führe `$ kill -HUP $(pgrep kovri)` aus, um den neuen Tunnel zu laden. Eine drastischere Möglichkeit besteht darin, einen harten Neustart durchzuführen, durch Stoppen und Starten von Kovri.

## Monero P2P über Kovri

Es ist genauso einfach, `monerod` auf deinen neuen Kovri-Client-Tunnel zeigen zu lassen.

Hier ist ein Beispiel für das Starten eines minenden Testnet-Nodes:

```bash
monerod --testnet --start-mining deine-Testnet-Wallet-Adresse --add-exclusive-node 127.0.0.1:24040
```

Falls du Verbindungsprobleme bemerkst, warte, bis sich deine Kovri-Nodes ins Netzwerk integrieren (~5-10 Minuten nach dem Start).

## Monero RPC über Kovri

Moneros RPC-Service über Kovri verfügbar zu machen, ist ein ähnlicher Prozess.

Konfiguriere einen Server-Tunnel auf deinem Kovri-Node:

```
[XMR_RPC_Server]
type = server
address = 127.0.0.1
port = 28081
in_port = 28081
keys = xmr-rpc-keys.dat
;white_list =
;black_list =
```

Dies wird einen neuen Schlüsselsatz und eine neue Zieladresse erzeugen.

Um dieselbe Zieladresse als P2P zu nutzen, ersetze einfach `xmr-rpc-keys.dat` durch `xmr-p2p-keys.dat` in der obigen Konfiguration.

Falls du bereits deinen Kovri-Router gestartet hast, führe `$ kill -HUP $(pgrep kovri)` aus, um den neuen Tunnel zu laden. Eine drastischere Möglichkeit besteht darin, einen harten Neustart durchzuführen, durch Stoppen und Starten von Kovri.

Dieser Tunnel macht `monerod`s standardmäßiges Testnet-JSON-RPC verfügbar und man kann Kovris HTTP-Client-Tunnel verwenden, um sich zu verbinden.

Hier ist ein Beispiel zur Verbindung mit curl von einem Kovri-Client-Node aus:

```bash
export http_proxy=127.0.0.1:4446 rpc_server=http://dein-kopiertes-rpc-ziel.b32.i2p:28081
curl -X POST ${rpc_server}/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_height"}' -H 'Content-Type: application/json'
```
