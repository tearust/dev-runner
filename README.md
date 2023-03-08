
## Pre-requisites
- git
- docker: install docker and "docker compose"
- Node.js & hardhat: please following the hardhat install tutorial [here](https://hardhat.org/tutorial)

## Prepare dummy layer1

We should prepare the dummy(local) ethereum layer before running the tests.

First clone our layer1 contract repository:
```
git clone https://github.com/tearust/eth_layer1
```

Then cd into the contract repository and run the following to start dummy layer1:
```
npx hardhat node --hostname 0.0.0.0
```

Finally, in another terminal (and the same directory) run the following to init contracts:
```
npx hardhat --network localdocker run scripts/deploy_alpha.js
```

## Running the tests

### Prepare your custom actors
If you have any custom wasm actors needed to be loaded, please place them in the directory `local`.

### Run with server mode
Server mode will run the tests without iteractions:
```
cd single-node
docker compose up
```
(If you installed `docker-compose` please replace the `docker compose up` command with `docker-compose up`)

### Run the interactive mode
First run the whole docker compose:
```
cd single-cli
docker compose up
```
(If you installed `docker-compose` please replace the `docker compose up` command with `docker-compose up`)

Then enter into the client docker service using the following command:
```
docker exec -it parent-instance-client /bin/bash
```

Then use the following command to start client manually:
```
./app
```

After all actors initialized successfully, you can type commands to interact with the runtime like the following:
```
libp2p id
```
and the above command will give you the current node's connection id.