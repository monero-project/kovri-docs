# Erste Schritte mit dem Kovri-Testnet

## Präambel

Kovris Testnet liegt momentan in einer Reihe von Docker-Containern und -Images, die alle über ein einziges Docker-Netzwerk miteinander kommunizieren. Dies ermöglicht das private Testen und Überwachen des Netzwerks, ohne sich mit dem öffentlichen Kovri-Netzwerk verbinden zu müssen.

## Voraussetzungen

- Linux-Entwicklungsumgebung (Linux wird derzeit unterstützt)
   - In der Kovri-[README](https://github.com/monero-project/kovri-docs/blob/master/i18n/de/README.md#kompilierung) findet sich eine Liste an Kompilierungsabhängigkeiten
- [Docker](https://www.docker.com/)
   - Der kompilierende Nutzer muss die Berechtigungen haben, Docker zu nutzen (zur Docker-Gruppe hinzugefügt sein, zum Beispiel)
- Ein geklontes Repository
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

## Schritt 1: Das Testnet erstellen

Um eine vollständige Liste der Optionen zu sehen, führe die `help`-Option aus:
```bash
$ ./kovri/contrib/testnet/testnet.sh help
```
Du kannst die aufgelisteten Umgebungsvariablen aus deiner Shell exportieren oder sie manuell während des Setups setzen.

Erstelle die Umgebung und setze die Werte entsprechend:
```bash
$ ./kovri/contrib/testnet/testnet.sh create
```
- Neuen Entwicklern wird geraten, die Default-Werte zu verwenden, mit Ausnahme des Speicherortes deiner Repository
- Siehe im Dockerfiles-Ordner nach verfügbaren Dockerfiles, die während des Setups zu kompilieren sind
- Um das Repo sauber zu halten, wähle einen Ordner außerhalb des Repos

## Schritt 2a: Das Testnet starten

```bash
$ ./kovri/contrib/testnet/testnet.sh start
```
Führe `help` aus, um Details zu den Überwachungsoptionen und darüber, wie man überwacht, zu erhalten.

## Schritt 2b: Benutzerdefinierte Befehle ausführen

**TODO(unassigned): improve this section**

Wie man Befehle von innerhalb eines Containers ausführt, ist in der Docker-Dokumentation beschrieben.

Du kannst auch Folgendes versuchen:
```bash
$ ./contrib/testnet/testnet.sh exec "bash"
```

## Schritt 3: Das Testnet stoppen

```bash
$ ./kovri/contrib/testnet/testnet.sh stop
```
- Du solltest aufgefordert werden, ein Container-Timeout-Intervall festzulegen (falls env nicht bestimmt ist)
   - Dies ist nützlich im Falle sich aufhängender Router

## Schritt 4: Das Testnet zerstören

```bash
$ ./kovri/contrib/testnet/testnet.sh destroy
```
- Du solltest aufgefordert werden, den Testnet-Ordner zu zerstören (falls env nicht bestimmt ist)
