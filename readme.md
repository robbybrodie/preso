# x2Ansible Presentation Materials

This repository contains presentation materials for explaining the x2Ansible Chef-to-Ansible migration solution powered by Red Hat AI 3 on OpenShift.

## 📑 Contents

- **[INDEX.md](./INDEX.md)** - Complete presentation guide with delivery tips
- **[slide-01-platform-foundation.md](./slide-01-platform-foundation.md)** - Platform overview and infrastructure
- **[slide-02-ai-agents-and-llama-stack.md](./slide-02-ai-agents-and-llama-stack.md)** - Understanding AI agents and Llama Stack components
- **[slide-03-x2ansible-architecture.md](./slide-03-x2ansible-architecture.md)** - x2a-ui and x2a-api architecture
- **[slide-04-end-to-end-workflow.md](./slide-04-end-to-end-workflow.md)** - Complete migration workflow and business value

## 🚀 Quick Start

1. **Start with [INDEX.md](./INDEX.md)** for presentation overview and tips
2. Review slides in order (1 → 2 → 3 → 4)
3. View in any Markdown viewer with Mermaid diagram support

## 🎯 Target Audience

Technical professionals who:
- Understand infrastructure and automation
- May not have extensive AI/ML experience
- Need to understand how AI agents work
- Want to see practical AI application in DevOps

## 💡 Key Features

- ✅ Extensive Mermaid diagrams for visual learning
- ✅ Progressive complexity (foundational → detailed)
- ✅ Real-world architecture based on x2ansible/x2a-ui and x2a-api
- ✅ Explainability-focused for non-AI experts
- ✅ Business value and ROI focus

## 🔗 Related Projects

- **x2a-ui**: https://github.com/x2ansible/x2a-ui
- **x2a-api**: https://github.com/x2ansible/x2a-api

## 📊 Presentation Time

- **Full deck**: ~55 minutes
- **With Q&A**: ~70 minutes
- **Executive summary**: ~25 minutes (Slides 1 & 4 only)

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
