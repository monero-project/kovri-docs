# Monero à travers Kovri

## Démarrer

1. Suivez les instructions pour compiler et/ou installer [Kovri](https://github.com/monero-project/kovri) & [Monero](https://github.com/monero-project/monero)
2. Étudiez le [Guide Utilisateur](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/user_guide.md) dans la langue de votre choix
3. Configurez les tunnels serveur et client de Kovri pour vous connecter aux nœuds `monerod` à travers le réseau I2P

## Tunnel serveur de Kovri

Tout d'abord, configurez un tunnel serveur sur un nœud.

Pour configurer un tunnel serveur, voir le fichier `tunnels.conf` situé dans votre répertoire de données. Pour localiser votre répertoire de données, voir `kovri.conf`.

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

Cette configuration va ouvrir un port d'écoute de Kovri sur le port P2P testnet par défaut de `monerod`. Ensuite, lisez le [Guide Utilisateur](https://github.com/monero-project/kovri-docs/blob/master/i18n/fr/user_guide.md) pour savoir comment obtenir une adresse de destination Base32.

Si vous avez déjà démarré votre routeur kovri, lancez `$ kill -HUP $(pgrep kovri)` pour charger le nouveau tunnel. Plus radicalement, vous pouvez également faire un redémarrage forcé en arrêtant et redémarrant kovri.

## Tunnel client Kovri

Maintenant que le tunnel serveur est configuré, commencez la configuration du tunnel client en le faisant pointer vers le tunnel serveur.

Exemple :

```
[XMR_Client]
type = client
address = 127.0.0.1
port = 24040
dest = your-copied-server-destination.b32.i2p
dest_port = 28080
keys = xmr-client-keys.dat
```

Répétez le procéder pour chaque nœud auquel vous voulez vous connecter en utilisant Kovri.

Si vous avez déjà démarré votre routeur kovri, lancez `$ kill -HUP $(pgrep kovri)` pour charger le nouveau tunnel. Plus radicalement, vous pouvez également faire un redémarrage forcé en arrêtant et redémarrant kovri.

## Monero P2P à travers Kovri

Faire pointer `monerod` vers votre nouveau tunnel client Kovri est tout aussi simple.

Voici un exemple pour démarrer un nœud testnet d'extraction minière :

```bash
monerod --testnet --start-mining your-testnet-wallet-address --add-exclusive-node 127.0.0.1:24040
```

Si vous remarquez des problèmes de connectivité, attendez qur vos noeuds Kovri aient intégré le réseau (~5-10 min après démarrage)

## Monero RPC à travers Kovri

Exposer le service RPC de Monero à travers Kovri est un processus similaire.

Configurez un tunnel serveur sur votre nœud Kovri :

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

Cela va générer un nouveau jeu de clefs, et une nouvelle adresse de destination.

Pour utiliser la même adresse de destination que pour P2P, remplacez simplement `xmr-rpc-keys.dat` par `xmr-p2p-keys.dat` dans la configuration ci-dessus.

Si vous remarquez des problèmes de connectivité, attendez que vos nœuds Kovri aient intégré le réseau (~5-10 min après démarrage)

Ce tunnel expose l'API JSON RPC testnet par défaut de Monero, et chacun peut utiliser le tunnel client HTTP de Kovri pour se connecter.

Voici un exemple pour se connecter avec curl depuis un nœud client de Kovri :

```bash
export http_proxy=127.0.0.1:4446 rpc_server=http://your-copied-rpc-destination.b32.i2p:28081
curl -X POST ${rpc_server}/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_height"}' -H 'Content-Type: application/json'
```
