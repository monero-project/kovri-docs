# Monero via Kovri

## Getting Started

1. Follow the instructions for building and/or installing [Kovri](https://github.com/monero-project/kovri) & [Monero](https://github.com/monero-project/monero)
2. Review the [User Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) in your language of choice
3. Configure Kovri server and client tunnels to connect to `monerod` nodes over the I2P network

## Kovri server tunnel

First, configure a server tunnel on one node.

To setup a server tunnel, see `tunnels.conf` located in your data directory. To locate your data directory, see `kovri.conf`.

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

This configuration will open a Kovri listener on `monerod`'s default testnet P2P port. Next, read the [User Guide](https://github.com/monero-project/kovri-docs/blob/master/i18n/en/user_guide.md) for how to obtain the base32 destination address.

If you have already started your kovri router, run `$ kill -HUP $(pgrep kovri)` to load the new tunnel. More drastically, you can also do a hard restart by stopping and starting kovri.

## Kovri client tunnel

Now that the server tunnel is setup, begin the client tunnel setup by pointing to the server tunnel.

Example:

```
[XMR_Client]
type = client
address = 127.0.0.1
port = 24040
dest = your-copied-server-destination.b32.i2p
dest_port = 28080
keys = xmr-client-keys.dat
```

Repeat the process for each node you would like to connect using Kovri.

If you have already started your kovri router, run `$ kill -HUP $(pgrep kovri)` to load the new tunnel. More drastically, you can also do a hard restart by stopping and starting kovri.

## Monero P2P via Kovri

Pointing `monerod` to your new Kovri client tunnel is just as easy.

Here is an example for starting a mining testnet node:

```bash
monerod --testnet --start-mining your-testnet-wallet-address --add-exclusive-node 127.0.0.1:24040
```

If you notice connectivity issues, wait for your Kovri nodes to integrate into the network (~5-10 min after start).

## Monero RPC via Kovri

Exposing Monero's RPC service via Kovri is a similar process.

Configure a server tunnel on your Kovri node:

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

This will generate a new set of keys, and a new destination address.

To use the same destination address as P2P, simply replace `xmr-rpc-keys.dat` with `xmr-p2p-keys.dat` in the above configuration.

If you have already started your kovri router, run `$ kill -HUP $(pgrep kovri)` to load the new tunnel. More drastically, you can also do a hard restart by stopping and starting kovri.

This tunnel exposes `monerod`'s default testnet JSON RPC, and one can use Kovri's HTTP client tunnel to connect.

Here is an example for connecting with curl from a Kovri client node:

```bash
export http_proxy=127.0.0.1:4446 rpc_server=http://your-copied-rpc-destination.b32.i2p:28081
curl -X POST ${rpc_server}/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_height"}' -H 'Content-Type: application/json'
```
