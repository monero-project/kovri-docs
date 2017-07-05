# Alors, vous avez installé Kovri. Et maintenant?

## Etape 1. Ouvrir votre NAT/Firewall
1. Choisissez un port entre ```9111``` et ```30777```
2. **Enregistrez ce port dans votre fichier de configuration** (`kovri.conf`)
3. Créez une permission dans votre NAT/Firewall pour autoriser les connexions TCP/UDP entrantes sur ce port (Voir les notes ci-dessous si vous n'y avez pas accès)

Notes:

- **Ne partagez pas votre numéro de port avec n'importe qui car cela affecterait votre anonymat!**
- Si vous n'enregistrez pas votre port, kovri va aléatoirement en générer un nouveau à chaque démarrage (vous avez aussi le choix d'affecter le port de l'option `--port` à chaque démarrage).
- Si vous n'avez pas accès à votre NAT, réferez vous aux instructions [BUILDING](https://github.com/monero-project/kovri/blob/master/doc/BUILDING.md) selon votre système d'exploitation.

## Etape 2. Configurer Kovri

Pour la liste de toutes les options possibles:

```bashfeature requests
$ ./kovri --help
```

Pour des précisions détaillées concernant chaque option:

- `kovri.conf` fichier de configuration concernant le routeur et le client
- `tunnels.conf` fichier de configuration concernant les tunnels client/serveur

## Etape 3. Exécuter Kovri
```bash
$ cd build/ && ./kovri
```

- Attendez environ 5 minutes pour être connecté au réseau avant de faire quoi que ce soit.

## Etape 4. Nous rejoindre sur IRC
1. Démarrez votre [client IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Réglez votre client pour qu'il se connecte au port IRC de kovri (6669 par défaut). Cela vous connectera au réseau internet Irc2 (le réseau IRC de I2P).
3. Rejoignez `#kovri` et `#kovri-dev`

## Etape 5. Ouvrir le site internet de I2P (garlic-site/eepsite)
1. Ouvrez le navigateur de votre choix (de préférence compatible avec kovri)
2. Configurez votre navigateur en lisant [ces instructions](https://geti2p.net/en/about/browser-config) **mais à la place du port 4444 et 4445** changez le port proxy HHTP en **4446** et **également** le port proxy SSL en **4446**
3. Rendez-vous sur http://check.kovri.i2p pour vérifier que cela fonctionne

Notes:

- **Exactement de la même façon que Tor, SSL n'est pas nécessaire pour utiliser sans risque et de façon sûre notre réseau**
- Le protocole SSL et le paramètre outproxy ne sont pas implantés pour le moment
- Si quelqu'un vous donne une adresse .i2p qui n'est pas dans votre carnet d'adresses, utilisez le service `Jump` à l'adresse http://stats.i2p/i2p/lookup.html
- Jetez un oeil au fichier hosts.txt dans votre répertoire de données pour voir une liste de sites par défaut que vous pouvez visiter. The docker image comes with the defaults of kovri,
- Enfin, le Proxy HTTP et l'implémentation de carnets d'adresses sont en cours de développemment et ne sont pas complètement terminés.

## Etape 6. Organiser votre propre service garlic (garlic-site/eepsite)
- Lisez `tunnels.conf` pour apprendre comment définir un tunnel de serveur pour indiquer le service que vous hébergez.

## Etape 7. Eclatez-vous!enjoy
- En savoir plus à propos de Kovri dans le [Moneropedia](https://getmonero.org/knowledge-base/moneropedia/kovri).
- Ouvrez une requête de fonctionnalité ou rapportez un bug dans notre [issues tracker](https://github.com/monero-project/kovri/issues)
- En savoir plus à propos du réseau I2P sur le [site java I2P](https://geti2p.net/en/docs)

# Alternatively, Docker

## Etape 1. Installer Docker
Installer Docker est externe à ces instructions, veuillez vous réferer à la [documentation docker](https://docs.docker.com/engine/installation/)

## Etape 2. Configurer / Ouvrir Firewall
Docker est fourni avec les valeurs par défaut de kovri, cependant il peut être configurer comme expliqué dans les sections précedentes.
Vous devriez pouvoir choisir un port au hasard et l'ouvrir (voir sections précedentes).

## Etape 3. Fonctionnement

### Réglages par défaut
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

### Réglages personalisés
Where `./kovri-settings/` contains `kovri.conf` and `tunnels.conf`.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
