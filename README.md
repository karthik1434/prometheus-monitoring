# Prometheus + Grafana Monitoring Setup (Beginner Friendly)

This project sets up Prometheus and Grafana using Docker Compose on Windows 10 to monitor system metrics using Node Exporter.

---

## 🚀 Components

- **Prometheus** – Time-series data collection and querying.
- **Node Exporter** – Exposes hardware and OS metrics from your machine.
- **Grafana** – Visualization tool connected to Prometheus.

---

## 📁 Folder Structure

prometheus-monitoring/
├── docker-compose.yml
├── prometheus/
│ └── prometheus.yml
└── grafana/ (optional)

yaml
Copy
Edit

---

## ⚙️ Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop) (Windows)
- [VS Code](https://code.visualstudio.com/)
- Enable WSL2 and Linux containers in Docker Desktop

---

## 🐳 Docker Compose Setup

### Step 1: Clone or create this folder structure

```bash
git clone <this-repo> # Or create the structure manually
cd prometheus-monitoring
Step 2: Run Docker Compose
bash
Copy
Edit
docker-compose up -d
This pulls official Docker images and starts:

Prometheus on localhost:9090

Grafana on localhost:3000

📊 Grafana Setup
Access Grafana: http://localhost:3000
Login: admin / admin (change after first login)

Add Prometheus Data Source:

URL: http://prometheus:9090

Save & Test

Build a Dashboard:

Go to Explore

Example Queries:

up

rate(node_cpu_seconds_total[5m])

node_memory_MemAvailable_bytes

⚙️ prometheus.yml
yaml
Copy
Edit
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['host.docker.internal:9100']
📌 host.docker.internal allows Prometheus to reach your Windows host from inside the container.

🛑 Stop the stack
bash
Copy
Edit
docker-compose down
📚 Useful Links
Prometheus Docs

Grafana Docs

Node Exporter

👨‍💻 Author
Karthik – DevOps Enthusiast