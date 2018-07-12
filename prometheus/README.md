# Monitor

The monitor service is the entrance for job and cluster management.
User and cluster operator can monitor the cluseter, service, job through the web UI.

## Deployment 

The [readme](../service-deployment/README.md) in service deployment introduces the overall installation process, including that of the monitor. 
The following parameters in the [clusterconfig.yaml](../service-deployment/clusterconfig-example.yaml) are of interest to monitor:

* grafana config:

grafana:

  # port for grafana

  grafana-port: 3000

* prometheus config:

prometheus:

  # port for prometheus port

  prometheus-port: 9091

  # port for node exporter

  node-exporter-port: 9100

## Usage

### Cluster View


### Job View


### Service View


## Component

- [prometheus](https://prometheus.io/): store the metrics, support query and aggregate metrics.
- [grafana](https://grafana.com/): Query prometheus and render metrics.
- [node-exporter](https://github.com/prometheus/node_exporter): Each server will launch a node-exporter to fetch node hardware metrics.
- gpu-exporter: Each server will launch a gpu-exporter to fetch node gpu, job container metrics.
- watchdog: Check and log whole cluster service health. 