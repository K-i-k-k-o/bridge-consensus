Vous pouvez miner sur:
* bzminer
* lolminer
* srbminer
* teamreadminer




# Installation

## Option 1: Build from source (native executable)
* `git clone https://github.com/K-i-k-k-o/bridge-consensus.git`

* Installez go 1.18 ou plus récent

* `cd bridge-consensus`

* entrez `cd cmd/kaspabridge/;go build .;./kaspabridge`

ouvrez les ports:
5555
10106

## Option 2: Docker all-in-one


Installez docker

* `git clone https://github.com/K-i-k-k-o/bridge-consensus.git`

* `cd bridge-consensus`  

* entrez la commande: 

`docker compose -f docker-compose-all-src.yml up -d --build` 

vous pouvez modifier les parametres dans [config.yaml](cmd/kaspabridge/config.yaml) ou dans  [docker-compose-all-src.yml](docker-compose-all-src.yml) 

ouvrez les ports:
5555
3000
9090
10106

pour acceder a grafana: <http://ip_du_bridge:3000/d/x7cE7G74k1/ksb-monitoring> avec user/pass: admin/admin


## Option 3: Docker bridge only

*Best option for users who want docker encapsulation, and don't need reporting, or are already using Grafana/Prometheus.  Requires a local copy of this repository, and docker installation.*

* [Install Docker](https://docs.docker.com/engine/install/) using the appropriate method for your OS.  The docker commands below are assuming a server type installation - details may be different for a desktop installation.

* Clone this repository using git (`git clone https://github.com/rdugan/kaspa-stratum-bridge.git`) or download and unpack the [zip file](https://github.com/rdugan/kaspa-stratum-bridge/archive/refs/heads/main.zip)

* Enter the 'kaspa-stratum-bridge' directory and type the command `docker compose -f docker-compose-bridge-src.yml up -d --build` [^2]. This will run the bridge assuming a local kaspad node with default port settings, and listen on port 5555 for incoming stratum connections.  These settings can be updated in the [config.yaml](cmd/kaspabridge/config.yaml) file, or overridden by modifying/adding/deleting the parameters in the 'command' section of the [docker-compose-bridge-src.yml](docker-compose-bridge-src.yml) file.  No further services will be enabled.

[^2]: This command builds the bridge component from source, rather than the previous behavior of pulling down a pre-built image.  You may still use the pre-built image by issuing the command `docker run -p 5555:5555 onemorebsmith/kaspa_bridge:latest`, but it is not guaranteed to be up to date, so compiling from source is the better alternative.


# Configuration

Configuration for the bridge is done via the [config.yaml](cmd/kaspabridge/config.yaml) file in the same directory as the executable, or `./cmd/kaspabridge` from the project root if building from source / using docker.  Available parameters are as follows:



