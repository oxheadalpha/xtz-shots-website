---
# Page settings
layout: snapshot
keywords:
comments: false
# Hero section
title: Tezos snapshots for ${NETWORK}
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

{% assign network_substring = site.data.tezos_metadata.network | remove: "net" %}
{% capture domain_name %}https://{{ site.data.tezos_metadata.network }}.{{ site.domain_name }}{% endcapture %}

{% if network_substring == "main" %}
  {% assign tzstats_subdomain = "" %}
  {% assign tzkt_subdomain = "" %}
{% elsif network_substring == "hangzhou" %}
  {% assign tzstats_subdomain = network_substring | append: "." %}
  {% assign tzkt_subdomain = "hangzhou2net" | append: "." %}
{% else %}
  {% assign tzstats_subdomain = network_substring | append: "." %}
  {% assign tzkt_subdomain = site.data.tezos_metadata.network | append: "." %}
{% endif %}

{% assign min = 100 %}
{% assign max = 999 %}
{% assign diff = max | minus: min %}
{% assign randomNumber = "now" | date: "%N" | modulo: diff | plus: min %}

# Tezos snapshots for {{ site.data.tezos_metadata.network }}

Octez version used for snapshotting: `{{ site.data.rolling_snapshot.tezos_version }}`

## Rolling snapshot

[Download Rolling Snapshot]({{ domain_name }}/{{ site.data.rolling_snapshot.filename }})

Block height: `{{ site.data.rolling_snapshot.block_height }}`

Block hash: `{{ site.data.rolling_snapshot.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ site.data.rolling_snapshot.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ site.data.rolling_snapshot.block_hash }}){:target="\_blank"}

Block timestamp: `{{ site.data.rolling_snapshot.block_timestamp }}`

Size in bytes: `{{ site.data.rolling_snapshot.filesize_bytes }}`

Checksum (SHA256):

```
{{ site.data.rolling_snapshot.sha256 }}
```

[Artifact Metadata]({{ domain_name }}/rolling-snapshot-metadata?{{ randomNumber }})

## Archive tarball

[What is a tarball?](https://xtz-shots.io/getting-started/#what-is-a-tarball-) - [Limitation of tarballs](https://xtz-shots.io/getting-started/#caveats)

[Download Archive Tarball]({{ domain_name }}/{{ site.data.archive_tarball.filename }})

Block height: `{{ site.data.archive_tarball.block_height }}`

Block hash: `{{ site.data.archive_tarball.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ site.data.archive_tarball.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ site.data.archive_tarball.block_hash }}){:target="\_blank"}

Block timestamp: `{{ site.data.archive_tarball.block_timestamp }}`

Size in bytes: `{{ site.data.archive_tarball.filesize_bytes }}`

Checksum (SHA256):

```
{{ site.data.archive_tarball.sha256 }}
```

[Artifact Metadata]({{ domain_name }}/archive-tarball-metadata?{{ randomNumber }})

## Rolling tarball

[What is a tarball?](https://xtz-shots.io/getting-started/#what-is-a-tarball-) - [Limitation of tarballs](https://xtz-shots.io/getting-started/#caveats)

[Download Rolling Tarball]({{ domain_name }}/{{ site.data.rolling_tarball.filename }})

Block height: `{{ site.data.rolling_tarball.block_height }}`

Block hash: `{{ site.data.rolling_tarball.block_hash }}`

[Verify on TzStats](https://{{ tzstats_subdomain }}tzstats.com/{{ site.data.rolling_tarball.block_hash }}){:target="\_blank"} - [Verify on TzKT](https://{{ tzkt_subdomain }}tzkt.io/{{ site.data.rolling_tarball.block_hash }}){:target="\_blank"}

Block timestamp: `{{ site.data.rolling_tarball.block_timestamp }}`

Size in bytes: `{{ site.data.rolling_tarball.filesize_bytes }}`

Checksum (SHA256):

```
{{ site.data.rolling_tarball.sha256 }}
```

[Artifact Metadata]({{ domain_name }}/rolling-tarball-metadata?{{ randomNumber }})

## How to use

### Rolling Snapshot

Issue the following commands:

```bash
wget {{ domain_name }}/{{ site.data.rolling_snapshot.filename }}
tezos-node snapshot import {{ site.data.rolling_snapshot.filename }} --block {{ site.data.rolling_snapshot.block_hash }}
```

Or simply use the permalink:

```bash
wget {{ domain_name }}/rolling -O tezos-{{ site.data.tezos_metadata.network }}.rolling
tezos-node snapshot import tezos-{{ site.data.tezos_metadata.network }}.rolling --block {{ site.data.rolling_snapshot.block_hash }}
```

### Archive Tarball

Issue the following commands:

```bash
curl -L "{{ domain_name }}/{{ site.data.archive_tarball.filename }}" \
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
curl -L "{{ domain_name }}/{{ site.data.rolling_tarball.filename }}" \
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
