---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: About Polkashots
description: 

# Author box
author:
    title: Brought to you by MIDL.dev
    title_url: 'https://midl.dev/'
    external_url: true
    description: A proof-of-stake infrastructure company - we help you validate your DOT. <a href="https://MIDL.dev/polkadot" target="_blank">Learn more</a>.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    home:
        content: Previous page
        url: 'https://polkashots.io/'
---

### What is this ?

[polkadot](https://polkadot.network) and [kusama](https://kusama.network) are proof-of-stake blockchain protocols.

This website helps people operating polkadot and kusama nodes to synchronize new nodes, so they are operational faster.

This project was sponsored by a grant from the [Web 3 Foundation](https://web3.foundation/).

### How to use

When starting a polkadot node for the first time, you must wait for it to sync. The process can take hours or days. Alternatively, if you want a fully synced node faster, you may import a fully synced database.

We provide snapshots of pre-synced Polkadot and Kusama databases updated regularly - twice a day on average.

They are compressed using the 7z compression algorithm.

In order to fully automate your recovery mechanism, we provide **permalinks**: URLs that never change and reliably point to a recent snapshot.

In the instructions below, we assume that the user is `polkadot` and the home directory is `/home/polkadot`.

To download a recent snapshot of polkadot database, simply do:

```
wget https://dot.polkashots.io/snapshot
```

This link redirects, so if using `curl`, make sure to pass the `-L` parameter to follow http redirects.

You must the uncompress this snapshot with the `7z` utility. As `polkadot` user, run:

```
7z x <file> -o/home/polkadot/.local/share/polkadot/chains/polkadot
```

This will create a folder `/home/polkadot/.local/share/polkadot/chains/polkadot/paritydb`.

For Kusama, decompress command is:

```
7z x <file> -o/home/polkadot/.local/share/polkadot/chains/ksmcc3
```

### Video instructions

These intstructional videos explain how to restore from a snapshot:

* [Secure validator - Follow-up #2 - Snapshot](https://www.youtube.com/watch?v=Egbf5biQGNc)
* [Secure validator - Follow-up #3 - From zero to fully synced](https://www.youtube.com/watch?v=UE6GJGvIur8)

### Database formats

Like any [Substrate](https://substrate.dev) chain, Polkadot supports two database backends:

* [RocksDb](https://rocksdb.org/) is the default option,
* [ParityDb](https://github.com/paritytech/parity-db) is more efficient but also more experimental.

We provide Polkadot snapshots for both database backends: [RocksDb polkadot snapshots](https://dot-rocksdb.polkashots.io) and [ParityDb polkadot snapshots](https://dot.polkashots.io).

We also provide [Kusama RocksDb snapshots](http://ksm-rocksdb.polkashots.io).

### Pruning

These snapshots are **not** archive snapshots. You must run your validator with the `--unsafe-pruning` argument after starting your node from the snapshots provided here. The `--unsafe-pruning` mode is sufficient to run a validator node.

Substrate has an `export-blocks` and `import-blocks` option, but these snapshots do not make use of it. The `import-blocks` function verifies every block, which is as slow as an initial sync. Instead, we provide raw database backend files because setup is faster than with the block import function.

### How does it work ?

The snapshot generation engine is deployed on [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine).

All source code is [open source](https://github.com/midl-dev/polkadot-snapshot-generator) so anyone can deploy a separate snapshot generator setup in the cloud.


### Brought to you by MIDL.dev

We are [MIDL.dev](https://midl.dev), a blockchain infrastructure company.

We maintain a suite of open-source software projects to deploy secure bakers and nodes.

Contact us if you need help with:

* becoming a validator
* deploying a polkadot parachain in the cloud
* generating snapshots for your parachain

### Disclaimers

Users are solely responsible for any risks associated with usage of the polkadot network. Users should do their own research to determine if polkadot is the appropriate platform for their needs and should apply judgement and care in their network interactions.

Unless required by applicable law or agreed to in writing, MIDL.dev provides a service on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied, including, without limitation, any warranties or conditions of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A PARTICULAR PURPOSE. You are solely responsible for determining the appropriateness of using our services.
