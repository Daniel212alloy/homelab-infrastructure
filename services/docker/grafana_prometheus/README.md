## 📊 Monitoring Server (Work in Progress)

A monitoring stack is currently being developed as part of this homelab infrastructure project.

The goal is to implement centralized infrastructure monitoring using:

* **Prometheus** - Metrics collection and monitoring system
* **Grafana** - Visualization dashboard for server and service metrics
* **Node Exporter** - Host-level system metrics exporter

### Current Status

🚧 Initial setup phase

* [x] Prometheus container deployed
* [x] Grafana container deployed
* [x] Basic Docker environment prepared
* [ ] Configure Prometheus scrape targets
* [ ] Add Node Exporter monitoring
* [ ] Create Grafana dashboards
* [ ] Configure alerts and notifications

### Planned Architecture

```
              Servers / Services
                     |
              Node Exporter
                     |
                     |
                Prometheus
                     |
                     |
                 Grafana
                     |
              Monitoring Dashboard
```

This monitoring on progress will be integrated with the existing Docker and homelab environment to provide visibility into system performance, resource usage, and service availability.




