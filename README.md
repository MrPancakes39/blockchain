# What is blockchain?

A blockchain, originally block chain, is a growing list of records, called blocks, that are linked using cryptography. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data. By design, a blockchain is resistant to modification of the data.

# Learn Blockchains by Building One

[![Build Status](https://travis-ci.org/dvf/blockchain.svg?branch=master)](https://travis-ci.org/dvf/blockchain)

This is the source code for my post on [Building a Blockchain](https://medium.com/p/117428612f46). 

## Installation

1. Make sure [Python 3.6+](https://www.python.org/downloads/) is installed. 
2. Install requirements.
```
$ pip install -r requirements.txt
```
3. Install [pipenv](https://github.com/kennethreitz/pipenv). 
```
$ pip install pipenv 
```
4. Install enviroment requirements  
```
$ pipenv install 
``` 

5. Run the server:
    * `$ pipenv run python blockchain.py` 
    * `$ pipenv run python blockchain.py -p 5001`
    * `$ pipenv run python blockchain.py --port 5002`

6. Start Mining
```
$ curl http://0.0.0.0:5000/mine
```
7. Start a Transaction.
```
$ curl -H "Content-Type: application/json" \
   -d '{"sender": "sender_name",
        "recipient": "recipient_name",
        "amount": "amount"}' \
   -X POST http://0.0.0.0:5000/transactions/new

Output:
{
  "message": "Transaction will be added to Block 3"
}
```
9. Registering a node and Resolve chain:
```
$ curl -H "Content-Type: application/json" \
  -d '{"nodes": ["http://0.0.0.0:5000/"]}' \
  -X POST http://0.0.0.0:5000/nodes/register

Output:
{
  "message": "New nodes have been added", 
  "total_nodes": [
    "0.0.0.0:5000"
  ]
}

$ curl http://0.0.0.0:5000/nodes/resolve/
```
10. Get entire chain.
```
$ curl http://0.0.0.0:5000/chain
```

## Docker

Another option for running this blockchain program is to use Docker.  Follow the instructions below to create a local Docker container:

1. Clone this repository
2. Build the docker container

```
$ docker build -t blockchain .
```

3. Run the container

```
$ docker run --rm -p 80:5000 blockchain
```

4. To add more instances, vary the public port number before the colon:

```
$ docker run --rm -p 81:5000 blockchain
$ docker run --rm -p 82:5000 blockchain
$ docker run --rm -p 83:5000 blockchain
```

## Installation (C# Implementation)

1. Install a free copy of Visual Studio IDE (Community Edition):
https://www.visualstudio.com/vs/

2. Once installed, open the solution file (BlockChain.sln) using the File > Open > Project/Solution menu options within Visual Studio.

3. From within the "Solution Explorer", right click the BlockChain.Console project and select the "Set As Startup Project" option.

4. Click the "Start" button, or hit F5 to run. The program executes in a console window, and is controlled via HTTP with the same commands as the Python version.


## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

