# Voice Agent Setup Guide - Day 1

## ✅ Completed Setup Steps

1. ✅ Repository cloned successfully
2. ✅ Python dependencies installed (uv sync)
3. ✅ Frontend dependencies installed (pnpm install)
4. ✅ Environment files created (.env.local)
5. ✅ LiveKit server installed
6. ✅ Local development credentials configured

## 🔑 Required API Keys

You need to obtain the following API keys to run the voice agent with full functionality:

### 1. **Murf Falcon TTS API Key** (Required for text-to-speech)
- Sign up at: https://murf.ai/api
- Get your API key from the dashboard
- Add to: `backend/.env.local` as `MURF_API_KEY=your_key_here`

### 2. **Google Gemini API Key** (Required for LLM responses)
- Get free API key at: https://aistudio.google.com/app/apikey
- Add to: `backend/.env.local` as `GOOGLE_API_KEY=your_key_here`

### 3. **Deepgram API Key** (Required for speech-to-text)
- Sign up at: https://console.deepgram.com/signup
- Get your API key from the dashboard
- Add to: `backend/.env.local` as `DEEPGRAM_API_KEY=your_key_here`

## 🚀 Running the Voice Agent

### Option 1: Quick Start (All Services Together)

Open **3 separate terminal windows** and run:

**Terminal 1 - LiveKit Server:**
```powershell
$env:Path = "$env:USERPROFILE\.livekit;$env:Path"
livekit-server --dev
```

**Terminal 2 - Backend Agent:**
```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\backend
uv run python src/agent.py dev
```

**Terminal 3 - Frontend:**
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\frontend
pnpm dev
```

### Option 2: Using the Convenience Script (Linux/Mac)

If you're on Linux/Mac, you can use:
```bash
chmod +x start_app.sh
./start_app.sh
```

## 🌐 Access Your Voice Agent

Once all three services are running:

1. Open your browser and go to: **http://localhost:3000**
2. Allow microphone access when prompted
3. Start talking to your voice agent!

## 📋 Before First Run - Download Models

Before running the backend for the first time, download required models:

```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\backend
uv run python src/agent.py download-files
```

## 🎯 Day 1 Task Checklist

- [ ] Get API keys (Murf, Google Gemini, Deepgram)
- [ ] Add API keys to `backend/.env.local`
- [ ] Download required models (`uv run python src/agent.py download-files`)
- [ ] Start all 3 services (LiveKit, Backend, Frontend)
- [ ] Open http://localhost:3000 in browser
- [ ] Have a conversation with your voice agent
- [ ] Record a short video of your session
- [ ] Post on LinkedIn with hashtags: #MurfAIVoiceAgentsChallenge #10DaysofAIVoiceAgents
- [ ] Tag Murf AI and mention you're using the fastest TTS API - Murf Falcon

## 🔧 Troubleshooting

### Port Already in Use
If port 3000 or 7880 is already in use, you can:
- Stop other services using those ports
- Or modify the ports in the configuration files

### LiveKit Server Not Found
Make sure to add LiveKit to your PATH:
```powershell
$env:Path = "$env:USERPROFILE\.livekit;$env:Path"
```

### UV Command Not Found
Add uv to your PATH:
```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
```

## 📚 Useful Resources

- [Murf Falcon TTS Documentation](https://murf.ai/api/docs/text-to-speech/streaming)
- [LiveKit Agents Documentation](https://docs.livekit.io/agents)
- [Backend README](./backend/README.md)
- [Frontend README](./frontend/README.md)

## 🎉 Ready to Build!

Once you complete Day 1, you'll have:
- A working voice agent running locally
- Experience with Murf Falcon TTS
- Understanding of LiveKit architecture
- Foundation for the next 9 days of challenges

Good luck! 🚀
