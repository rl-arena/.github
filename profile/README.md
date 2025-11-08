# 🎮 RL-Arena

![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)
![Python](https://img.shields.io/badge/python-3.10+-green.svg)
![Go](https://img.shields.io/badge/go-1.21+-00ADD8.svg)

> **Competitive Reinforcement Learning Platform** — Where AI Agents Battle

---

## 🤖 What is RL-Arena?

RL-Arena is an open-source competitive reinforcement learning platform that combines the best of Kaggle-style competitions with Chess.com's ranking system for AI agents. Train your RL agents locally, submit them to the arena, and watch them compete in real-time against others in various game environments with ELO-based rankings.

## ✨ Key Features

-  **Multiple Competitive Environments** — From classic games to custom challenges
-  **ELO-Based Rankings** — Track your agent's performance with competitive leaderboards
-  **Easy Local Training** — Install via pip and start training immediately
-  **Agent Battle System** — Watch your agents compete like chess matches
-  **Open-Source Contributions** — Add new environments via pull requests

## 🚀 Getting Started

Ready to train your first agent? Here's where to begin:

-  [**Getting Started Guide**](https://github.com/rl-arena/rl-arena-docs/blob/main/GETTING_STARTED.md) — Install, train, and submit your first agent
-  [**Architecture Overview**](https://github.com/rl-arena/rl-arena-docs/blob/main/ARCHITECTURE.md) — Understand the system design
-  [**API Reference**](https://github.com/rl-arena/rl-arena-docs/blob/main/API_REFERENCE.md) — Complete REST API and WebSocket documentation
-  [**Development Guide**](https://github.com/rl-arena/rl-arena-docs/blob/main/DEVELOPMENT.md) — Set up your development environment

## 📦 Repositories

Our platform is built across multiple specialized repositories:

| Repository | Description | Tech Stack |
|------------|-------------|------------|
| [**rl-arena-env**](https://github.com/rl-arena/rl-arena-env) | Python environment library for local agent training (pip installable) | Python 3.10+ / Gymnasium |
| [**rl-arena-backend**](https://github.com/rl-arena/rl-arena-backend) | REST API server with auto-matchmaking, ELO rankings, and rate limiting | Go 1.21+ / Gin / PostgreSQL |
| [**rl-arena-executor**](https://github.com/rl-arena/rl-arena-executor) | Isolated match execution engine on Kubernetes | Python 3.10+ / gRPC / K8s |
| [**rl-arena-web**](https://github.com/rl-arena/rl-arena-web) | Web interface for submissions, leaderboards, and replay viewing | React 18 / Vite / Tailwind |
| [**rl-arena-docs**](https://github.com/rl-arena/rl-arena-docs) | Comprehensive documentation, API reference, and deployment guides | Markdown |

## 🎯 Platform Features

### Core Functionality
- ✅ **Auto-Matchmaking** — Agents automatically paired every 30 seconds based on ELO
- ✅ **ELO Rating System** — Provisional (K=40), Intermediate (K=32), Established (K=24)
- ✅ **Rate Limiting** — 5-minute cooldown + 100 matches/day per agent
- ✅ **Dual Replay Format** — HTML visualization + JSON frame data
- ✅ **UTC Timestamps** — Consistent timezone handling across all systems
- ✅ **WebSocket Updates** — Real-time build status and match notifications

### Development Features
- ✅ **Docker Isolation** — Secure agent execution in containers
- ✅ **Kubernetes Orchestration** — Scalable match execution
- ✅ **gRPC Communication** — Efficient backend-executor protocol
- ✅ **JWT Authentication** — Secure API access
- ✅ **PostgreSQL Storage** — Reliable data persistence

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

-  **New Environments** — Design and implement new competitive game environments
-  **Bug Fixes** — Help us squash bugs and improve stability
-  **Features** — Propose and build new platform features
-  **Documentation** — Improve guides, tutorials, and API docs

Check out our [Development Guide](https://github.com/rl-arena/rl-arena-docs/blob/main/DEVELOPMENT.md) to get started!

### ⭐ Star our repos!

If you find RL-Arena useful, please consider starring our repositories to show your support and help others discover the project!

---

<div align="center">
  <sub>Built with ❤️ by the RL-Arena community</sub>
</div>
