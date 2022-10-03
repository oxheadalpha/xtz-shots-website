---
# Page settings
layout: snapshot
permalink: {{ page.permalink }}
keywords:
comments: false
# Hero section
title: Tezos snapshots for AWSPRPRPPRRP
description:
# Author box
author:
  title: Brought to you by Oxhead Alpha
  title_url: "https://medium.com/the-aleph"
  external_url: true
  description: A Tezos core development company, providing common goods for the Tezos ecosystem. <a href="https://medium.com/the-aleph" target="_blank">Learn more</a>.
# Micro navigation
micro_nav: true
# Page navigation
page_nav:
  home:
    content: Previous page
    url: https://xtz-shots.io/index.html
---

{% assign network_substring = page.latest_snapshots.rolling.chain_name | remove: "net" %}
{% capture domain_name %}https://{{ page.latest_snapshots.rolling.chain_name }}.{{ site.domain_name }}{% endcapture %}

{% if network_substring == "main" %}
  {% assign tzstats_subdomain = "" %}
  {% assign tzkt_subdomain = "" %}
{% else %}
  {% assign tzstats_subdomain = network_substring | append: "." %}
  {% assign tzkt_subdomain = page.latest_snapshots.rolling.chain_name | append: "." %}
{% endif %}

{% assign min = 100 %}
{% assign max = 999 %}
{% assign diff = max | minus: min %}
{% assign randomNumber = "now" | date: "%N" | modulo: diff | plus: min %}

# Tezos snapshots for {{ page.latest_snapshots.rolling.chain_name }}

Octez version used for snapshotting: `{{ page.latest_snapshots.rolling.tezos_version }}`

## Rolling snapshot

[Download Rolling Snapshot]({{ page.latest_snapshots.rolling.url }})

Block height: `{{ page.latest_snapshots.rolling.block_height }}`

Block hash: `{{ page.latest_snapshots.rolling.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ page.latest_snapshots.rolling.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ page.latest_snapshots.rolling.block_hash }}){:target="\_blank"}

Block timestamp: `{{ page.latest_snapshots.rolling.block_timestamp }}`

File Size: `{{ page.latest_snapshots.rolling.filesize }}`

Checksum (SHA256):

```
{{ page.latest_snapshots.rolling.sha256 }}
```

[Artifact Metadata]({{ page.latest_snapshots.rolling.url }}.json)

## Archive tarball

[What is a tarball?](https://xtz-shots.io/getting-started/#what-is-a-tarball-) - [Limitation of tarballs](https://xtz-shots.io/getting-started/#caveats)

{% if page.latest_snapshots.archive-tarball.url %}
[Download Archive Tarball]({{ page.latest_snapshots.archive-tarball.url }})

Block height: `{{ page.latest_snapshots.archive-tarball.block_height }}`

Block hash: `{{ page.latest_snapshots.archive-tarball.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ page.latest_snapshots.archive-tarball.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ page.latest_snapshots.archive-tarball.block_hash }}){:target="\_blank"}

Block timestamp: `{{ page.latest_snapshots.archive-tarball.block_timestamp }}`

File Size: `{{ page.latest_snapshots.archive-tarball.filesize }}`

Checksum (SHA256):

```
{{ page.latest_snapshots.archive-tarball.sha256 }}
```

[Artifact Metadata]({{ page.latest_snapshots.archive-tarball.url }}.json)
{% else %}
Uh oh! No archive tarball for Tezos build `{{ page.latest_snapshots.rolling.tezos_version }}` yet. Looks like we still need some more time. Check out https://xtz-shots.io/`{{ page.latest_snapshots.rolling.chain_name }}`/list.html for older artifacts.
{% endif %}

## Rolling tarball

[What is a tarball?](https://xtz-shots.io/getting-started/#what-is-a-tarball-) - [Limitation of tarballs](https://xtz-shots.io/getting-started/#caveats)

[Download Rolling Tarball]({{ page.latest_snapshots.rolling-tarball.url }})

Block height: `{{ page.latest_snapshots.rolling-tarball.block_height }}`

Block hash: `{{ page.latest_snapshots.rolling-tarball.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ page.latest_snapshots.rolling-tarball.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ page.latest_snapshots.rolling-tarball.block_hash }}){:target="\_blank"}

Block timestamp: `{{ page.latest_snapshots.rolling-tarball.block_timestamp }}`

File Size: `{{ page.latest_snapshots.rolling-tarball.filesize }}`

Checksum (SHA256):

```
{{ page.latest_snapshots.rolling-tarball.sha256 }}
```

[Artifact Metadata]({{ page.latest_snapshots.rolling-tarball.url }}.json)

## How to use

### Rolling Snapshot

Issue the following commands:

```bash
wget {{ domain_name }}/{{ page.latest_snapshots.rolling.filename }}
tezos-node snapshot import {{ page.latest_snapshots.rolling.filename }} --block {{ page.latest_snapshots.rolling.block_hash }}
```

Or simply use the permalink:

```bash
wget {{ domain_name }}/rolling -O tezos-{{ page.latest_snapshots.rolling.chain_name }}.rolling
tezos-node snapshot import tezos-{{ page.latest_snapshots.rolling.chain_name }}.rolling --block {{ page.latest_snapshots.rolling.block_hash }}
```

### Archive Tarball

Issue the following commands:

```bash
curl -L "{{ domain_name }}/{{ page.latest_snapshots.archive-tarball.filename }}" \
| lz4 -d | tar -x -C "/var/tezos"
```

Or simply use the permalink:

```bash
curl -L "{{ domain_name }}/archive-tarball" \
| lz4 -d | tar -x -C "/var/tezos"
```

### Rolling Tarball

Issue the following commands:

```bash
curl -L "{{ domain_name }}/{{ page.latest_snapshots.rolling-tarball.filename }}" \
| lz4 -d | tar -x -C "/var/tezos"
```

Or simply use the permalink:

```bash
curl -L "{{ domain_name }}/rolling-tarball" \
| lz4 -d | tar -x -C "/var/tezos"
```

### More details

[About xtz-shots.io]({{ site.url }}/getting-started/).

[Tezos documentation](https://tezos.gitlab.io/user/snapshots.html){:target="\_blank"}.
