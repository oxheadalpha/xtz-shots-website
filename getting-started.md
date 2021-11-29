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
    description: A proof-of-stake infrastructure company - we help you bake your XTZ. <a href="https://medium.com/the-aleph" target="_blank">Learn more</a>.

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    home:
        content: Previous page
        url: 'https://xtz-shots.io/index.html'
---

### What is this ?

[Tezos](https://tezos.com) is a proof-of-stake blockchain.

This website helps people operating Tezos nodes to synchronize to the head of the chain, so they are operational faster.

New snapshots are uploaded twice a day.

This project was sponsored by a grant from the [Tezos foundation](https://tezos.foundation/).

### How to use

We are the first snapshot website to provide **permalinks**: URLs that never change and reliably point to a recent snapshot.

For example, to download a recent full snapshot of Tezos mainnet, simply do:

```
wget https://mainnet.xtz-shots.io/full
```

More details can be found in the [snapshot page](https://mainnet.xtz-shots.io).

#### Tezos node version

We display the Tezos node version used for snapshot generation. For best results, use the same version to import your snapshot. The snapshot format may have changed.

### How does it work ?

The snapshot generation engine is deployed on [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine).

All source code is [open source](https://github.com/midl-dev/tezos-snapshot-generator) so anyone can deploy a separate snapshot generator setup in the cloud.


### Brought to you by Oxhead Alpha

We are [Oxhead Alpha](https://www.oxheadalpha.com/), a blockchain infrastructure company.

We maintain the [Tezos Suite](https://medium.com/the-aleph) of open-source software projects to deploy secure bakers and nodes.

Contact us if you need help with:

* becoming a validator
* deploying your private chain based on Tezos
* generating snapshots for your private chain

### Disclaimers

Users are solely responsible for any risks associated with usage of the Tezos network. Users should do their own research to determine if Tezos is the appropriate platform for their needs and should apply judgement and care in their network interactions.

Unless required by applicable law or agreed to in writing, Oxhead Alpha provides a service on an “AS IS” BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied, including, without limitation, any warranties or conditions of TITLE, NON-INFRINGEMENT, MERCHANTABILITY, or FITNESS FOR A PARTICULAR PURPOSE. You are solely responsible for determining the appropriateness of using our services.
