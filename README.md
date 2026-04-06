# UNIXAI - The MINI JARVIS 🤖

**An Intelligent WhatsApp-to-System Interface & Autonomous AI Orchestrator.**

A headless WhatsApp Web automation engine integrated with advanced AI (Gemini, Groq, Ollama), designed to serve as a remote gateway for desktop control and intelligent system assistance.

## 🚀 Quick Start

```bash
# Install dependencies
pip install -r requirements.txt

# Install Playwright browsers
playwright install chromium

# Run dashboard (port 8888)
python dashboard_app.py

# Or run WhatsApp agent directly
python main.py

# Or use the auto-start script
./unixai.sh  # Auto-venv, port cleanup, dashboard start at :8888
```

---

## 📊 Dashboard

Access at: **http://127.0.0.1:8888**

Features:
- Start/Stop WhatsApp agent
- Switch LLM provider (Gemini/Groq)
- View real-time logs
- Chat statistics & charts
- API keys management
- Terminal command center

---

## 🔧 Configuration

### Dashboard Port

Edit `.env` to change dashboard port:

```bash
DASHBOARD_PORT=8888  # Change to any available port
```

## 📁 Project Structure

```
UNIXAI/
├── .cursor/rules/              # AI Assistant Instructions
│   └── ai-instructions.md      # Guide for AI assistants
│
├── docs/                       # Documentation
│   ├── architecture/           # Architecture docs
│   │   └── architecture.md     # System architecture overview
│   ├── modules/                # Module reference
│   │   └── modules.md          # All modules documented
│   ├── decisions/              # Architectural Decision Records
│   │   └── ADR-*.md            # Decision history
│   ├── FEATURES.txt            # Complete feature list
│   ├── TODO.md                 # Roadmap
│   └── TROUBLESHOOT.txt        # Troubleshooting guide
│
├── channels/whatsapp/          # WhatsApp Web automation
│   ├── agents/                 # AI agents (ReAct pattern)
│   ├── adapters/               # LLM & WhatsApp adapters
│   │   ├── llm/                # LLM providers
│   │   │   ├── gemini.py       # Gemini API client
│   │   │   ├── groq.py         # Groq API client
│   │   │   └── ollama.py       # Ollama client (offline)
│   │   └── whatsapp.py         # WhatsApp client
│   ├── services/               # Business logic
│   ├── rules/                  # Message rules (12 rules)
│   ├── skills/                 # RAG knowledge base
│   ├── monitoring/             # Error monitoring
│   └── logging/                # Chat logging
│
├── dashboard/                  # Web Dashboard (FastAPI)
│   ├── app.py                  # FastAPI application
│   ├── routes/                 # API routes
│   ├── templates/              # HTML templates
│   ├── static/                 # CSS/JS assets
│   └── state.py                # Runtime state
│
├── shared/                     # Foundation (base classes)
│   ├── bases.py                # BaseAgent, BaseService, BaseTool
│   ├── utils.py                # Decorators & utilities
│   ├── errors.py               # Custom exceptions (12 types)
│   └── services.py             # Shared services
│
├── config/                     # Configuration
│   ├── keys/                   # API keys (gitignored)
│   ├── ai_wa.py                # LLM configuration
│   └── prompt_common.txt       # System prompts
│
├── knowledge/                  # RAG Vector DB
│   ├── documents/              # Uploaded files
│   ├── web/                    # Crawled websites
│   └── vector_db/              # ChromaDB storage
│
├── reports/                    # Runtime Data
│   ├── agent/                  # Chat logs, stats
│   └── logs/                   # System logs
│
├── scripts/                    # Utility scripts
├── tools/                      # Tools
│   └── dom/                    # DOM monitoring
│
├── main.py                     # Main entry point (WhatsApp)
├── dashboard_app.py            # Dashboard entry point
├── login.py                    # Quick login helper
├── requirements.txt            # Python dependencies
└── wa_profile/                 # WhatsApp session (gitignored)
```

---

## 📖 Documentation

### **Core Documentation**

| File | Description |
|------|-------------|
| [`docs/architecture/architecture.md`](docs/architecture/architecture.md) | 🏗️ **System architecture overview** |
| [`docs/modules/modules.md`](docs/modules/modules.md) | 📦 **Complete module reference** |
| [`.cursor/rules/ai-instructions.md`](.cursor/rules/ai-instructions.md) | 🤖 **AI assistant guidelines** |
| [`AI_INSTRUCTION.md`](AI_INSTRUCTION.md) | 📘 **Complete development guide** |
| [`docs/FEATURES.txt`](docs/FEATURES.txt) | Complete feature list |
| [`docs/TODO.md`](docs/TODO.md) | Roadmap & planned features |
| [`docs/TROUBLESHOOT.txt`](docs/TROUBLESHOOT.txt) | Troubleshooting guide |
| [`docs/decisions/`](docs/decisions/) | Architectural Decision Records (ADR) |

### **Additional Resources**

| File | Description |
|------|-------------|
| [`config/ai_wa.py`](config/ai_wa.py) | LLM configuration (Gemini/Groq/Ollama) |
| [`config/rules-policy.txt`](config/rules-policy.txt) | AI response rules & policies |
| [`tools/dom/README.md`](tools/dom/README.md) | DOM testing tools |
| [`scripts/README.md`](scripts/README.md) | Utility scripts documentation |

> **💡 Tip:** For development work, start with [`docs/architecture/architecture.md`](docs/architecture/architecture.md) for big picture, then [`docs/modules/modules.md`](docs/modules/modules.md) for module details. AI assistants should read [`.cursor/rules/ai-instructions.md`](.cursor/rules/ai-instructions.md) first.

---

## 🎯 Key Features

### **Core Automation**
- ✅ **WhatsApp Web Automation** - Playwright-based automation
- ✅ **Group Support** - Mention/reply detection only (no spam) - **STRICT ENFORCED**
- ✅ **Private Chat** - Full response mode
- ✅ **Message Deduplication** - Hash-based duplicate detection
- ✅ **Voice Notes** - Auto-transcription with Whisper

### **AI Integration**
- ✅ **Multi-LLM Support** - Gemini, Groq (4 models), Ollama (offline)
- ✅ **Smart Replies** - Context-aware responses (NO emotional core - removed for latency)
- ✅ **Rules Engine** - 12 hardcoded rules (bypasses LLM)
- ✅ **RAG Knowledge Base** - Document upload + web crawling (HYBRID/FULL RAG/GENERAL AI modes)
- ✅ **Guided Freedom** - Creative, varied responses (temperature 0.8, no templates)
- ✅ **Multi-line Output** - Clipboard paste for `/aitest` commands (single reply)
- ✅ **Low Latency** - Direct AI response (no emotional processing overhead)

### **Dashboard & Monitoring**
- ✅ **Web UI** - FastAPI dashboard at http://127.0.0.1:8888
- ✅ **Real-time Logs** - WebSocket updates with phone masking
- ✅ **LLM Switching** - Hot-swap providers (Gemini/Groq/Ollama)
- ✅ **Ollama Control** - Model selector + keep-alive toggle
- ✅ **RAG Mode Toggle** - Switch between HYBRID/FULL RAG
- ✅ **Browser Selection** - Native (System Chrome) vs Bundled (Playwright)
- ✅ **Headless Mode** - CPU savings 30-40%
- ✅ **Statistics** - Chat analytics with Plotly charts
- ✅ **API Key Management** - Add/Edit/Delete keys with rotation

### **Architecture**
- ✅ **Modular Design** - Base classes (BaseAgent, BaseService, BaseTool)
- ✅ **DRY Principle** - Shared utilities, decorators, services
- ✅ **Event-Driven** - Pub/sub event bus
- ✅ **Health Monitoring** - Built-in health checks
- ✅ **Error Handling** - 12 custom exception types
- ✅ **Privacy-First** - Phone number masking, local profile
- ✅ **Security** - Bot commands disabled in groups, authorization required

---

## 🔧 Configuration

### API Keys
Edit files in `config/keys/`:
- `gemini_keys.txt` - Google Gemini API keys
- `groq_key.txt` - Groq API key

### WhatsApp Profile
Default: `wa_profile/`
- Persistent browser profile
- Login session saved
- No need to scan QR every time

---

## 📊 Dashboard

Access at: **http://127.0.0.1:8888**

Features:
- Start/Stop WhatsApp agent
- Switch LLM provider (Gemini/Groq)
- View real-time logs
- Chat statistics & charts
- API keys management
- Terminal command center

---

## 🛠️ Development

### **Coding Standards**

This project follows **DRY (Don't Repeat Yourself)** principle with modular architecture:

- **Use Base Classes:** `BaseAgent`, `BaseService`, `BaseTool` from `shared/bases.py`
- **Type Hints:** Always use type hints for function signatures
- **Error Handling:** Use custom exceptions from `shared/errors.py`
- **Logging:** Use centralized logging from `logging_utils.py`

### **Adding New Features**

1. **Create in shared/:** Base class implementation
2. **Register in agent:** Import and initialize in `WhatsAppAgent`
3. **Add API endpoint:** If needed, add in `dashboard/routes/api.py`
4. **Add UI:** If needed, add in `templates/index.html` + `static/js/`

### **Testing**

```bash
# Run unit tests (if available)
pytest tests/

# Test LLM connection
python scripts/test_ollama.py

# Test API endpoints
curl http://127.0.0.1:8888/api/status
```

### **For AI Assistants**

📘 **Read [`AI_INSTRUCTION.md`](AI_INSTRUCTION.md) first!** It contains:
- Complete architecture overview
- Core systems explanation (Emotional Core, RAG, Multi-LLM)
- Development guidelines & best practices
- Troubleshooting guides
- API reference
- Checklist for understanding the project

---

## 🆕 Latest Updates

### **v2.8.0 - Afternoon Improvements (March 13, 2026)**

| Feature | Description | Benefit |
|---------|-------------|---------|
| **🌐 Dashboard Port 8888** | Changed from 8000, configurable via .env | Avoid conflicts, easy config |
| **🚫 Ignore Groups Toggle** | Hot-swap ON/OFF without restart | Real-time control |
| **📤 Send Logging** | Enhanced debug for message failures | Track send issues |
| **🎨 Ollama Temp 0.8** | llama3.2:1b: 0.6 → 0.8 | More creative responses |
| **📝 /aitest Prompt** | 23 lines → 7 lines (90% smaller) | Faster, same security |
| **🌍 Bundled Browser** | Default: Playwright Chromium | 100% Windows compatible |

**Before:**
```
❌ Port 8000 conflicts
❌ Ignore Groups requires restart
❌ Send failures not logged
❌ Ollama 1b temperature 0.6 (conservative)
❌ /aitest prompt 500 tokens
❌ Native browser (Linux-only paths)
```

**After:**
```
✅ Port 8888 (configurable)
✅ Ignore Groups hot-swap
✅ Send failure logging
✅ Ollama 1b temperature 0.8 (creative)
✅ /aitest prompt 50 tokens
✅ Bundled Chromium (cross-platform)
```

### **v2.7.0 - Latency Optimization (March 13, 2026)**

| Feature | Description | Benefit |
|---------|-------------|---------|
| **🧠 Emotional Core Removed** | Removed 4-layer emotional processing | **-50-200ms latency** ✅ |
| **⏱️ Typing Delay Removed** | No more artificial delay simulation | **-1-8s latency** ✅ |
| **🤖 Qwen API Removed** | Deleted paid API adapter | **Cleaner codebase** ✅ |
| **📋 LLM Adapters Simplified** | Removed emotional_metadata processing | **Faster response** ✅ |

**Before:**
```
❌ Emotional Core processing → +50-200ms
❌ Typing delay simulation → +1-8s
❌ Qwen paid API → Cost money
❌ Emotional metadata in all adapters → Complex
```

**After:**
```
✅ Direct AI response → Fast & simple
✅ No artificial delays → Instant reply
✅ Free LLM only → Gemini, Groq, Ollama
✅ Clean adapters → No emotional overhead
```

### **v2.6.0 - Quality of Life Improvements**

| Feature | Description | Benefit |
|---------|-------------|---------|
| **🔌 Port 8888 Auto-Cleanup** | `unixai.sh` auto-kill port sebelum start | No more "Address in use" errors |
| **📋 Multi-line Message Fix** | Clipboard paste for `/aitest` output | Single reply instead of multiple |
| **🎨 Guided Freedom** | Temperature 0.8, creative responses | Varied, natural, human-like replies |

**Before:**
```
❌ Port 8888 conflict → Manual kill
❌ /aitest output → 2 separate replies
❌ Response template → Robotic, repetitive
```

**After:**
```
✅ Auto port cleanup → Smooth startup
✅ /aitest output → 1 unified reply
✅ Creative AI → Natural, varied responses
```

---

## ⚠️ Compliance

**Important:** This project uses WhatsApp Web automation via Playwright (not official API).

**Risks:**
- May violate WhatsApp Terms of Service
- Could result in account restrictions
- UI changes may break automation

**Recommendation:** Use official [WhatsApp Business Platform](https://business.whatsapp.com/) for production.

---

## 📝 License

Internal project - UNIXAI

---

## 👨‍💻 Author

Pande Permadi (unixland)
