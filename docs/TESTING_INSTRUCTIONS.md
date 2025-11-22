# 🚀 Testing Instructions - Voice Agent is Ready!

## ✅ Setup Complete

All API keys are configured and models are downloaded:
- ✅ Deepgram API: `dd3feba4c2cbef84c29edaa2030cae05094fd6e6`
- ✅ Murf Falcon API: `ap2_f8824bda-6b14-487c-81dd-5ad84c2a6aef`
- ✅ Google Gemini API: `AIzaSyB5vvcTsyTMzO4f_kk9As27prcTainrH8w`

## 📊 Pipeline Analysis

I've created a detailed pipeline analysis in **PIPELINE_ANALYSIS.md** covering:
- ✅ All components (STT, LLM, TTS, VAD, Turn Detection)
- ✅ Latency breakdown (~350-1250ms total)
- ✅ Performance optimizations enabled
- ✅ Known limitations and rate limits
- ✅ Stop/start behavior (automatic turn-taking)
- ✅ SSML support status (not required, but can be added)

## 🎯 To Start Testing

### Option 1: Use the PowerShell Scripts (Easiest)

Open **3 separate PowerShell windows** and run:

**Window 1 - LiveKit Server:**
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-livekit.ps1
```

**Window 2 - Backend Agent:**
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-backend.ps1
```

**Window 3 - Frontend:**
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-frontend.ps1
```

### Option 2: Manual Commands

If scripts don't work, use these commands:

**Terminal 1:**
```powershell
$env:Path = "$env:USERPROFILE\.livekit;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
livekit-server --dev
```

**Terminal 2:**
```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\backend
uv run python src/agent.py dev
```

**Terminal 3:**
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\frontend
pnpm dev
```

## 🌐 Access Your Voice Agent

Once all 3 services are running:

1. **Open browser**: http://localhost:3000
2. **Allow microphone** when prompted
3. **Click "Connect"** button
4. **Start talking!**

## 🎤 Test Conversation Examples

Try these to test the pipeline:

- "Hello! Can you introduce yourself?"
- "Tell me a short joke"
- "What's the weather like today?" (will respond with general info)
- "Explain quantum computing in simple terms"
- "Count from 1 to 5"

## 🔍 What to Watch For

### ✅ Pipeline Working Correctly:
- Agent responds within 1-2 seconds
- Voice sounds natural (Murf Falcon quality)
- Turn-taking is smooth (stops when you speak)
- No echo or feedback
- Clear transcription of your speech

### ⚠️ Potential Issues:
- Long delay (>3 seconds): Check API keys
- Robotic voice: TTS issue
- Can't hear you: Check microphone permissions
- Echo: Disable noise cancellation if needed
- Agent cuts off: Adjust VAD sensitivity

## 📊 Check the Logs

While testing, monitor the backend terminal for:
- Transcription quality (Deepgram output)
- LLM token usage (Gemini)
- TTS timing (Murf Falcon speed)
- Overall latency metrics

## 🎯 Test Scenarios

### 1. Basic Conversation (2 min)
- Greet the agent
- Ask a simple question
- Have a short back-and-forth

### 2. Interruption Test (1 min)
- Let agent speak
- Interrupt mid-sentence
- See if turn-taking works

### 3. Complex Query (2 min)
- Ask for detailed explanation
- Check if response is complete
- Verify TTS quality for long responses

### 4. Speed Test (1 min)
- Ask quick questions rapidly
- Measure response time
- Check for lag

## 📹 Record Your Session

For Day 1 challenge completion:
1. ✅ Test all scenarios above
2. 📹 Record 30-60 seconds showing:
   - You speaking to the agent
   - Agent responding clearly
   - Natural conversation flow
3. 📱 Post on LinkedIn with:
   - #MurfAIVoiceAgentsChallenge
   - #10DaysofAIVoiceAgents
   - Tag @Murf AI
   - Mention "Murf Falcon - fastest TTS API"

## 🛠️ Troubleshooting Quick Fixes

**Port 3000 in use?**
```powershell
# Kill process on port 3000
Stop-Process -Id (Get-NetTCPConnection -LocalPort 3000).OwningProcess -Force
```

**Port 7880 in use?**
```powershell
# Kill process on port 7880
Stop-Process -Id (Get-NetTCPConnection -LocalPort 7880).OwningProcess -Force
```

**Services won't start?**
- Verify API keys in `backend\.env.local`
- Check no typos in keys
- Ensure PATH variables are set

## 📚 Documentation

- **PIPELINE_ANALYSIS.md** - Complete pipeline breakdown
- **START_HERE.md** - Setup overview
- **DAY_1_README.md** - Day 1 instructions
- **QUICK_START.md** - Quick reference

## ✨ Next Steps After Testing

Once everything works:
1. Experiment with different voices (check Murf docs)
2. Try different conversation styles
3. Adjust LLM parameters (temperature, etc.)
4. Add custom tools/functions
5. Prepare for Day 2 challenges!

---

## 🎉 You're Ready!

All configuration is complete. Just start the 3 services and begin testing!

**Happy building! 🚀**
