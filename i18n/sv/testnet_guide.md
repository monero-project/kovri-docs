# Att komma igång med Kovris testnät

## Inledning

Kovri's testnätverk finns för närvarande inom ett antal Docker-behållare och avbildningar som alla kommunicerar över ett enda Docker-nätverk.
Detta möjliggör privat nätverkstestning och -övervakning utan anslutning till det offentliga kovri-nätverket.

## Förutsättningar

- Linux utvecklingsmiljö (Linux stöds för närvarande)
   - Se kovris [README](https://github.com/monero-project/kovri#building) för en lista av bygg-beroenden
- [Docker](https://www.docker.com/)
   - Användaren som ska bygga måste ha behörighet att använda Docker (tillagd i gruppen docker, till exempel)
- Ett klonat kodförråd

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

## Steg 1: Skapa testnätet

Kör kommandot `help` för att visa en fullständig lista av alternativ:

```bash
$ ./kovri/contrib/testnet/testnet.sh help
```

Du kan exportera de listade miljövariablerna från ditt skal eller ange dem själv vid konfiguration.

Skapa miljön och ange lämpliga värden:

```bash
$ ./kovri/contrib/testnet/testnet.sh create
```

- Nya utvecklare rekommenderas att använda standardinställningarna, förutom sökvägen till kodförrådet
- Se mappen Dockerfiles för tillgängliga Dockerfiles att bygga vid konfiguration
- För att hålla rent i kodförrådet Kovri bör du välja en mapp utanför kodförrådet

## Steg 2a: Starta testnätet

```bash
$ ./kovri/contrib/testnet/testnet.sh start
```

Kör kommandot `help` för att visa information om hur övervakning sker.

## Steg 2b: Kör anpassade kommandon

**TODO(unassigned): förbättra detta avsnitt**

Se Dockers dokumentation för information om hur man kör kommandon inifrån en behållare.

Du kan också försöka:

```bash
$ ./contrib/testnet/testnet.sh exec "bash"
```

## Steg 3: Stoppa testnätet

```bash
$ ./kovri/contrib/testnet/testnet.sh stop
```

- Du får en uppmaning att ange ett timeout-intervall för behållaren (om env inte har angetts)
   - Detta är användbart ifall routern hänger sig

## Steg 4: Avsluta testnätet

```bash
$ ./kovri/contrib/testnet/testnet.sh destroy
```

- Du för en uppmaning att ange vilken testnät-mapp som ska avlutas (om env inte har angetts)

