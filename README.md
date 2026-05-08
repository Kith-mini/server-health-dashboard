# 🖥️ Automated Server Health Dashboard

A production-grade, self-hosted server monitoring stack built with **Prometheus**, **Grafana**, **Node Exporter**, and **Alertmanager** — containerised with **Docker Compose** and deployable with a single command.

> Built as part of a 5-phase DevOps project: Plan → Build → Test → Document → Resume

---

## 📸 Dashboard Preview

**Node Exporter Full (ID: 1860)** — Live CPU, RAM, Disk, and Network metrics

![Dashboard](docs/screenshots/dashboard.png)

---

## 🧰 Tech Stack

| Tool | Role | Port |
|------|------|------|
| **Prometheus** | Metrics collection & storage | `:9090` |
| **Node Exporter** | Linux system metrics agent | `:9100` |
| **Grafana** | Dashboard visualisation | `:3000` |
| **Alertmanager** | Alert routing (Telegram/Email) | `:9093` |
| **Docker Compose** | Container orchestration | — |

---

## ⚡ Quick Start

### Prerequisites
- Ubuntu Linux (20.04+)
- Docker 24+
- Docker Compose v2+
- Git

### 1. Clone the repository
\`\`\`bash
git clone https://github.com/Kith-mini/server-health-dashboard.git
cd server-health-dashboard
\`\`\`

### 2. Configure secrets
\`\`\`bash
cp .env.example .env
nano .env
\`\`\`

### 3. Start the stack
\`\`\`bash
docker compose up -d
\`\`\`

### 4. Verify all containers are running
\`\`\`bash
docker compose ps
\`\`\`

---

## 🌐 Access the Services

| Service | URL | Credentials |
|---------|-----|-------------|
| **Grafana** | http://localhost:3000 | admin / your password |
| **Prometheus** | http://localhost:9090 | No login required |
| **Alertmanager** | http://localhost:9093 | No login required |
| **Node Exporter** | http://localhost:9100/metrics | No login required |

---

## 📊 Import the Grafana Dashboard

1. Open **http://localhost:3000** and log in
2. Click **Dashboards → New → Import**
3. Enter dashboard ID: **1860**
4. Click **Load**
5. Select **Prometheus** as the datasource
6. Click **Import**

---

## 🚨 Alert Rules

| Alert | Condition | Duration | Severity |
|-------|-----------|----------|----------|
| HighCPUUsage | CPU > 80% | 2 minutes | warning |
| HighMemoryUsage | RAM > 85% | 2 minutes | warning |
| DiskSpaceLow | Disk > 85% | 5 minutes | critical |
| InstanceDown | Target unreachable | 1 minute | critical |

---

## 📁 Project Structure

\`\`\`
server-health-dashboard/
├── docker-compose.yml
├── .env
├── prometheus/
│   ├── prometheus.yml
│   └── alert.rules.yml
├── grafana/
│   └── provisioning/
│       ├── datasources/prometheus.yml
│       └── dashboards/dashboard.yml
├── alertmanager/
│   └── alertmanager.yml
├── scripts/
│   ├── check_health.py
│   └── simulate_stress.py
└── docs/screenshots/
\`\`\`

---

## 🔧 Useful Commands

\`\`\`bash
docker compose up -d          # Start the stack
docker compose down           # Stop the stack
docker compose ps             # Check status
docker compose logs -f        # View live logs
docker compose restart alertmanager  # Restart one service
\`\`\`

---

## 🛠️ Troubleshooting

| Problem | Fix |
|---------|-----|
| Grafana shows "No data" | Check Prometheus is running at :9090 |
| Alertmanager restarting | Run docker logs alertmanager |
| Targets show DOWN | Run docker compose ps and restart |
| DiskSpaceLow alert firing | Run docker system prune -a |

---

## 👤 Author

**Kith-mini** — [github.com/Kith-mini](https://github.com/Kith-mini)

---

## 📄 License

MIT License
