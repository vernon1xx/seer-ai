# 👁️ SEER AI

### *Envision Your World*
**See Everything. Everywhere. Reliably.**

---

<p align="center">
  <a href="https://vernon1xx.github.io/seer-ai/prototypes/SEER-AI-v4.html">
    <img src="docs/assets/seer-ai-cube-preview.png" alt="SEER AI Cube Interface" width="600">
  </a>
</p>

## 🎮 Live Demo

**[▶️ Try SEER AI Prototype](https://vernon1xx.github.io/seer-ai/prototypes/SEER-AI-v4.html)**

> 🖱️ **Drag** to rotate the cube | 🎤 **Voice** commands in Chrome | 📱 **Touch** supported

---

## 🎯 What is SEER AI?

SEER AI is an **AI-powered industrial facility management platform** that combines:

- 🎮 **3D Visual Navigation** — Interactive cube interface for intuitive access
- 🤖 **Natural Language AI** — Ask questions like "Show me LOTO for Dry Kiln 2"
- 🗣️ **Voice Commands** — Hands-free operation with speech recognition
- 🗺️ **Hierarchical Facility Maps** — Drill down from site → building → equipment → component
- 🔒 **LOTO Procedures** — Integrated lockout/tagout with MCC diagrams
- ⚙️ **Cube Configurator** — Admin tool to customize faces, tiles, and links
- 🐳 **Docker Deployment** — Complete containerized stack
- 🧠 **Local AI Support** — Ollama integration for offline operation

---

## 🚀 Quick Start

### View the Prototype

1. Download `prototypes/SEER-AI-v4.html`
2. Open in Chrome (for voice support)
3. **Drag** to rotate the cube
4. **Click** tiles to open detail panels
5. **Type or speak** queries in the chat box

### Docker Deployment (Coming Soon)

```bash
git clone https://github.com/vernon1xx/seer-ai.git
cd seer-ai
docker-compose up -d
```

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         SEER AI CUBE                            │
│                    (React + Three.js Frontend)                  │
└─────────────────────────────────────────────────────────────────┘
                               │
                               ▼
┌─────────────────────────────────────────────────────────────────┐
│                      SEER AI BACKEND                            │
│                    (Python FastAPI)                             │
└─────────────────────────────────────────────────────────────────┘
         │              │              │              │
         ▼              ▼              ▼              ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
│ PostgreSQL  │ │   MinIO     │ │   Ollama    │ │  InfluxDB   │
│ (Structured)│ │  (Files)    │ │ (Local AI)  │ │(Time-series)│
└─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘
```

---

## 🧊 The 6-Face Cube

| Face | Position | Content |
|------|----------|---------|
| **Facility Map** | Top | Site overview, buildings, navigation |
| **Administration** | Front | HR, handbook, forms, directory |
| **Safety** | Right | LOTO, JSAs, incidents, training |
| **Production** | Back | Dashboard, schedule, quality, KPIs |
| **Maintenance** | Left | CMMS, work orders, PMs, equipment |
| **Environmental** | Bottom | Air, water, waste, permits, regulations |

---

## 🛠️ SEER Tools Suite

### Configuration Tools
| Tool | Purpose |
|------|---------|
| **Cube Configurator** ⭐ | Customize faces, tiles, links — no coding required |
| Theme Editor | Colors, fonts, branding |
| User/Role Manager | Access control |

### Data Collection Tools
| Tool | Purpose |
|------|---------|
| Facility Builder | Create site/building/area hierarchy |
| Equipment Importer | CSV/Excel bulk upload |
| Document Uploader | File management |

### Procedure Tools
| Tool | Purpose |
|------|---------|
| LOTO Procedure Builder | Safety lockout/tagout procedures |
| JSA Builder | Job Safety Analysis forms |
| PM Template Builder | Preventive maintenance templates |

---

## 📦 Industry Templates

SEER AI supports exportable JSON configurations. Pre-built templates available:

| Template | Industry |
|----------|----------|
| Lumber Mill Pro | Wood products, sawmills |
| Water Treatment | Municipal water/wastewater |
| Manufacturing | General industrial |
| Utilities | Power generation |

> 💡 Create your own templates and share them!

---

## 📚 The Industrial AI Book Series

SEER AI is part of a comprehensive 6-book series for deploying AI in industrial environments:

| Book | Title | Status |
|------|-------|--------|
| 1 | Building Your Foundation | ✅ Complete |
| 2 | Mastering Your Foundation | 🔄 In Progress |
| 3 | Seeing Your Data (Grafana) | 📋 Planned |
| 4 | Automation (N8N) | 📋 Planned |
| 5 | AI Mastery | ✅ Complete |
| 6 | Production & Enterprise | 📋 Planned |

---

## 🧩 SEER Maintenance (CMMS)

A complete Computerized Maintenance Management System:
- Work order management
- Preventive maintenance scheduling
- Equipment registry
- LOTO procedure integration
- Parts inventory
- Vendor management

---

## 🔗 Integrations

| System | Purpose | Status |
|--------|---------|--------|
| Docker | Container orchestration | ✅ Ready |
| Ollama | Local AI processing | ✅ Ready |
| PostgreSQL | Structured data | 🔄 Planned |
| InfluxDB | Time-series data | 🔄 Planned |
| Grafana | Dashboards | 🔄 Planned |
| N8N | Workflow automation | 🔄 Planned |
| MCP Toolkit | Claude Desktop | 🔄 Planned |

---

## 🎯 Target Industries

- 🪵 Lumber & Wood Products
- 🏭 Manufacturing
- 💧 Water & Wastewater
- ⚡ Utilities
- 🏗️ Facilities Management
- 🌿 Environmental Compliance

---

## 📖 Documentation

- [ROADMAP.md](ROADMAP.md) — Development roadmap
- [Architecture Overview](docs/architecture/overview.md)
- [Cube Configuration Schema](docs/architecture/cube-config-schema.md)
- [API Documentation](docs/api/) (Coming Soon)

---

## 🤝 Contributing

We welcome contributions! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## 📄 License

MIT License — See [LICENSE](LICENSE) for details.

---

## 👤 Author

**Vernon Buchanan**
- Environmental Compliance & Safety Lead
- SDS Lumber Company
- GitHub: [@vernon1xx](https://github.com/vernon1xx)

---

## 🌟 Star History

If SEER AI helps you manage your facility, please ⭐ this repo!

---

<p align="center">
  <strong>SEER AI</strong> — <em>Envision Your World</em>
</p>
