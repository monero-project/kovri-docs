# Getting started with the Kovri testnet

## Prerequisites

1. `kovri` and `kovri-util` binaries in a local Kovri repository
2. Docker, with a user permissioned to create containers and networks
3. A Linux system
  * testnet may work on other platforms, but only Linux is supported currently

## Step 1: Creating the testnet

For most of the steps below, users can simply select the defaults.

1. As the Docker-permissioned user, navigate to the Kovri repo directory
  * For this guide our user will be `testuser`, and the Kovri repo is cloned into the home directory
  * Ex: `cd /home/testuser/kovri`
2. Run the testnet creation script:
  * Ex: `./contrib/testnet/testnet.sh create`
3. You will be prompted to change the Kovri repo directory
  * If your Kovri repo is not in `/tmp/kovri`, press `enter` to change
  * You must use absolute paths to specify the repo location
  * Ex: `/home/testuser/kovri`
4. You will be prompted to change the Kovri image name
  * This is the base Docker image used to build Kovri instance containers
  * By default, Kovri git information is used, but this name can be any unique name you want
  * Ex: `kovri:latest`
5. You will be prompted to change the Kovri web image name
  * This is the Docker image used to create the web server instance for serving Kovri files
  * Similar to the Kovri image name, a default name is supplied, but any unique name can be chosen
  * Ex: `kovri:web`
6. You will be prompted to select the Kovri Dockerfile
  * This is the Dockerfile used to build the Kovri Docker image
  * By default, the `Dockerfile.alpine` image is used
  * Currently there is also `Dockerfile.arch`, an Arch-based Dockerfile
  * The Alpine image is significantly smaller than the Arch image
7. You will be prompted to build the Kovri image
  * Build the image, since this is the first testnet creation
8. You will be prompted to change the web Dockerfile
  * Press `n` and `enter` to keep the default web Dockerfile
  * Currently, there is only one supported web Dockerfile: `Dockerfile.apache`
9. You will be prompted to build the web Docker image
  * Build the image, since this is the first testnet creation
10. You will be prompted to use the binaries from the repo
  * Press `enter` to use the binaries built in local repo
11. You will be prompted to build the binaries inside the container
  * This is necessary to ensure binaries work correctly when the base system is different from the Docker guest
  * If you choose not to build inside the container, Kovri binaries on the base system should be built statically
  * Only Kovri binaries built inside the container are supported
  * The usual warning applies: only choose the non-default if you know what you're doing
12. You will prompted to change the testnet output directory
  * This is the directory for storing Kovri logs and reseed files from the Docker containers
  * To keep the Kovri repo clean, choose a directory outside the repo
  * Ex: `/home/testuser/testnet`
13. You will be prompted to change the utility binary arguments
  * These arguments are used to create `RouterInfo` files for each Kovri instance
  * The default creates a floodfill router with high bandwidth
  * If you want to test a specific router configuration, change these settings
  * The usual warning applies: only choose the non-default if you know what you're doing
14. You will be prompted to change the Kovri binary arguments
  * These arguments are used for configuring Kovri binary instances at runtime
  * The default enables floodfill, disables SU3 verification and HTTPS, flushes logs to file, and enables I2PControl
  * If you want to test a specific runtime configuration, change these settings
  * The usual warning applies: only choose the non-default if you know what you're doing
15. You will be prompted to use named pipes for logging
  * Named pipes allow the user to cat a log file in the testnet output directory to get each instance's logs
  * Ex: `cat /home/testuser/testnet/kovri_010/log_pipe`
16. The Docker network `kovri-testnet`, testnet output directories, and Kovri instance `RouterInfos` will be created
17. You will be prompted to enable monitoring
  * This will enable graphical monitoring of the Kovri testnet environment
  * Currently, monitoring consists of InfluxDB (storage), cadvisor (collection), and Grafana (display)
  * Instructions for accessing the Grafana interface are output after creation
  * Work is underway to move all of this functionality into a Qt GUI

Congratulations, you have created a working testnet environment!

## Step 2: Running the Kovri testnet

Now that the testnet has been created, let's get it running.

1. Navigate to the Kovri repo
  * Ex: `cd /home/testuser/kovri`
2. Run the startup script
  * Ex: `./contrib/testnet/testnet.sh start`
3. All the testnet components will startup
4. Cat individual instance log pipes for a view of their logs:
  * Ex: `cat /home/testuser/testnet/kovri_010/log_pipe`
5. If monitoring is enabled, navigate to the Grafana endpoint in a browser:
  * Ex: `http://127.0.0.1:3030` with credentials `admin:kovri`
  * Click the `Home` icon to get a list of Dashboards
    * Details Containers: detailed statistics about container resource usage
    * Details NetDB: detailed statistics about Kovri instances' NetDB
    * Instance Overview: overall statistics of the Kovri tesnet environment
  * Each Dashboard can be filtered to show a subset of Kovri instances

## Step 3: Stopping the Kovri testnet

When the current round of testing is done, it's time to stop the testnet.

1. Navigate to the Kovri repo
  * Ex: `cd /home/testuser/kovri`
2. Run the shutdown script
  * Ex: `./contrib/testnet/testnet.sh stop`
3. You will be prompted to set a timeout interval
  * This is useful for allowing participating tunnels extra time to close
4. All of the Docker containers and network will begin shutting down

## Destroying the Kovri testnet

After all testing is done for this Kovri build, it's time to destroy the testnet.

1. Navigate to the Kovri repo
  * Ex: `cd /home/testuser/kovri`
2. Run the destruction script
  * Ex: `./contrib/testnet/testnet.sh destroy`
3. You will be prompted for a testnet working directory to destroy
  * Ex: `/home/testuser/testnet`
4. All of the Docker containers and network will begin shutting down
5. All of the Docker containers will be removed
6. You will be prompted for a Kovri testnet network to destroy
  * `kovri-testnet` is the default testnet network

## Running custom commands on the Kovri testnet

Sometimes, it may be useful to run a specific command within a Kovri Docker container.

Luckily, there's an option for that.

1. Navigate to the Kovri repo
  * Ex: `cd /home/testuser/kovri`
2. Run the execution script
  * For instance, let's say you need a bash shell
  * Ex: `./contrib/testnet/testnet.sh exec "bash"`
  * Other possibilities exist, and are left as an exploration for the reader
3. The Kovri repo is loaded into the temporary container, so one also has access to the Kovri binaries
  * Ex: From within the container: `./build/kovri` and `./build/kovri-util`
  * Note: It may be necessary to enter a bash shell, and rebuild the binaries
