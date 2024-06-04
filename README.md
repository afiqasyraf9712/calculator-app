# Calculator Application

## Introduction
This repository contains a sample Node.js app that integrates the Prometheus client for Node.js and exposes metrics on [http://localhost:8080/metrics](http://localhost:8080/metrics). The metrics are periodically scraped by Prometheus and visualized through a Grafana monitoring dashboard.

### Prerequisites
Make sure that you have Docker and Docker Compose installed:

- [Docker Engine](https://docs.docker.com/engine/)
- [Docker Compose](https://docs.docker.com/compose/)

## Getting Started
1. **Clone the repository:**
git clone https://github.com/afiqasyraf9712/calculator-app.git


2. **Navigate into the project directory:**
cd node-prometheus-grafana


3. **Start the Docker containers:**
docker-compose up -d


## Testing Containers
- Prometheus should be accessible via [http://localhost:9090](http://localhost:9090).
- Grafana should be accessible via [http://localhost:3000](http://localhost:3000).
- Example Node.js server metrics for monitoring should be accessible via [http://localhost:8080/metrics](http://localhost:8080/metrics).
- Example Node.js slow URL should be accessible via [http://localhost:8080/slow](http://localhost:8080/slow).

## Open Monitoring Dashboards
Open in your web browser the monitoring dashboards:

- [NodeJS Application Dashboard](#)
- [High Level Application Metrics](#)
- [Node Service Level Metrics Dashboard](#)
- [NodeJS Request Flow Dashboard](#)

## Resources
- [Prometheus client for Node.js GitHub Repository](https://github.com/siimon/prom-client)
- [Prometheus - Monitoring System & Time Series Database](https://prometheus.io/)
- [Grafana - Leading Observability Tool for Visualizations & Dashboards](https://grafana.com/)
- [Docker Engine Overview](https://docs.docker.com/engine/)



