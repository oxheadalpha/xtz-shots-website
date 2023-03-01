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

# All Tezos Snapshots for {{ page.snapshots.rolling[0].chain_name }}

The full list of snapshots is also available as a metadata file:
* [Download metadata file](https://xtz-shots.io/tezos-snapshots.json)
* [Read more about metadata](/getting-started/#xtz-shots-metadata)

## Rolling Snapshots
{% assign sorted = page.snapshots.rolling | sort: 'block_timestamp' | reverse %}

| Filename | Date | Size | Octez version | |
| -- | -- | -- | -- |
{% for s in sorted %}
{%- assign version = s.tezos_version.version -%}
{%- assign major_version = version.major -%}
{%- assign minor_version = version.minor -%}
{%- assign additional_info = s.tezos_version.version.additional_info -%}
{%- if additional_info.rc -%}
  {%- assign rc = additional_info.rc -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }} rc~{{ rc }}{%- endcapture -%}
{%- else -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }}{%- endcapture -%}
{%- endif -%}
| `{{ s.filename }}` | `{{ s.block_timestamp }}`| {{ s.filesize }} | `{{ version }}` | [⬇️]({{ s.url}}) |
{% endfor %}

## Rolling Tarballs
{% assign sorted = page.snapshots.rolling-tarball | sort: 'block_timestamp' | reverse %}

| Filename | Date | Size | Octez version | |
| -- | -- | -- | -- |
{% for s in sorted -%}
{%- assign version = s.tezos_version.version -%}
{%- assign major_version = version.major -%}
{%- assign minor_version = version.minor -%}
{%- assign additional_info = s.tezos_version.version.additional_info -%}
{%- if additional_info.rc -%}
  {%- assign rc = additional_info.rc -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }} rc~{{ rc }}{%- endcapture -%}
{%- else -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }}{%- endcapture -%}
{%- endif -%}
| `{{ s.filename }}` | `{{ s.block_timestamp }}`| {{ s.filesize }} | `{{ version }}` | [⬇️]({{ s.url}}) |
{% endfor %}

## Archive Tarballs
{% assign sorted = page.snapshots.archive-tarball | sort: 'block_timestamp' | reverse %}

| Filename | Date | Size | Octez version | |
| -- | -- | -- | -- |
{% for s in page.snapshots.archive-tarball -%}
{%- assign version = s.tezos_version.version -%}
{%- assign major_version = version.major -%}
{%- assign minor_version = version.minor -%}
{%- assign additional_info = s.tezos_version.version.additional_info -%}
{%- if additional_info.rc -%}
  {%- assign rc = additional_info.rc -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }} rc~{{ rc }}{%- endcapture -%}
{%- else -%}
  {%- capture version %}v{{ major_version }}.{{ minor_version }}{%- endcapture -%}
{%- endif -%}
| `{{ s.filename }}` | `{{ s.block_timestamp }}`| {{ s.filesize }} | `{{ version }}` | [⬇️]({{ s.url}}) |
{% endfor %}

[About xtz-shots.io]({{ site.url }}/getting-started/).

[Tezos documentation](https://tezos.gitlab.io/user/snapshots.html){:target="\_blank"}.
