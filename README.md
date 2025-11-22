# AI Voice Agents Challenge - 10 Days Project

🎯 **Day 1 COMPLETE** ✅ | Building Real-Time Voice AI Agents with LiveKit, Gemini, and Murf Falcon

Welcome to my implementation of the **AI Voice Agents Challenge** by [murf.ai](https://murf.ai)!

## 🏆 Challenge Overview

**Build 10 AI Voice Agents over 10 Days** using Murf Falcon – the consistently fastest TTS API!

### Challenge Format

- One task provided each day with reference materials
- Build voice agents with specific personas and skills
- Share progress on GitHub and LinkedIn
- Win rewards and level up your AI voice agent skills!

## 📊 Progress Tracker

- ✅ **Day 1**: Get Your Starter Voice Agent Running - **COMPLETED**
- ⏳ **Day 2-10**: Coming soon...

## 🚀 Tech Stack

- **Voice Infrastructure**: [LiveKit Agents](https://docs.livekit.io/agents) - Real-time voice framework
- **Speech-to-Text**: [Deepgram Nova-3](https://deepgram.com/) - High-accuracy transcription (80-250ms)
- **Language Model**: [Google Gemini 2.5 Flash](https://ai.google.dev/) - Fast, intelligent responses (100-500ms)
- **Text-to-Speech**: [Murf Falcon](https://murf.ai/api) - Ultra-fast, natural voice (50-150ms) ⚡
- **Frontend**: Next.js 15.5.2 with TypeScript & React
- **Backend**: Python 3.11 with LiveKit Agents SDK

**Total Pipeline Latency**: 350-1250ms (STT + LLM + TTS)

## 📁 Repository Structure

```
murf_ai_ten-days-of-voice-agents-2025/
├── backend/              # LiveKit Agents backend with Murf Falcon TTS
│   ├── src/
│   │   ├── agent.py      # Main agent orchestration (BVC removed for local dev)
│   │   └── __init__.py
│   ├── pyproject.toml    # Python dependencies
│   ├── uv.lock           # Dependency lock file
│   ├── Dockerfile        # Production container
│   └── README.md         # Backend documentation
├── frontend/             # Next.js voice interaction UI
│   ├── app/              # Next.js app directory
│   ├── components/       # React components
│   ├── hooks/            # Custom React hooks
│   ├── package.json      # Node dependencies
│   └── README.md         # Frontend documentation
├── docs/                 # Comprehensive documentation
│   ├── START_HERE.md            # First-time setup guide
│   ├── SETUP_GUIDE.md           # Detailed configuration
│   ├── QUICK_START.md           # Rapid deployment
│   ├── TESTING_INSTRUCTIONS.md  # Testing procedures
│   ├── PIPELINE_ANALYSIS.md     # Performance metrics & optimization
│   ├── DAY_1_README.md         # Day 1 completion notes
│   └── PROJECT_ORGANIZATION.md  # Repository structure
├── challenges/           # Daily challenge descriptions
│   └── Day 1 Task.md
├── start_app.sh          # Convenience script (all services)
├── .gitignore            # Comprehensive git exclusions
└── README.md             # This file
```

## ⚡ Quick Start

### Prerequisites

- **Python 3.9+** with [uv](https://docs.astral.sh/uv/) package manager
- **Node.js 18+** with pnpm (or npm)
- **LiveKit Server** for local development
- **API Keys**: Deepgram, Murf, Google Gemini

### 1. Clone Repository

```bash
git clone https://github.com/dayanandXdarpan/murf_ai_ten-days-of-voice-agents-2025.git
cd murf_ai_ten-days-of-voice-agents-2025
```

### 2. Backend Setup

```bash
cd backend

# Install uv if not already installed
# curl -LsSf https://astral.sh/uv/install.sh | sh  # macOS/Linux
# pip install uv  # Windows

# Install dependencies
uv sync

# Create environment file
cp .env.example .env.local

# Edit .env.local and add your API keys:
# DEEPGRAM_API_KEY=your_deepgram_key
# MURF_API_KEY=your_murf_api_key
# GOOGLE_API_KEY=your_google_gemini_key

# Download required models (optional)
uv run python src/agent.py download-files
```

### 3. Frontend Setup

```bash
cd ../frontend

# Install dependencies
pnpm install
# or: npm install

# Create environment file
cp .env.example .env.local

# Edit .env.local:
# LIVEKIT_URL=ws://127.0.0.1:7880
```

### 4. Start Services

**Option A: All services at once (Unix/macOS)**
```bash
chmod +x start_app.sh
./start_app.sh
```

**Option B: Individual terminals (Windows/Unix)**

```bash
# Terminal 1: LiveKit Server
livekit-server --dev

# Terminal 2: Backend Agent
cd backend
uv run python src/agent.py dev

# Terminal 3: Frontend
cd frontend
pnpm dev
```

### 5. Test Your Agent

1. Open **http://localhost:3000** in your browser
2. Grant **microphone permissions** when prompted
3. Start speaking: *"Hello, can you hear me?"*
4. Watch the magic happen! ✨

## 📚 Complete Documentation

| Document | Description | Use Case |
|----------|-------------|----------|
| [START_HERE.md](docs/START_HERE.md) | Beginner-friendly setup guide | First-time users |
| [SETUP_GUIDE.md](docs/SETUP_GUIDE.md) | Comprehensive installation | Detailed configuration |
| [QUICK_START.md](docs/QUICK_START.md) | Rapid deployment | Get running fast |
| [TESTING_INSTRUCTIONS.md](docs/TESTING_INSTRUCTIONS.md) | Testing procedures | Validate your setup |
| [PIPELINE_ANALYSIS.md](docs/PIPELINE_ANALYSIS.md) | Performance metrics | Optimization insights |
| [DAY_1_README.md](docs/DAY_1_README.md) | Day 1 journey | Challenge completion |
| [PROJECT_ORGANIZATION.md](docs/PROJECT_ORGANIZATION.md) | Repo structure | Understanding layout |

## 🔧 Key Features & Modifications

### ✅ Day 1 Implementations

- **Complete voice agent setup** with LiveKit, Deepgram, Gemini, Murf
- **Real-time audio processing** with Silero VAD and turn detection
- **Production-ready configuration** with comprehensive .gitignore
- **Organized documentation** in dedicated docs/ folder
- **Local development optimizations**:
  - BVC (Background Voice Cancellation) disabled (lines 127-132 in `agent.py`)
  - BVC requires LiveKit Cloud; removed for local compatibility
  - All other pipeline features intact

### 🎨 Frontend Features

- Real-time voice interaction with LiveKit
- Audio visualization and level monitoring
- Light/dark theme switching
- Mobile-responsive design
- Chat transcript view

### 🧠 Backend Features

- Multi-modal agent framework (voice + optional video)
- Configurable LLM providers (Gemini, OpenAI, Anthropic)
- Multiple STT options (Deepgram, Groq)
- Murf Falcon TTS integration (fastest in class!)
- Comprehensive metrics and logging
- Production Docker support

## 📈 Performance Metrics

Based on local testing with Day 1 setup:

| Component | Latency | Notes |
|-----------|---------|-------|
| **Speech-to-Text** | 80-250ms | Deepgram Nova-3 |
| **LLM Processing** | 100-500ms | Gemini 2.5 Flash |
| **Text-to-Speech** | 50-150ms | Murf Falcon ⚡ |
| **Audio Pipeline** | ~50ms | VAD + processing |
| **Total Latency** | 350-1250ms | End-to-end response |

**Key Insight**: Murf Falcon delivers consistently fast TTS, making it ideal for real-time voice interactions!

See [PIPELINE_ANALYSIS.md](docs/PIPELINE_ANALYSIS.md) for detailed breakdown.

## 🛠️ Troubleshooting

### Backend won't connect to LiveKit
```bash
# Ensure LiveKit server is running
livekit-server --dev

# Check it's on the correct port
netstat -an | grep 7880  # Unix/macOS
netstat -an | findstr 7880  # Windows
```

### Agent not listening to microphone
1. Check browser microphone permissions
2. Verify Deepgram API key in `backend/.env.local`
3. Check backend logs for "STT transcript:" messages

### Python import errors
```bash
cd backend
# Clear cache
rm -rf __pycache__ src/__pycache__  # Unix/macOS
# Windows PowerShell:
# Get-ChildItem -Recurse -Directory -Filter "__pycache__" | Remove-Item -Recurse -Force

# Reinstall dependencies
uv sync --refresh
```

### Frontend hydration warnings
If you see warnings about `cz-shortcut-listen="true"`:
- These are **cosmetic only** from browser extensions (e.g., ColorZilla)
- They don't affect functionality
- Safe to ignore

## 🔗 Resources & Documentation

### Official Docs
- [Murf Falcon TTS API](https://murf.ai/api/docs/text-to-speech/streaming)
- [LiveKit Agents Documentation](https://docs.livekit.io/agents)
- [Deepgram API Docs](https://developers.deepgram.com/)
- [Google Gemini API](https://ai.google.dev/gemini-api/docs)

### Original Templates
- [LiveKit Python Agent Starter](https://github.com/livekit-examples/agent-starter-python)
- [LiveKit React Frontend Starter](https://github.com/livekit-examples/agent-starter-react)
- [Challenge Repository](https://github.com/murf-ai/ten-days-of-voice-agents-2025)

### Community
- [LiveKit Community Slack](https://livekit.io/join-slack)
- [Murf Discord](https://murf.ai/discord)

## 🧪 Testing

Run the comprehensive test suite:

```bash
cd backend
uv run pytest
```

Learn more: [LiveKit Agent Testing Documentation](https://docs.livekit.io/agents/build/testing/)

## 📄 License

This project builds upon MIT-licensed templates:
- Backend: [Apache 2.0](backend/LICENSE)
- Frontend: [Apache 2.0](frontend/LICENSE)

See individual LICENSE files for details.

## 🙏 Acknowledgments

- **Murf AI** for organizing this amazing challenge and building Falcon TTS
- **LiveKit** for the powerful voice agent framework
- **Deepgram** for high-quality speech recognition
- **Google** for Gemini 2.5 Flash LLM
- Original repository: [murf-ai/ten-days-of-voice-agents-2025](https://github.com/murf-ai/ten-days-of-voice-agents-2025)

## 🎯 What's Next?

Stay tuned for **Day 2-10 challenges**! Each day will add new capabilities:
- Custom personas and conversation styles
- External API integrations
- Domain-specific agents (customer service, tutoring, etc.)
- Performance optimizations
- Multi-modal interactions

## 📱 Share Your Progress

Completed Day 1? Share your achievement:

```
✅ Completed Day 1 of #10DaysofAIVoiceAgents Challenge!

Built a real-time voice agent using:
🎙️ LiveKit Agents
🧠 Google Gemini 2.5 Flash
🗣️ Deepgram Nova-3
⚡ Murf Falcon TTS (50-150ms latency!)

GitHub: https://github.com/dayanandXdarpan/murf_ai_ten-days-of-voice-agents-2025

@Murf AI #MurfAIVoiceAgentsChallenge
```

---

**Author**: [@dayanandXdarpan](https://github.com/dayanandXdarpan)  
**Challenge**: #10DaysofAIVoiceAgents by Murf AI  
**Day 1 Completed**: November 23, 2025  
**Repository**: https://github.com/dayanandXdarpan/murf_ai_ten-days-of-voice-agents-2025

Let's build amazing voice AI agents together! 🚀
