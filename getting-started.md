---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: About XTZ-shots
description: 

# Author box
author:
    title: Brought to you by Oxhead Alpha
    title_url: 'https://medium.com/the-aleph'
    external_url: true
    description: A Tezos core development company, providing common goods for the Tezos ecosystem. <a href="https://medium.com/the-aleph" target="_blank">Learn more</a>.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    home:
        content: Previous page
        url: 'https://xtz-shots.io/index.html'
---

### About XTZ-Shots

[Tezos](https://tezos.com) is a proof-of-stake blockchain.

This website helps people operating Tezos nodes to synchronize to the head of the chain, so they are operational faster.

## What is a snapshot?

A Tezos snapshot is a package containing Tezos chain data necessary for the node to synchronize to the network and validate blocks.

In the absence of a snapshot, running a Tezos node for the first time requires syncing the historical mainnet chain from its genesis on June 2018, which takes several days. Consequently, most people spinning up new nodes use a snapshot.

Importing a Tezos snapshot performs a sanity check of its contents. Consequently, it still takes a bit of time to import a snapshot- currently up to one hour on mainnet.

[Read more on the Tezos documentation](https://tezos.gitlab.io/user/snapshots.html)

### How to use

We provide **permalinks**: URLs that never change and reliably point to a recent snapshot. This allows to write automation where your node may automatically download a recent snapshot at first boot.

For example, to download a recent rolling snapshot of Tezos mainnet, simply do:

```bash
wget https://mainnet.xtz-shots.io/rolling
```

The run the import command.

All commands can be found in the [snapshot page](https://mainnet.xtz-shots.io).

## What is a tarball ?

In addition to snapshot, we provide tarballs. Unlike snapshots, tarballs are **raw archives of the Tezos node data directory**, in lz4 format.

We provide 2 kind of tarballs:

### Rolling tarballs

Rolling tarballs are generated from our rolling snapshots. We take a rolling snapshot, import it into a node, then package its data directory into a tarball.

Effectively, by importing a tarball instead of a snapshot, you skip the snapshot import that the node would normally do.

Consequently, by importing a tarball, you can go from zero to a fully synced node in less time: currently it takes about **9 minutes** to get a fully synced rolling node.

### Archive tarballs

Archive tarballs contain the full backend data directory of an archive node, complete will all history of transactions since genesis. Archive snapshots do not exist, so importing a tarball is the only way of getting an archive node, short of syncing from scratch.

Most Tezos users do not need an archive node. It is mostly useful for indexing the entire chain.

### Internal sanity checks

Before making tarballs available, we test them internally: we import them and make sure that the node starts and RPC becomes available.

### Caveats

Snapshot import performs some safety checks to ensure that the chain state that you are importing is consistent. In contrast, importing a tarball completely bypasses these checks. As a consequence, by importing a tarball, you entrust the tarball provider to give you the correct mainnet chain.

Please evaluate whether this is appropriate for your use case. If not, you may elect to use a snapashot or generate your own tarballs.

## How to use a tarball?

For example to expand one of our tarballs for a **mainnet archive node** -

```bash
curl -LfsS "https://mainnet.xtz-shots.io/archive-tarball" \
| lz4 -d | tar -x -C "/var/tezos"
```

### Tezos node version

We display the Tezos node version used for snapshot generation. For best results, use the same version to import your snapshot. The snapshot format may have changed.

### How regularly are we creating snapshots?

For testnets:

* Rolling snapshots **every 35 minutes**

* Rolling tarballs **every 35 minutes**

* Archive tarballs **every 35 minutes**

For mainnet:

* Rolling snapshots **every 1 hour and 45 minutes**

* Rolling tarballs **every 1 hour and 45 minutes**

* Archive tarballs **every 12 hours**

### Open source

We are generating these artifacts in a Kubernetes environment.

The source code for the snapshot engine will be open-sourced shortly as part of the [tezos-k8s](https://github.com/oxheadalpha/tezos-k8s) Helm chart.

### Brought to you by Oxhead Alpha

We are [Oxhead Alpha](https://www.oxheadalpha.com/), a blockchain infrastructure company.

We maintain a [series of open source infrastructure projects](https://github.com/oxheadalpha) to further the tezos ecosystem of open-source software projects to deploy secure bakers and nodes.

Contact us if you need help with:

* becoming a validator
* deploying your private chain based on Tezos
* generating snapshots for your private chain

### Disclaimers

Users are solely responsible for any risks associated with usage of the Tezos network. Users should do their own research to determine if Tezos is the appropriate platform for their needs and should apply judgement and care in their network interactions.

Unless required by applicable law or agreed to in writing, Oxhead Alpha provides a service on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied, including, without limitation, any warranties or conditions of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A PARTICULAR PURPOSE. You are solely responsible for determining the appropriateness of using our services.
