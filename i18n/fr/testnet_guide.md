# Débuter avec le réseau de test de Kovri

## Préambule

Le réseau de test de Kovri se situe actuellement au sein d'une série de conteneurs et images Docker qui communiquent tous sur un unique réseau Docker.
Cela permet de faire des tests et de la supervision privée sans avoir besoin de se connecter au réseau publique de Kovri.

## Prérequis

- Environnement de développement Linux (Linux est actuellement supporté)
   - Voir le [README](https://github.com/monero-project/kovri#building) de Kovri pour une liste de dépendances de compilation
- [Docker](https://www.docker.com/)
   - L'utilisateur qui compilera doit avoir les droits d'utilisation de Docker (en étant ajouté au groupe Docker par exemple)
- Un dépôt cloné
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

## Étape 1 : Créer le réseau de test

Pour une liste exhaustive d'option, utilisez l'option `help` :
```bash
$ ./kovri/contrib/testnet/testnet.sh help
```
Vous pouvez exporter les variables d'environnement listées depuis votre shell ou les définir manuellement pendant la configuration.

Créer l'environnement et définir les valeurs en conséquence :
```bash
$ ./kovri/contrib/testnet/testnet.sh create
```
- Pour les nouveaux développeurs, il est recommandé d'utiliser les valeurs par défaut, à l'exception de l'emplacement de votre dossier de dépôt
- Voir le répertoire *Dockerfiles* pour les fichiers Docker à compiler pendant la configuration
- Pour garder le dossier du dépôt Kovri propre, choisissez un répertoire en dehors du dépôt

## Étape 2a : Démarrer le réseau de test

```bash
$ ./kovri/contrib/testnet/testnet.sh start
```
Pour les options de supervision, lancez `help` pour des détails sur comment superviser.

## Étape 2b : Lancer les commandes personnalisées

**À faire (non assigné): améliorer cette rubrique**

Pour exécuter des commandes depuis un conteneur, voir la documentation de Docker.

Vous pouvez également essayer :
```bash
$ ./contrib/testnet/testnet.sh exec "bash"
```

## Étape 3 : Arrêter le réseau de test

```bash
$ ./kovri/contrib/testnet/testnet.sh stop
```
- Vous devriez être invité à définir un délai de temporisation du conteneur (si la variable d'environnement n'est pas définie)
   - C'est utile en cas de routeur suspendu

## Étape 4 : Détruire le réseau de test

```bash
$ ./kovri/contrib/testnet/testnet.sh destroy
```
- Vous devriez être invité à définir le répertoire du réseau de test à détruire (si la variable d'environnement n'est pas définie)
