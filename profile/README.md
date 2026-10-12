# Internet Topology Research

Reconstructing and studying the Internet's **AS-level topology** from public BGP routing data.

Every route on the Internet carries an AS path: the sequence of Autonomous Systems it crosses. We collect routing table snapshots from public route collectors, extract those paths and turn them into a graph of AS adjacencies. That graph can then be analyzed, compared over time and shared as open datasets.

## Repositories

| Repository | What it contains |
|---|---|
| [**internet-topology-ris**](https://github.com/carlos-cagnazzo/internet-topology-ris) | Tooling. A Python pipeline that downloads MRT RIB snapshots from RIPE RIS and RouteViews, extracts and cleans AS paths, and builds deduplicated edge lists, ASN lists and path lists. It also has helpers for set operations between topologies, country/RIR annotation, GML export and AS lookups. [Documentation](https://carlos-cagnazzo.github.io/internet-topology-ris) |
| [**internet-topology-datasets**](https://github.com/carlos-cagnazzo/internet-topology-datasets) | Datasets. Published topology snapshots built with the pipeline: AS adjacencies (text and GML), ASN lists, raw IPv4/IPv6 AS paths, CAIDA peerings and an approximation of the Tier-1 set. |

## How it fits together

```
RIPE RIS (rrc00–rrc25) ─┐
                        ├─> MRT RIB snapshots ─> AS paths ─> AS-level topology ─> datasets
RouteViews collectors ──┘     (get-mrt)        (extract)       (build)            & analysis
```

Path cleaning collapses AS prepending and truncates paths at AS sets. Optionally, paths that contain ASNs not formally assigned in the NRO delegated stats can be filtered out. IPv4 and IPv6 topologies are produced both separately and combined.

## Datasets at a glance

| Snapshot | Contents |
|---|---|
| [2025-04](https://github.com/carlos-cagnazzo/internet-topology-datasets/tree/main/202504) | AS adjacencies, unique ASNs, raw IPv4/IPv6 AS paths |
| [2026-07](https://github.com/carlos-cagnazzo/internet-topology-datasets/tree/main/202607) | AS adjacencies (text and GML), ASN list, CAIDA peerings, Tier-1 approximation |

ASNs are zero-padded 8-digit decimals (`00007046`), and adjacency files list one undirected `ASN ASN` pair per line.

## Talks and publications

- **A Short Survey and Brief Tutorial on the State of the Art in Internet Routing Security**. Carlos Martínez Cagnazzo, Cristina Mayr and Claudio Risso. 2025 IEEE CHILEAN Conference on Electrical, Electronics Engineering, Information and Communication Technologies (CHILECON), pp. 1–8. [IEEE Xplore](https://ieeexplore.ieee.org/abstract/document/11476436), [camera-ready PDF](https://github.com/carlos-cagnazzo/.github/blob/main/papers/chilecon-2025-routing-security-survey.pdf).
- **El grafo de los ASNs de Internet** (*The Internet ASN graph*). Claudio Risso and Carlos Martínez, LACNIC 45 Technical Forum, May 2026. [Slides](https://github.com/carlos-cagnazzo/internet-topology-datasets/blob/main/talks/el-grafo-de-los-asns-de-internet-lacnic45.pdf), video in [Spanish](https://youtu.be/02ROROD3dVM), [English](https://youtu.be/EBa1wEFbnKs) and [Portuguese](https://youtu.be/YXNHc5nR2CY).

## Data sources

This work builds on public data from [RIPE NCC RIS](https://www.ripe.net/analyse/internet-measurements/routing-information-service-ris/), [RouteViews](https://www.routeviews.org/), the [NRO delegated extended stats](https://ftp.ripe.net/pub/stats/ripencc/nro-stats/latest/nro-delegated-stats), [CAIDA](https://www.caida.org/) and the [RIPEstat Data API](https://stat.ripe.net/docs/data_api).
