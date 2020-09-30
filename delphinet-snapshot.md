---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Delphinet snapshots
description: Delphinet is a test network running the Delphi protocol.

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
        url: '/index'
#    next:
#        content: Next page
#        url: '#'
---

# Attributes
 * Publish date
 * Snapshot_Type
 * Snapshot_ID
 * BlockHash
 * BlockNum
 * Blocktime
 * Download links

On Delphinet, the following constants differ from Mainnet:
* preserved_cycles is 3 instead of 5;
* blocks_per_cycle is 2048 instead of 4096;
* blocks_per_voting_period is 2048 instead of 32768;
* time_between_blocks is [ 30, 20 ] instead of [ 60, 40 ];
* test_chain_duration is 61440 instead of 1966080;
* delay_per_missing_endorsement is 4 instead of 8.

This results in a faster chain than Mainnet:
* 2 blocks per minute;
* a cycle should last about 17 hours;
* a voting period lasts 1 cycle and should thus also last about 17 hours.