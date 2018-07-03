# Alors, vous avez installé Kovri. Et maintenant?

## Etape 1. Ouvrir votre NAT/Firewall
1. Choisissez un port entre `9111` et `30777`
2. **Enregistrez ce port dans votre fichier de configuration** (`kovri.conf`)
3. Créez une permission dans votre NAT/Firewall pour autoriser les connexions TCP/UDP entrantes sur ce port (Voir les notes ci-dessous si vous n'y avez pas accès)

Notes:

- Si vous n'enregistrez pas votre port, Kovri va aléatoirement en générer un nouveau à chaque démarrage (vous avez aussi le choix d'affecter le port de l'option `--port` à chaque démarrage).
- Si vous n'avez pas accès à votre NAT, référez-vous au [guide de compilation](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/building.md) relatif à votre système d'exploitation.
- **Ne partagez pas votre numéro de port avec n'importe qui car cela affecterait votre anonymat!**

## Etape 2. (Recommandé) Sécurité Opérationnelle

- Créez et dédiez un utilisateur `kovri` à l'exécution de Kovri
- Si vous utilisez Linux, considérez l'utilisation d'un noyau durci (comme [grsec](https://en.wikibooks.org/wiki/Grsecurity) avec RBAC)
- Après l'installation des ressources nécessaires dans votre répertoire Kovri, envisagez la mise en place de contrôles d'accès appropriés avec [setfacl](https://linux.die.net/man/1/setfacl), [umask](https://en.wikipedia.org/wiki/Umask), ou tout autre solution d'ACL de votre OS.
- Ne partagez jamais votre numéro de port avec quiconque dans la mesure où cela impacterait votre anonymat !

**Remarque : voir kovri.conf pour déterminer votre répertoire Kovri sur Linux/OSX/Windows**

## Etape 3. Configurer Kovri

Pour la liste de toutes les options possibles:

```bash
$ ./kovri --help
```

Pour des précisions détaillées concernant chaque option:

- `kovri.conf` fichier de configuration concernant le routeur et le client
- `tunnels.conf` fichier de configuration concernant les tunnels client/serveur

## Etape 4. (Optionnelle) Configurer des tunnels

En bref, les *tunnels client* sont des tunnels que vous utilisez pour vous connecter à d'autre services er les *tunnels serveur* sont utilisés lorsque vous hébergez un(des) service(s) (et que d'autres se connectent à votre(vos) service(s)).

Par défaut, vous aurez des tunnels client configurés pour IRC (Irc2P) et e-mail (i2pmail). Pour ajouter/supprimer des tunnels client, voir `tunnels.conf`.

Lorsque vous créez un(des) tunnel(s) serveur, vous avez besoin de créer des *clefs privées persistantes*. Pour ce faire, dé-commentez ou créez `keys = vos-clefs.dat` et remplacez `vos-clef` par un nom approprié. **Ne partagez votre fichier privé `.dat` avec quiconque, and assurez-vous d'en faire une sauvegarde !**

Une fois configurée, votre [Adresse Base32](https://getmonero.org/resources/moneropedia/base32-address) sera visible dans vos logs après le démarrage de Kovri. Vous pouvez également trouvée l'adresse dans un fichier texte accompagné du fichier de clefs privées dans le sous-répertoire `client/keys` de votre répertoire Kovri. L'adresse dans ce fichier texte `.txt` peut être partagée sans risque afin que d'autres puissent se connecter à votre service.

Exemple :

- Fichier de clefs privées : `client/keys/vos-clefs.dat`
- Adresse [Base32](https://getmonero.org/resources/moneropedia/base32-address)/[Base64](https://getmonero.org/resources/moneropedia/base64-address) publique : `client/keys/vos-clefs.dat.txt`

**Remarque : voir kovri.conf pour déterminer votre répertoire Kovri sur Linux/OSX/Windows**

## Etape 5. (Optionnelle) Inscrire votre nouveau [eepsite](https://getmonero.org/resources/moneropedia/eepsite)

**Stop ! Tant que [#498](https://github.com/monero-project/kovri/issues/498) n'est pas résolu, n'envisagez d'inscrire votre service qu'avec Kovri and *pas* stats.i2p !**

- Ouvrir une nouvelle demande avec `[Subscription Request] votre-hôte.i2p` (remplacez `votre-hôte.i2p` avec le nom d'hôte de votre choix) sur le [*Tracker d'Issues*](https://github.com/monero-project/kovri/issues/)
- Dans le corp de votre demande, collez le contenu de votre fichier `.txt` publique mentionné dans l'étape précédente
- Après revue, vous ajouterez votre hôte ratifierez votre adhésion
- Terminé !

## Etape 6. Exécuter Kovri
```bash
$ cd build/ && ./kovri
```
- Attendez environ 5 minutes pour être connecté au réseau avant d'essayer d'utiliser les services

## Etape 7. Nous rejoindre sur IRC
1. Démarrez votre [client IRC](https://en.wikipedia.org/wiki/List_of_IRC_clients)
2. Réglez votre client pour qu'il se connecte au port IRC de Kovri (6669 par défaut). Cela vous connectera au réseau internet Irc2P (le réseau IRC de I2P).
3. Rejoignez `#kovri` et `#kovri-dev`

## Etape 8. Ouvrir un site internet de I2P (garlic-site/eepsite)
1. Ouvrez le navigateur de votre choix (de préférence dévoué à l'usage de Kovri)
2. Configurez votre navigateur en lisant [ces instructions](https://geti2p.net/fr/about/browser-config) **mais à la place du port 4444 et 4445** changez le port proxy HHTP en **4446** et *également* le port proxy SSL en **4446**
3. Rendez-vous sur http://check.kovri.i2p pour vérifier que cela fonctionne

Remarques :

- **Exactement de la même façon que Tor, SSL n'est pas nécessaire pour utiliser sans risque et de façon sûre le réseau**
- Le protocole SSL et le service outproxy ne sont pas implémentés pour le moment
- Si quelqu'un vous donne une adresse .i2p qui n'est pas dans votre carnet d'adresses, utilisez le service `Jump` à l'adresse http://stats.i2p/i2p/lookup.html
- Jetez un œil au fichier hosts.txt dans votre répertoire de données pour voir une liste de sites par défaut que vous pouvez visiter.
- Enfin, le Proxy HTTP et le carnet d'adresse sont en cours de développement.

## Etape 9. Amusez-vous!
- En savoir plus à propos de Kovri dans le [Moneropedia](https://getmonero.org/resources/moneropedia/kovri.html).
- Ouvrez une requête de fonctionnalité ou rapportez un bug dans notre [issues tracker](https://github.com/monero-project/kovri/issues)
- En savoir plus à propos du réseau I2P sur le [site java I2P](https://geti2p.net/en/docs)

# Les options de conteneurs

## Snapcraft

Sur un système Linux, utilisez snapcraft pour un déploiement simplifié.

### Etape 1. Obtenez le dépot des sources Kovri

```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

### Etape 2. Installez snapcraft

- Référez-vous au gestionaire de paquets de votre distribution pour snapcraft et [snapd](https://snapcraft.io/docs/core/install)

Sur Ubuntu, lancez simplement :
```bash
$ sudo apt-get install snapcraft
```

### Etape 3. Créez le snap

```bash
$ cd kovri/ && snapcraft && sudo snap install *.snap --dangerous
```
Remarque : l'option --dangerous est nécessaire uniquement car le snap n'a pas été signé (vous le compilez vous-même de toute façon, donc ça ne devrait pas être un problème)

### Etape 4. Lancez Kovri avec snapcraft

```bash
$ snap run kovri
```

## Docker

### Etape 1. Installer Docker
Installer Docker est hors du champ de ce document, veuillez vous référer à la [documentation docker](https://docs.docker.com/engine/installation/)

## Etape 2. Configurer / Ouvrir le Firewall

L'image docker est fournie avec les valeurs par défaut de Kovri, cependant elle peut être configurée comme expliqué dans les sections précédentes.

Vous devriez pouvoir choisir un port au hasard et l'ouvrir (voir sections précédentes).

### Etape 3. Fonctionnement

#### Réglages par défaut
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT geti2p/kovri
```

#### Réglages personnalisés
Where `./kovri-settings/` contains `kovri.conf` and `tunnels.conf`.
```bash
KOVRI_PORT=42085 && sudo docker run -p 127.0.0.1:4446:4446 -p 127.0.0.1:6669:6669 -p $KOVRI_PORT --env KOVRI_PORT=$KOVRI_PORT -v kovri-settings:/home/kovri/.kovri/config:ro geti2p/kovri
```
