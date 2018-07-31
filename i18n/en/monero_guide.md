# Monero via Kovri

## Getting Started

Follow the instructions for building and/or installing Kovri & Monero.

Configure server and client tunnels in Kovri to connect `monerod` nodes over the I2P network.

## Kovri server tunnel

First, configure a server tunnel on one node.

For example, add this to the server node's `kovri-data-dir/config/tunnels.conf`:

```
[XMRP2PServer]
type = server
address = 127.0.0.1
port = 28080
in_port =
keys = xmr-p2p-keys.dat
white_list =
black_list =
```

This configuration will open a Kovri listener on `monerod`'s default testnet P2P port.

After configuring the server tunnel, start Kovri to get the node's destination address:

```bash
kovri # press ^C to kill Kovri
cat kovri-data-dir/client/keys/xmr-p2p-keys.dat.b32.txt
```

## Kovri client tunnel

Copy the Base32-encoded destination, including the trailing `.b32.i2p`, to the tunnel configuration on the client node.

For example, add this to the client node's `kovri-data-dir/config/tunnels.conf`:

```
[XMRClient]
type = client
address = 127.0.0.1
port = 24040
dest = your-copied-server-destination.b32.i2p
dest_port = 28080
keys = xmr-client-keys.dat
```

Restart the Kovri node to load the new tunnel configuration.

Repeat the process for each node you would like to connect using Kovri.

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
[XMRRPCServer]
type = server
address = 127.0.0.1
port = 28081
in_port =
keys = xmr-rpc-keys.dat
white_list =
black_list =
```

This will generate a new set of keys, and a new destination address.

To use the same destination address as P2P, simply replace `xmr-rpc-keys.dat` with `xmr-p2p-keys.dat` in the above configuration.

Start Kovri, and copy your RPC server tunnel keys:

```bash
kovri # press ^C to kill Kovri
cat kovri-data-dir/client/keys/xmr-rpc-keys.dat.b32.txt
```

This tunnel exposes `monerod`'s default testnet JSON RPC, and one can use Kovri's HTTP client tunnel to connect.

Here is an example for connecting with curl from a Kovri client node:

```bash
export http_proxy=127.0.0.1:4446 rpc_server=http://your-copied-rpc-destination.b32.i2p:28081
curl -X POST ${rpc_server}/json_rpc -d '{"jsonrpc":"2.0","id":"0","method":"get_height"}' -H 'Content-Type: application/json'
```
