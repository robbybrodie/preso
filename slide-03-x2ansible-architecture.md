# Slide 3: The x2Ansible Solution
## Architecture & Component Flow

---

## 🎯 x2Ansible: Three-Tier Architecture

```mermaid
graph TB
    subgraph Presentation[Presentation Layer]
        UI[x2a-ui<br/>━━━━━━━━━━━━━━━━<br/>Next.js 14 / React<br/>TypeScript<br/>━━━━━━━━━━━━━━━━<br/>• File upload interface<br/>• Real-time conversion display<br/>• Diff viewer<br/>• Export management]
    end
    
    subgraph Business[Business Logic Layer]
        API[x2a-api<br/>━━━━━━━━━━━━━━━━<br/>FastAPI / Python<br/>Async Workers<br/>━━━━━━━━━━━━━━━━<br/>• REST endpoints<br/>• WebSocket streaming<br/>• Validation orchestration<br/>• Session management]
    end
    
    subgraph Intelligence[Intelligence Layer]
        Agent[Llama Stack Agent<br/>━━━━━━━━━━━━━━━━<br/>AI Orchestration<br/>━━━━━━━━━━━━━━━━<br/>• Conversion planning<br/>• Quality recommendations<br/>• Knowledge retrieval]
        
        Converter[Conversion Engine<br/>━━━━━━━━━━━━━━━━<br/>Python Parsers<br/>━━━━━━━━━━━━━━━━<br/>• Chef DSL parsing<br/>• Ansible generation<br/>• Syntax transformation]
        
        Validator[Validation Tools<br/>━━━━━━━━━━━━━━━━<br/>ansible-lint MCP<br/>━━━━━━━━━━━━━━━━<br/>• Profile-based checks<br/>• Best practice enforcement<br/>• Error reporting]
    end
    
    subgraph Storage[Storage & Integration]
        DB[(Session Store<br/>Redis/PostgreSQL)]
        FS[(File Storage<br/>Persistent Volume)]
        GIT[Git Repository<br/>GitLab/GitHub]
        AAP[Ansible Automation<br/>Platform]
    end
    
    UI -->|HTTPS| API
    API --> Agent
    API --> Converter
    API --> Validator
    API --> DB
    API --> FS
    Converter --> GIT
    Validator --> AAP
    Agent --> Converter
    Agent --> Validator
    
    style Presentation fill:#0066cc,color:#fff
    style Business fill:#cc0000,color:#fff
    style Intelligence fill:#92d400,color:#000
    style Storage fill:#666,color:#fff
```

---

## 🌐 x2a-ui: User Interface Components

**Source**: [github.com/x2ansible/x2a-ui](https://github.com/x2ansible/x2a-ui)

```mermaid
graph TB
    subgraph UI[x2a-ui Application]
        subgraph Pages[Pages / Routes]
            Home[Home Page<br/>• Project overview<br/>• Quick start]
            Upload[Upload Page<br/>• File/folder upload<br/>• Drag & drop<br/>• Validation]
            Analyze[Analysis Dashboard<br/>• Cookbook structure<br/>• Complexity metrics<br/>• Recommendations]
            Convert[Conversion Workspace<br/>• Side-by-side view<br/>• Conversion progress<br/>• Real-time streaming]
            Review[Review & Export<br/>• Diff viewer<br/>• Validation results<br/>• Git export options]
        end
        
        subgraph Components[Shared Components]
            FileTree[File Tree Browser]
            CodeEditor[Code Editor<br/>Monaco/Syntax Highlight]
            DiffView[Diff Viewer<br/>Unified/Split modes]
            ChatPanel[AI Assistant Panel<br/>Q&A Interface]
            StatusBar[Status & Progress]
        end
        
        subgraph Services[Frontend Services]
            APIClient[API Client<br/>Axios/Fetch]
            WSClient[WebSocket Client<br/>SSE for streaming]
            StateManager[State Management<br/>React Context/Zustand]
            Router[Next.js Router]
        end
    end
    
    Home --> Upload
    Upload --> Analyze
    Analyze --> Convert
    Convert --> Review
    
    Upload --> FileTree
    Analyze --> CodeEditor
    Convert --> DiffView
    Convert --> ChatPanel
    Review --> DiffView
    
    FileTree --> APIClient
    CodeEditor --> APIClient
    DiffView --> APIClient
    ChatPanel --> WSClient
    StatusBar --> WSClient
    
    APIClient --> API[x2a-api]
    WSClient --> API
    
    style Pages fill:#0066cc,color:#fff
    style Components fill:#92d400,color:#000
    style Services fill:#cc0000,color:#fff
```

**Key UI Features:**
- 📤 **Drag-and-drop upload** for Chef cookbooks
- 🔍 **Live analysis** with complexity scoring
- 🤖 **AI chat assistant** for questions during migration
- 📊 **Side-by-side diff** showing Chef vs Ansible
- ✅ **Real-time validation** feedback
- 📦 **One-click export** to Git/AAP

---

## ⚙️ x2a-api: Backend Service Architecture

**Source**: [github.com/x2ansible/x2a-api](https://github.com/x2ansible/x2a-api)

```mermaid
graph TB
    subgraph API[x2a-api Service]
        subgraph Endpoints[REST API Endpoints]
            E1[POST /api/upload<br/>━━━━━━━━━━━━━━━━<br/>• Multipart file upload<br/>• Cookbook validation<br/>• Size/format checks]
            
            E2[POST /api/analyze<br/>━━━━━━━━━━━━━━━━<br/>• Structure parsing<br/>• Complexity analysis<br/>• Dependency mapping]
            
            E3[POST /api/convert<br/>━━━━━━━━━━━━━━━━<br/>• Chef → Ansible translation<br/>• Streaming progress<br/>• AI-assisted enhancement]
            
            E4[POST /api/validate<br/>━━━━━━━━━━━━━━━━<br/>• ansible-lint checks<br/>• Profile selection<br/>• Error explanations]
            
            E5[POST /api/chat<br/>━━━━━━━━━━━━━━━━<br/>• RAG-powered Q&A<br/>• Context-aware responses<br/>• Migration guidance]
            
            E6[POST /api/export<br/>━━━━━━━━━━━━━━━━<br/>• Git commit & push<br/>• AAP job template<br/>• Archive download]
        end
        
        subgraph Orchestration[Orchestration Layer]
            Manager[Session Manager<br/>━━━━━━━━━━━━━━━━<br/>• Track user sessions<br/>• Manage state<br/>• Handle timeouts]
            
            AgentRegistry[Agent Registry<br/>━━━━━━━━━━━━━━━━<br/>• Single agent per session<br/>• Connection pooling<br/>• Lifecycle management]
            
            StreamHandler[Stream Handler<br/>━━━━━━━━━━━━━━━━<br/>• SSE implementation<br/>• Progress events<br/>• Error recovery]
        end
        
        subgraph Workers[Worker Processes]
            W1[Gunicorn Workers<br/>• Async support<br/>• Timeout handling<br/>• Load balancing]
        end
    end
    
    subgraph External[External Services]
        LlamaStack[Llama Stack<br/>Agent Framework]
        MCP[MCP Tools<br/>ansible-lint]
        Storage[(Redis + PVC)]
        Git[Git Repositories]
    end
    
    E1 --> Manager
    E2 --> Manager
    E3 --> Manager
    E3 --> StreamHandler
    E4 --> Manager
    E5 --> Manager
    E6 --> Manager
    
    Manager --> AgentRegistry
    StreamHandler --> AgentRegistry
    AgentRegistry --> LlamaStack
    E4 --> MCP
    Manager --> Storage
    E6 --> Git
    
    W1 --> E1
    W1 --> E2
    W1 --> E3
    
    style Endpoints fill:#cc0000,color:#fff
    style Orchestration fill:#0066cc,color:#fff
    style Workers fill:#92d400,color:#000
```

---

## 🔄 API Request Flow Examples

### Example 1: File Upload → Analysis

```mermaid
sequenceDiagram
    participant Browser
    participant Nginx
    participant API as x2a-api
    participant Storage
    participant Agent
    
    Browser->>Nginx: POST /api/upload<br/>multipart/form-data
    Nginx->>API: Forward request
    API->>API: Validate file size/type
    API->>Storage: Save to PVC<br/>/data/sessions/{id}/
    Storage-->>API: File path
    API->>API: Create session record
    API-->>Browser: 200 OK + session_id
    
    Browser->>API: POST /api/analyze<br/>{session_id}
    API->>Agent: Initialize analysis agent
    Agent->>Agent: Parse cookbook structure
    Agent->>Agent: Identify resources
    Agent->>Agent: Calculate complexity
    Agent-->>API: Analysis results
    API->>Storage: Cache results
    API-->>Browser: JSON response with metrics
```

---

### Example 2: Streaming Conversion

```mermaid
sequenceDiagram
    participant Browser
    participant API as x2a-api
    participant Agent
    participant Converter
    participant Validator
    
    Browser->>API: POST /api/convert<br/>Accept: text/event-stream
    API->>API: Open SSE connection
    API->>Agent: Start conversion
    
    loop For each resource
        Agent->>Converter: Convert resource
        Converter-->>Agent: Ansible YAML
        Agent->>API: Progress event
        API-->>Browser: data: {"progress": 25, "status": "Converting recipes"}
    end
    
    Agent->>Validator: Validate playbook
    Validator-->>Agent: Lint results
    Agent->>API: Complete event
    API-->>Browser: data: {"progress": 100, "complete": true}
    API->>API: Close connection
```

---

## 🛠️ Agent Integration Pattern

**How x2a-api leverages Llama Stack agents:**

```mermaid
graph TB
    subgraph Request[API Request Handler]
        Req[Incoming Request]
        Sess[Session Lookup]
    end
    
    subgraph Registry[Agent Registry Pattern]
        Check{Agent<br/>Exists?}
        Reuse[Reuse Existing Agent]
        Create[Create New Agent]
    end
    
    subgraph Agent[Llama Stack Agent]
        Tools[Registered Tools:<br/>• chef_parser<br/>• ansible_generator<br/>• validator<br/>• git_ops]
        Memory[Session Memory:<br/>• Conversation history<br/>• Conversion context<br/>• User preferences]
        RAG[Knowledge Base:<br/>• Migration patterns<br/>• Best practices<br/>• Example mappings]
    end
    
    subgraph Response[Response Builder]
        Format[Format Results]
        Stream[Stream Events]
        Return[Return to Client]
    end
    
    Req --> Sess
    Sess --> Check
    Check -->|Yes| Reuse
    Check -->|No| Create
    Reuse --> Tools
    Create --> Tools
    Tools --> Memory
    Memory --> RAG
    RAG --> Format
    Format --> Stream
    Stream --> Return
    
    style Registry fill:#cc0000,color:#fff
    style Agent fill:#92d400,color:#000
```

**Key Pattern Benefits:**
- ✅ **Agent reuse** - maintains context across requests
- ✅ **Memory persistence** - agent remembers conversation
- ✅ **Tool access** - can call converters, validators, Git
- ✅ **RAG integration** - answers questions with retrieved knowledge

---

## 🔐 Security & Error Handling

### Timeout Protection

```mermaid
graph LR
    Request[API Request] --> Wrapper[AsyncIO Timeout Wrapper]
    Wrapper --> Agent[Agent Processing]
    
    Agent -->|Success| Response[200 Response]
    Agent -->|Timeout| Timeout[408 Timeout<br/>Graceful response]
    Agent -->|Error| Error[500 Error<br/>Logged & reported]
    
    style Wrapper fill:#92d400,color:#000
    style Timeout fill:#ff9900,color:#000
    style Error fill:#cc0000,color:#fff
```

**Protections in place:**
- ⏱️ **120s timeout** for validation endpoints
- ⏱️ **300s timeout** for conversion endpoints  
- 📦 **10MB size limit** on uploads
- 🔒 **Session isolation** - no cross-contamination
- 🔄 **Graceful degradation** on agent failures

---

### Model Context Protocol (MCP) Integration

```mermaid
graph TB
    subgraph API[x2a-api]
        Validate[Validation Request]
    end
    
    subgraph MCP[MCP Layer]
        Client[MCP Client]
        ToolGroup[ansible-lint Toolgroup]
    end
    
    subgraph LlamaStack[Llama Stack]
        Agent[Llama Agent]
        ToolRegistry[Tool Registry]
    end
    
    subgraph Execution[Execution]
        Lint[ansible-lint Process]
        Rules[Lint Profiles:<br/>• basic<br/>• moderate<br/>• safety]
    end
    
    Validate --> Agent
    Agent --> ToolRegistry
    ToolRegistry --> Client
    Client --> ToolGroup
    ToolGroup --> Lint
    Lint --> Rules
    Rules -->> Lint
    Lint -->> ToolGroup
    ToolGroup -->> Client
    Client -->> ToolRegistry
    ToolRegistry -->> Agent
    Agent -->> Validate
    
    style MCP fill:#0066cc,color:#fff
    style Execution fill:#92d400,color:#000
```

**Why MCP matters:**
- 🔌 **Standardized tool protocol** for AI agents
- 🧰 **Structured responses** from ansible-lint
- 📊 **Profile-based validation** (basic, moderate, safety)
- 🔄 **Reusable across agents**

---

## 💡 Key Takeaways

**x2a-ui provides:**
- Modern, responsive interface for migration workflow
- Real-time feedback and AI-assisted guidance
- Integrated diff viewer and export tools

**x2a-api provides:**
- RESTful endpoints for all migration operations
- Streaming support for long-running conversions
- Agent orchestration with Llama Stack
- Secure session management and error handling

**Together they create:**
- Seamless user experience
- AI-augmented automation
- Enterprise-grade reliability

**Next**: Complete end-to-end workflow

