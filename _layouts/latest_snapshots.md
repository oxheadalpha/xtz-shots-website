---
# Page settings
layout: snapshot_list
permalink: {{ page.permalink }}
keywords:
comments: false
# Hero section
title: Tezos snapshots for AWSPRPRPPRRP
description:
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

# Most recent snapshots for {{ page.latest_snapshots.rolling.chain_name }}

{% assign version = page.latest_snapshots.rolling.tezos_version.version %}
{% assign major_version = version.major %}
{% assign minor_version = version.minor %}
{% assign additional_info = page.latest_snapshots.rolling.tezos_version.version.additional_info %}

{% if additional_info == "release" %}
  {% capture version %}v{{ major_version }}.{{ minor_version }}{% endcapture %}
{% else %}
  {% assign rc = additional_info.rc %}
  {% capture version %}v{{ major_version }}.{{ minor_version }} rc~{{ rc }}{% endcapture %}
{% endif %}

Octez version used for snapshotting: `{{ version }}`

[Browse older snapshots](/{{page.latest_snapshots.rolling.chain_name}}/list.html).

## Rolling snapshot

{% if page.latest_snapshots.rolling.url %}
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

[Artifact Metadata]({{ domain_name }}/{{ page.latest_snapshots.rolling.filename }}.json)
{% else %}
Uh oh! No rolling snapshot yet. Looks like we still need some more time. Check back soon!
{% endif %}

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

[Artifact Metadata]({{ domain_name }}/{{ page.latest_snapshots.archive-tarball.filename }}.json)
{% else %}
Uh oh! No archive tarball yet. Looks like we still need some more time. Check back soon!
{% endif %}

## Rolling tarball

[What is a tarball?](https://xtz-shots.io/getting-started/#what-is-a-tarball-) - [Limitation of tarballs](https://xtz-shots.io/getting-started/#caveats)

{% if page.latest_snapshots.rolling-tarball.url %}
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

[Artifact Metadata]({{ domain_name }}/{{ page.latest_snapshots.rolling-tarball.filename }}.json)
{% else %}
Uh oh! No rolling tarball yet. Looks like we still need some more time. Check back soon!
{% endif %}

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

:warning: TAR path is `node/data/` which corresponds to `/var/tezos/node/data`. Make sure to account for this on your local setup when untarring.

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

:warning: TAR path is `node/data/` which corresponds to `/var/tezos/node/data`. Make sure to account for this on your local setup when untarring.

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
