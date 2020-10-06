---
# Page settings
layout: snapshot
keywords:
comments: false

# Hero section
title: Mainnet snapshots
description: 

# Author box
author:
    title: MIDL.dev
    title_url: 'https://midl.dev/'
    external_url: true
    description: MIDL.dev is a staking-as-a-service company

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    home:
        content: Previous page
        url: 'https://xtz-shots.io/index.html'
---

## Tezos snapshot for ${TEZOS_NETWORK}

Block height: $BLOCK_HEIGHT

Block hash: \`${BLOCK_HASH}\` - [Verify on TzStats](https://tzstats.com/${BLOCK_HASH}) - [Verify on TzKT](https://tzkt.io/${BLOCK_HASH})

Block timestamp: $BLOCK_TIMESTAMP

## Rolling snapshot

[Rolling Snapshot](${snapshot_name}.rolling)

## Full snapshot

[Full Snapshot](${snapshot_name}.full)

HOW TO USE

```
wget https://delphinet.xtz-shots.io/tezos-delphinet-83316.rolling
tezos-node snapshot import tezos-delphinet-83316.rolling --block BMDKHftB5biRp9ZdkcMaoGby5UhT38eR8ntB1SWQ54fDNqKgr1n
```