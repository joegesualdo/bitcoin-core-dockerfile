# Bitcoin Core Dockerfile  
> Dockerfile for a bitcoin core container

---

**⚠️ This is experimental. Please use at your own risk.⚠️**

---

## Build
> Note: tag name can be whatever you'd like
```
$docker build . -t bitcoin-core-docker:latest
```
## Run
> If you'd like to run the container, make sure to add a directory to hold the bitcoin data (i.e. /btcdata) and a bitcoin config file (bitcoin.conf) and make sure to connect them to the container. Also, make sure you expose the ports to your local machine to query the node (i.e. make rpc port accessible).
```
$ docker run --name bitcoin-core -v $(pwd)/btcdata:/root/.bitcoin -v $(pwd)/bitcoin.conf:/root/.bitcoin/bitcoin.conf -p 127.0.0.1:18332:18332/tcp -p 127.0.0.1:18333:18333/tcp -it -d bitcoin-core-docker:latest
```
## Start the Bitcoin core node
1) ssh into the container
```
$ docker exec -it bitcoin-core /bin/bash
```
2) Start bitcoind from inside the container
```
/usr/local/bin/bitcoind -testnet -rest=1 -server=1 -printtoconsole -txindex=1
```

## License
MIT © [Joe Gesualdo]()
