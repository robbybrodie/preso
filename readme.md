# x2Ansible Presentation Materials

This repository contains **two sets** of presentation materials for explaining the x2Ansible Chef-to-Ansible migration solution powered by Red Hat AI 3 on OpenShift.

## 📑 Contents

### 👔 Executive Presentation (For Senior Management)

**Best for:** VPs, Directors, Senior Managers, Business Leaders

- **[EXECUTIVE-INDEX.md](./EXECUTIVE-INDEX.md)** - Executive presentation guide
- **[executive-slide-01-current-infrastructure.md](./executive-slide-01-current-infrastructure.md)** - Infrastructure inventory (ACM, OpenShift, GPUs)
- **[executive-slide-02-llama-stack-components.md](./executive-slide-02-llama-stack-components.md)** - Llama Stack explained (Inference, Vector DB, Agents)
- **[executive-slide-03-what-is-an-agent.md](./executive-slide-03-what-is-an-agent.md)** - AI agents deep dive with business value

**Duration:** ~40 minutes + Q&A | **Focus:** Business value, ROI, capabilities

---

### 🔧 Technical Presentation (For Technical Teams)

**Best for:** Engineers, Architects, DevOps Teams, Technical Managers

- **[INDEX.md](./INDEX.md)** - Complete technical presentation guide
- **[slide-01-platform-foundation.md](./slide-01-platform-foundation.md)** - Platform overview and infrastructure
- **[slide-02-ai-agents-and-llama-stack.md](./slide-02-ai-agents-and-llama-stack.md)** - Understanding AI agents and Llama Stack components
- **[slide-03-x2ansible-architecture.md](./slide-03-x2ansible-architecture.md)** - x2a-ui and x2a-api architecture
- **[slide-04-end-to-end-workflow.md](./slide-04-end-to-end-workflow.md)** - Complete migration workflow and business value

**Duration:** ~55 minutes + Q&A | **Focus:** Architecture, implementation, technical details

## 🚀 Quick Start

### For Executive Presentations
1. Start with **[EXECUTIVE-INDEX.md](./EXECUTIVE-INDEX.md)**
2. Review executive slides 1 → 2 → 3
3. Focus on business value and ROI

### For Technical Presentations
1. Start with **[INDEX.md](./INDEX.md)**
2. Review technical slides 1 → 2 → 3 → 4
3. Deep dive on architecture and implementation

**Viewing:** Use any Markdown viewer with Mermaid diagram support (VS Code recommended)

## 🎯 Choose Your Presentation

| Audience | Presentation | Duration | Focus |
|----------|--------------|----------|-------|
| **Senior Management**<br/>VPs, Directors, Business Leaders | 👔 Executive (3 slides) | 40 min + Q&A | ROI, capabilities, business value |
| **Technical Teams**<br/>Engineers, Architects, DevOps | 🔧 Technical (4 slides) | 55 min + Q&A | Architecture, implementation, workflows |

## 💡 Key Features

**Both Presentation Decks:**
- ✅ Extensive Mermaid diagrams for visual learning
- ✅ Progressive complexity (foundational → detailed)
- ✅ Real-world architecture based on x2ansible projects
- ✅ Explainability-focused for audiences without AI background

**Executive Deck Adds:**
- ✅ Business-focused language and concepts
- ✅ ROI calculations and productivity metrics
- ✅ Infrastructure inventory (ACM, OpenShift, L40s/A100s)
- ✅ Strategic decision-making framework

**Technical Deck Adds:**
- ✅ Detailed component architecture
- ✅ API and UI implementation details
- ✅ Complete sequence diagrams
- ✅ Deployment topology and resource specs

## 🔗 Related Projects

- **x2a-ui**: https://github.com/x2ansible/x2a-ui
- **x2a-api**: https://github.com/x2ansible/x2a-api

## 📊 Presentation Time

| Deck | Core Content | With Q&A | Express Version |
|------|--------------|----------|-----------------|
| **👔 Executive** | 35-40 min (3 slides) | 50-55 min | 15-20 min (key points only) |
| **🔧 Technical** | 55 min (4 slides) | 70 min | 25 min (Slides 1 & 4 only) |

## 🛠️ Viewing Options

### VS Code (Recommended)
Install: **Markdown Preview Enhanced** extension
- Native Mermaid support
- Clean rendering
- Easy navigation

### GitHub/GitLab
Push to repository and view directly
- Mermaid renders automatically
- Shareable links

### Convert to HTML/PDF
```bash
# Install pandoc and mermaid-filter
pandoc slide-*.md -o presentation.pdf
```

## 📝 Customization

Before presenting, customize:
- GPU hardware specifications
- OpenShift version numbers
- Storage backend details
- Organization-specific requirements

See [INDEX.md](./INDEX.md) for detailed customization notes.

---

**Created for**: Technical presentations on AI-augmented automation  
**License**: Apache 2.0 (aligns with x2ansible projects)  
**Maintained by**: Red Hat Solutions Architecture
