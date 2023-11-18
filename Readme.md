# 👽 proyecto Ethereum Web2.5 Code Crypto 👽

Let's start! 💪🏻

```
Insatll geth - brew install ethereum
```

Create a pwd.txt with 123456 string

```
geth --datadir nodo1 account new --password ./pwd.txt
geth --datadir nodo2 account new --password ./pwd.txt
geth --datadir nodo3 account new --password ./pwd.txt
```

(Creation of Genesis file "genesis.json" with copy/paste not from puppeth (deprecated))

```
bootnode --genkey=boot.key
bootnode --verbosity=9 --nodekey=boot.key
```

```
geth --datadir nodo1 init genesis.json
geth --datadir nodo2 init genesis.json
geth --datadir nodo3 init genesis.json
```

(set en each genesis also in extra data each account if not work due to sealing error)

Now we setting each node with these configurations

```
geth --authrpc.port 9552 --ipcpath "\.\pipe\nodo1" --datadir nodo1 --syncmode full --http --http.api admin,eth,miner,net,txpool,personal --http.port 8545 --allow-insecure-unlock --unlock "<<wallet Node 1>>" --password pwd.txt --port 30034 --bootnodes "enode://d91d4671122f936a6a3d23a9287cfbc3290991b166c4e0c8120b3455b469464e13177f8ea298695eead4b29ba43736141f733c011cc9231b4d027aead85c2fbe@127.0.0.1:0?discport=30301" --mine --miner.etherbase <<wallet Node 1>> --nodiscover
```
```
geth --authrpc.port 9553 --ipcpath "\.\pipe\nodo2" --datadir nodo2 --syncmode full --http --http.api admin,eth,miner,net,txpool,personal --http.port 8546 --allow-insecure-unlock --unlock "<<wallet Node 2>>" --password pwd.txt --port 30035 --bootnodes "enode://d91d4671122f936a6a3d23a9287cfbc3290991b166c4e0c8120b3455b469464e13177f8ea298695eead4b29ba43736141f733c011cc9231b4d027aead85c2fbe@127.0.0.1:0?discport=30301"
```
```
geth --authrpc.port 9554 --ipcpath "\.\pipe\nodo3" --datadir nodo3 --syncmode full --http --http.api admin,eth,miner,net,txpool,personal,web3 --http.port 8547 --allow-insecure-unlock --unlock "<<wallet Node 3>>" --password pwd.txt --port 30036 --bootnodes "enode://d91d4671122f936a6a3d23a9287cfbc3290991b166c4e0c8120b3455b469464e13177f8ea298695eead4b29ba43736141f733c011cc9231b4d027aead85c2fbe@127.0.0.1:0?discport=30301" --mine --miner.etherbase <<wallet Node 3>>
```

To take a look at each node:

```
geth attach http://localhost:8545
```

For use Js:

```
yarn init -y
yarn add web3
```


To access GraphQL

[http://localhost:8547/graphql/ui] (http://localhost:8547/graphql/ui)
