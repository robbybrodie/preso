# Slide 1: Platform Foundation
## Red Hat AI 3 on OpenShift - Your AI Infrastructure

---

## 🎯 The Challenge: Chef → Ansible Migration

**Business Driver**: Modernize legacy Chef automation infrastructure

- Chef license costs and EOL concerns
- Need to centralize on Ansible Automation Platform (AAP)
- Manual translation is time-consuming and error-prone
- Require compliance and validation guardrails

**Solution**: AI-augmented migration using your existing infrastructure

---

## 🏗️ Your Platform Stack

```mermaid
graph TB
    subgraph OCP[OpenShift Container Platform 4.x]
        subgraph RHAI[Red Hat AI 3 / OpenShift AI]
            LS[Llama Stack Runtime]
            GPU[GPU Node Pool<br/>NVIDIA A100/H100]
            Models[Model Serving<br/>Llama 3, Mistral, Granite]
        end
        
        subgraph Apps[Application Services]
            UI[x2a-ui<br/>Next.js Frontend]
            API[x2a-api<br/>FastAPI Backend]
            Conv[Conversion Engine]
        end
        
        subgraph Integration[Integration Layer]
            AAP[Ansible Automation<br/>Platform]
            Git[Git Repository<br/>GitLab/GitHub]
            DevHub[Red Hat Developer Hub]
        end
    end
    
    LS --> GPU
    LS --> Models
    UI --> API
    API --> Conv
    API --> LS
    Conv --> AAP
    Conv --> Git
    
    style RHAI fill:#cc0000,color:#fff
    style Apps fill:#0066cc,color:#fff
    style Integration fill:#92d400,color:#000
```

---

## 🔴 Red Hat AI 3: Enterprise AI Platform

**What it provides:**

| Component | Capability |
|-----------|------------|
| **Llama Stack** | Open-source AI framework for agents and models |
| **GPU Acceleration** | On-cluster inference with vLLM runtime |
| **Model Serving** | Deploy Llama 3, Mistral, Granite, Phi models |
| **Security** | OAuth, RBAC, network policies - all within OpenShift |
| **Integration** | Native connections to AAP, Git, Developer Hub |

**Key Value**: Run powerful AI workloads securely on your infrastructure - no external API calls required

---

## 🔧 OpenShift Foundation Benefits

```mermaid
graph LR
    A[OpenShift Platform] --> B[Container Orchestration]
    A --> C[GPU Resource Management]
    A --> D[Network Security]
    A --> E[CI/CD Pipelines]
    
    B --> F[Auto-scaling AI Services]
    C --> G[Efficient LLM Inference]
    D --> H[Zero External Dependencies]
    E --> I[GitOps Workflows]
    
    style A fill:#cc0000,color:#fff
    style F fill:#92d400,color:#000
    style G fill:#92d400,color:#000
    style H fill:#92d400,color:#000
    style I fill:#92d400,color:#000
```

**Why this matters:**
- ✅ Enterprise-grade reliability and support
- ✅ GPU resources already available
- ✅ Secure, air-gapped deployment possible
- ✅ Integrates with existing automation workflows

---

## 📊 Deployment Architecture

```mermaid
graph TB
    subgraph External[External Access]
        Users[Migration Engineers]
        DevTeam[Development Team]
    end
    
    subgraph OpenShift[OpenShift Cluster]
        subgraph NS1[x2a-migration Namespace]
            Route1[OpenShift Route<br/>HTTPS/OAuth]
            UI1[x2a-ui Pods<br/>3 replicas]
            API1[x2a-api Pods<br/>3 replicas]
            PVC1[Persistent Storage<br/>Cookbooks & Playbooks]
        end
        
        subgraph NS2[red-hat-ai Namespace]
            LlamaStack[Llama Stack Operator]
            InferenceEngine[vLLM Inference<br/>GPU-enabled]
            VectorDB[(Vector Database<br/>Chroma/PGVector)]
            EmbedService[Embedding Service<br/>Granite-embedder]
        end
        
        subgraph NS3[ansible-automation Namespace]
            AAP[AAP Controller]
            Jobs[Job Execution Pods]
        end
    end
    
    Users --> Route1
    DevTeam --> Route1
    Route1 --> UI1
    UI1 --> API1
    API1 --> PVC1
    API1 --> LlamaStack
    LlamaStack --> InferenceEngine
    LlamaStack --> VectorDB
    LlamaStack --> EmbedService
    API1 --> AAP
    AAP --> Jobs
    
    style NS1 fill:#0066cc,color:#fff
    style NS2 fill:#cc0000,color:#fff
    style NS3 fill:#92d400,color:#000
```

---

## 💡 Key Takeaway

**You already have everything needed:**
- ✅ OpenShift cluster with GPU nodes
- ✅ Red Hat AI 3 with Llama Stack
- ✅ Integration with AAP
- ✅ Secure, on-premises AI capabilities

**Next**: Understanding how AI Agents work within this stack

