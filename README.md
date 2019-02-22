# ARTIS sigma1 DAppNode Package

[![DAppNodeStore Available](https://img.shields.io/badge/DAppNodeStore-Available-brightgreen.svg)](http://my.admin.dnp.dappnode.eth/#/installer/artis-sigma1.public.dappnode.eth)

Provides an [ARTIS](https://artis.eco) sigma1 Fullnode as a [DAppNode Package](https://dappnode.io/)

## Install on DAppNode

To install the latest official ARTIS package on a DAppNode, make sure you are connected to its VPN and visit `http://my.admin.dnp.dappnode.eth/#/installer/artis-sigma1.public.dappnode.eth`.

You can add extra options in the DAppNode UI such as:
```
EXTRA_OPTS=--tracing on
```
Please look up the [Parity documentation](https://wiki.parity.io/Configuring-Parity-Ethereum#cli-options-for-parity-ethereum-client) for available options.

## Connect using web3js

If the ARTIS DAppNode package is installed and running and you are connected to your DAppNode via VPN you can use:
```
var Web3 = require('web3');
var web3 = new Web3('ws://artis-sigma1.public.dappnode.eth:8546')
web3.eth.getBlockNumber().then(console.log)
```
In case you are running the ARTIS Docker container locally:
```
var Web3 = require('web3');
var web3 = new Web3('ws://127.0.0.1:8546')
web3.eth.getBlockNumber().then(console.log)
```

## Buidling the DAppNode Package

### Prerequisites

- same as described in the "Buidling as Docker" section below
- [DAppNodeSDK](https://github.com/dappnode/DAppNodeSDK) installed
- be connected to your DAppNode (e.g. via VPN)

### Run
```
dappnodesdk build
```

to test your new build, use the given IPFS hash to install the DAppNode package on your DAppNode.

For more information about building and deploying DAppNode packages we refer to the Readme of the [DAppNodeSDK](https://github.com/dappnode/DAppNodeSDK) repository.

## Buidling as Docker

If you prefer to build the ARTIS Docker image and run it as a Docker container yourself please follow the instructions described in this section.

### Prerequisites

- git

   Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

   Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding the current user to the docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

   Install [docker-compose](https://docs.docker.com/compose/install)
   
**Note**: Make sure you can run `git`, `docker ps` and `docker-compose` without any issues and without the sudo command.


### Buidl

`docker-compose build`

### Run

`docker-compose up -d`

### View Logs

`docker-compose logs -f`

### Stop

`docker-compose down`

### Extra options

You can add extra options to the `docker-compose.yml`, for example:
```
        environment:
            - EXTRA_OPTS=--tracing on
```
Please look up the [Parity documentation](https://wiki.parity.io/Configuring-Parity-Ethereum#cli-options-for-parity-ethereum-client) for available options.

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details
