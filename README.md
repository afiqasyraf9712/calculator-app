Node.js Application Monitoring with Prometheus and Grafana
The repository contains a sample Node.js app that integrates the Prometheus client for node.js and exposes metrics on [http://localhost:8080/metrics](http://localhost:8080/metrics). The metrics are periodically scraped by Prometheus and visualized through a Grafana monitoring dashboard.

Prerequisites
Make sure that you have Docker and Docker Compose installed:
Docker Engine
Docker Compose

Getting started
Clone the repository:
git clone https://github.com/arpendu11/node-prometheus-grafana.git


Navigate into the project directory:
cd node-prometheus-grafana


 Start the Docker containers:
docker-compose up -d


Test containers
Prometheus should be accessible via [http://localhost:9090](http://localhost:9090)
Grafana should be accessible via [http://localhost:3000](http://localhost:3000)
Example Node.js server metrics for monitoring should be accessible via [http://localhost:8080/metrics](http://localhost:8080/metrics)
Example Node.js slow URL should be accessible via [http://localhost:8080/slow](http://localhost:8080/slow)

Open monitoring dashboards
Open in your web browser the monitoring dashboards:

NodeJS Application Dashboard
High Level Application metrics
Node Service Level Metrics Dashboard
NodeJS Request Flow Dashboard
GitHub
GitHub - siimon/prom-client: Prometheus client for node.js
Prometheus client for node.js. Contribute to siimon/prom-client development by creating an account on GitHub.
GitHub - siimon/prom-client: Prometheus client for node.js
Prometheus - Monitoring system & time series database
An open-source monitoring system with a dimensional data model, flexible query language, efficient time series database and modern alerting approach.
Image
Grafana Labs
Grafana OSS | Leading observability tool for visualizations & dashb...
Improve operational efficiency, monitor your infrastructure, and analyze metrics, logs, and traces with Grafana, the leading open source tool for dashboards and visualizations.
Grafana OSS | Leading observability tool for visualizations & dashb...
Docker Documentation
Docker Engine overview
Find a comprehensive overview of Docker Engine, including how to install, storage details, networking, and more
Docker Engine overview