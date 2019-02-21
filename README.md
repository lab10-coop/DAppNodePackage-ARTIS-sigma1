# ARTIS sigma1 mainnet DAppnode Package

[![DAppNodeStore Available](https://img.shields.io/badge/DAppNodeStore-Available-brightgreen.svg)](http://my.admin.dnp.dappnode.eth/#/installer/artis-sigma1.public.dappnode.eth)

This provides a [ARTIS](https://artis.eco) sigma1 Fullnode as a [DAppnode Package](https://dappnode.io/)

## Install on DAppnode

To install the latest official package on an existing  DAppnode, make sure you are connected to it's VPN and visit http://my.admin.dnp.dappnode.eth/#/installer/artis-sigma1.public.dappnode.eth.
In order To install a custom build, look up the "Building as DAppnode Package" section.

## Building  as Docker

### Prerequisites

- git

   Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

   Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding current user to docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

   Install [docker-compose](https://docs.docker.com/compose/install)
   
**Note**: Make sure you can run `git`, `docker ps`, `docker-compose` without any issue and without sudo command.


## Buidling

`docker-compose build`

## Running

### Start

`docker-compose up -d`

### View logs

`docker-compose logs -f`

### Stop

`docker-compose down`

## Extra options

You can write extra options on the adminui or edit the `docker-compose.yml` and add extra options, such as:
```
 - EXTRA_OPTS=--tracing on
```
Look up https://wiki.parity.io/Configuring-Parity-Ethereum#cli-options-for-parity-ethereum-client for more details.


## Building as DAppnode Package

### Prerequisites

- same as "Buidling as Docker"
- install [DAppNodeSDK](https://github.com/dappnode/DAppNodeSDK)
- be connected to your DAppnode (e.g. via VPN)

run
```
dappnodesdk build
```

to test your newly build, use the given IPFS Hash to install the DNP on your Dappnode.

For more information about building and deploying DAppnode Packages, checkout the [DAppNodeSDK](https://github.com/dappnode/DAppNodeSDK) repository.

## Connect using web3js

If the package is running and you're connected to your dappnode you can use:
```
var Web3 = require('web3');
var web3 = new Web3('ws://artis-sigma1.public.dappnode.eth:8546')
web3.eth.getBlockNumber().then(console.log)
```
In case you are running it locally:
```
var Web3 = require('web3');
var web3 = new Web3('ws://127.0.0.1:8546')
web3.eth.getBlockNumber().then(console.log)
```

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details
