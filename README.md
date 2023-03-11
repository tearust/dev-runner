
## Pre-requisites
- git
- docker: install docker and "docker compose"

## Running the tests

### Prepare your custom actors
If you have any custom wasm actors needed to be loaded, please place them in the directory `local` (if test on A node should in `a-node` subdirectory, and if test on B node should in `b-node` subdirectory).

### Run with server
Server mode will run the tests without interactions. You won't be able use CLI in this case. 

You can run with server mode simply like the following:
```
docker compose up
```
(If you installed `docker-compose` please replace the `docker compose up` command with `docker-compose up`)

After started you should have two nodes (one is A node and one is B node) running within the docker compose services. 
You can test HTTP interface of the B nodes with default port of "8000" simply like the following:
```
curl -H "Content-Type: application/json" -d '{"actor": "someone.sample", "address": "0x0000000000000000000000000000000000000000"}' http://localhost:8000/say-hello
```

And you can test HTTP interface of the A nodes with default port of "8001" simply like the following:
```
curl -H "Content-Type: application/json" -d '{"actor": "someone.sample", "address": "0x0000000000000000000000000000000000000000"}' http://localhost:8001/say-hello
```
