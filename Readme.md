## Install Tendermint
Please see this tutorial : [tendermint](tendermint/Install.md)

## Create kvstore application on top of tendermint.


### What is kvstore?
 The kvstore is an application on top of tendermint.
 
As you see, Tendermint Core is written in the Golang Programming language. Running this kvstore built in Go inside the same process as tendermint core will give you the best possible performance.
 
Tendermint Core communicates with the application through the Application BlockChain Interface (ABCI).  All message types are defined in the [protobuf file](https://github.com/tendermint/tendermint/blob/master/proto/tendermint/abci/types.proto).

The kvstore application that we will create is installed at the same time as `abci-cli` above.The kvstore just stores transactions in a merkle tree. The merkle tree (hash tree) in cryptography and computer science is a tree in which every leaf node is labelled with the cryptographic hash of a data block, and every non-leaf node is labelled with the cryptographic hash of the labels of its child nodes. Please click [here](https://en.wikipedia.org/wiki/Merkle_tree).

### How to create and use kvstore.

The source code is defined [here]().

The kvstore is been running like this:

start application like this:

```sh
abci-cli kvstore
```
And in another terminal, run

```sh
abci-cli echo hello
abci-cli info
```

You'll see something like:

```sh
-> data: hello
-> data.hex: 68656C6C6F
```

and:

```sh
-> data: {"size":0}
-> data.hex: 7B2273697A65223A307D
```

```sh
abci-cli deliver_tx "kvstore_example"
abci-cli commit
abci-cli info
```

if then:

```sh
-> code: OK
-> data: {"size":1}
-> data.hex: 0x7B2273697A65223A317D
```

also:

```sh
abci-cli query "kvstore_example"
```

```sh
-> code: OK
-> log: exists
-> height: 2
-> value: kvstore_example
-> value.hex: 615373
```

An ABCI application must provide two things:

- a socket server
- a handler for ABCI messages

When we run the `abci-cli` tool we open a new connection to the
application's socket server, send the given ABCI message, and wait for a
response.


#Note

This [web application]() will be integrated with kvstore for Tendermint Core application.








 


