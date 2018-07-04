# Getting started with the Kovri testnet

## Preamble

Kovri's testnet currently resides within a series of Docker containers and images which all communicating over a single Docker network.
This allows for private network testing and monitoring without the need to connect to the public kovri network.

## Prerequisites

- Linux development environment (Linux is currently supported)
   - See the kovri [README](https://github.com/monero-project/kovri#building) for a list of build dependencies
- [Docker](https://www.docker.com/)
   - The build user must have permissions to use Docker (added to the docker group, for example)
- A cloned repository
```bash
$ git clone --recursive https://github.com/monero-project/kovri
```

## Step 1: Create the testnet

For a complete list of options, run the `help` option:
```bash
$ ./kovri/contrib/testnet/testnet.sh help
```
You can export the listed environment variables from your shell or set them manually during setup.

Create the environment and set the values accordingly:
```bash
$ ./kovri/contrib/testnet/testnet.sh create
```
- For new developers, it is advised to use the defaults with the exception of your repository location
- See the Dockerfiles directory for available Dockerfiles to build during setup
- To keep the Kovri repo clean, choose a directory outside the repo

## Step 2a: Start the testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh start
```
For monitoring options, run the `help` for details on how to monitor.

## Step 2b: Run custom commands

**TODO(unassigned): improve this section**

To execute commands from within a container, see Docker documentation.

You can also try:
```bash
$ ./contrib/testnet/testnet.sh exec "bash"
```

## Step 3: Stop the testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh stop
```
- You should be prompted to set a container timeout interval (if env not set)
   - This is useful in case of hanging routers

## Step 4: Destroy the testnet

```bash
$ ./kovri/contrib/testnet/testnet.sh destroy
```
- You should be prompted to set the testnet directory to destroy (if env not set)
