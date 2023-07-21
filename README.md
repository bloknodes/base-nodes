# base-nodes
Blockchain Nodes Base Container Images Repository

## About

The base container images contains the binary to run the blockchain node of choice.

## Versions

**Bitcoin**:

- Version: `0.21.2`
- Docker Image: `bloknodes/base-nodes:bitcoin-0.21.2`

**Dogecoin**:

- Version: `1.14.6`
- Docker Image: `bloknodes/base-nodes:dogecoin-1.14.6`

**Litecoin**:

- Version: `0.21.2.1`
- Docker Image: `bloknodes/base-nodes:litecoin-0.21.2.1`

**Ethereum**:

- Version: `1.12.0`
- Docker Image: `bloknodes/base-nodes:ethereum-1.12.0` (geth)

## Binary Paths

All nodes has their binary placed in `/usr/bin/`, you can look at the respective dockerfiles.