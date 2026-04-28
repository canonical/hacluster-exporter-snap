[![Get it from the Snap Store](https://snapcraft.io/en/dark/install.svg)](https://snapcraft.io/hacluster-exporter)

# HA Cluster Exporter Snap

A snap package for [ha_cluster_exporter](https://github.com/ClusterLabs/ha_cluster_exporter) — a Prometheus exporter for Pacemaker-based Linux HA clusters.

## Install

```bash
sudo snap install hacluster-exporter
```

The snap starts the exporter service automatically and exposes metrics on `:9664/metrics` by default.

## Use

Configure Prometheus to scrape `http://<cluster-node>:9664/metrics`.

For the most complete view of the cluster, run the snap on each cluster node. On each scrape, the exporter inspects the local node and exposes Pacemaker, Corosync, SBD, and DRBD metrics when those components are available.

Grafana dashboards can then be used to visualize the exported metrics.

## Configure

This snap currently starts `ha_cluster_exporter` with upstream defaults and does not expose snap configuration options.

Defaults:

- `web.listen-address`: `:9664`
- `web.telemetry-path`: `/metrics`

## Reference

The exporter is intended to run on cluster nodes where it can inspect the local HA stack. If a component is not available locally, metrics for that component are not exported.

Upstream documentation:

- [Metrics reference](https://github.com/ClusterLabs/ha_cluster_exporter/blob/main/doc/metrics.md)
- [Grafana dashboards](https://github.com/ClusterLabs/ha_cluster_exporter/tree/main/dashboards)
