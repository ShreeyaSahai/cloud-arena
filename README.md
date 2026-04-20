# ☁️ CloudArena — Cloud Gaming Infrastructure Benchmarking Tool

Simulate real-world cloud gaming infrastructure on AWS — measure latency, auto-scaling response, and cost efficiency across multiple regions.

## What is CloudArena?

CloudArena is an AWS-based benchmarking tool that simulates how cloud gaming platforms manage real player traffic. Instead of building a game, it focuses on the **infrastructure layer** — the part that actually determines whether a game feels smooth or laggy to players.

It answers a question game studios actually ask:

> *"If 1,000 players join my servers simultaneously across different regions, what happens?"*

---

## Core Features

| Feature | Description |
|---|---|
| 🎮 Player Session Simulation | Simulates 100 → 500 → 1000 concurrent players hitting game servers |
| 📊 Real Metrics | Captures p50/p95 latency, error rate, and server load via CloudWatch |
| ⚖️ Auto Scaling | AWS automatically adds EC2 instances when CPU exceeds threshold |
| 🌍 Multi-Region Testing | Compares latency across Mumbai, Virginia, and Ireland |
| 📄 Performance Reports | Generates structured reports a studio could actually use |

---

## Architecture

```
Players (k6 load test)
        │
        ▼
AWS Application Load Balancer
        │
        ▼
Auto Scaling Group (EC2 t2.micro instances)
  ├── cloudarena-server-1 (ap-south-1)
  ├── cloudarena-server-2 (us-east-1)
  └── [scales up to 3 instances automatically]
        │
        ▼
CloudWatch Metrics Dashboard
        │
        ▼
Performance Report (latency + cost + scaling time)
```

---

## Tech Stack

**Cloud Infrastructure**
- AWS EC2 (game servers)
- AWS Auto Scaling (dynamic server management)
- AWS CloudWatch (real-time monitoring)
- AWS Route 53 (multi-region routing)

**Backend**
- Python + FastAPI (game server API)
- boto3 (AWS SDK for metrics collection)

**Load Testing**
- k6 (simulates concurrent players)

**Frontend** *(Week 4)*
- React + Chart.js (live dashboard)

---

## Project Structure

```
cloudarena/
├── server.py                  # FastAPI game server
├── requirements.txt
├── .gitignore
├── README.md
│
├── aws/
│   ├── launch-template.md     # EC2 Launch Template config
│   ├── asg-config.md          # Auto Scaling Group setup
│   └── cloudwatch-setup.md    # CloudWatch dashboard config
│
├── load-tests/
│   ├── basic-load.js          # 100 player simulation
│   └── stress-test.js         # 1000 player stress test
│
├── scripts/
│   ├── fetch-metrics.py       # Pull CloudWatch metrics via boto3
│   └── generate-report.py     # Generate performance PDF report
│
├── results/
│   ├── load-test-1.md         # Real numbers from k6 runs
│   └── region-comparison.md   # Mumbai vs Virginia vs Ireland
│
└── frontend/                  # React dashboard (Week 4)
```

---

## Getting Started

> ⚠️ This project runs on AWS infrastructure.
> You need your own AWS account to deploy it.
> The repo contains the code + full setup instructions.

### Prerequisites
- AWS Account (Free Tier works — estimated cost $0-5)
- Python 3.8+
- k6 installed
- AWS CLI configured with your own credentials

### Setup Your AWS Credentials
```bash
aws configure
# Enter your own AWS Access Key ID
# Enter your own AWS Secret Access Key  
# Default region: ap-south-1
# Output format: json
```

### Then follow the setup guides in order:
1. [`aws/launch-template.md`] — Launch your EC2
2. [`aws/asg-config.md`] — Set up Auto Scaling
3. [`aws/cloudwatch-setup.md`] — Set up monitoring
4. Run load tests from `load-tests/`

---

## 📊 Results *(updated as tests run)*

> Real numbers will be added here after each load test run.

| Metric | Value |
|---|---|
| Concurrent Users Tested | — |
| p95 Latency (Mumbai) | — |
| p95 Latency (Virginia) | — |
| Auto Scaling Trigger Time | — |
| Estimated Monthly Cost | — |

---

## 🗺️ Roadmap

- [x] Week 1 — FastAPI server deployed on EC2
- [x] Week 1 — All 3 endpoints live on AWS
- [ ] Week 2 — Auto Scaling + CloudWatch dashboard
- [ ] Week 2 — k6 load tests (100/500/1000 players)
- [ ] Week 3 — Multi-region deployment
- [ ] Week 3 — Performance report generation
- [ ] Week 4 — React dashboard + demo video

---

## 👥 Team

Built by a team of 2 as a cloud infrastructure portfolio project.

---

## 💡 Motivation

Most cloud portfolio projects deploy something and call it done. CloudArena goes further — it puts infrastructure under real stress and measures exactly how it holds up: latency under load, scaling response time, and cost per region. The goal is to produce numbers a real engineering team would find useful, not just a working demo.

---
