# 🚀 Quick Start - Day 1 Voice Agent

## Step 1: Get Your API Keys (5-10 minutes)

Open these links in your browser and sign up for free API keys:

1. **Murf Falcon TTS**: https://murf.ai/api
   - Sign up for an account
   - Navigate to API section
   - Copy your API key

2. **Google Gemini**: https://aistudio.google.com/app/apikey
   - Click "Create API Key"
   - Copy the generated key

3. **Deepgram STT**: https://console.deepgram.com/signup
   - Create account
   - Go to API Keys section
   - Copy your API key

## Step 2: Add API Keys to Configuration

Edit `backend/.env.local` and add your keys:

```env
LIVEKIT_URL=ws://127.0.0.1:7880
LIVEKIT_API_KEY=devkey
LIVEKIT_API_SECRET=secret
GOOGLE_API_KEY=your_google_key_here
MURF_API_KEY=your_murf_key_here
DEEPGRAM_API_KEY=your_deepgram_key_here
```

## Step 3: Download Models

Open PowerShell and run:

```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\backend
uv run python src/agent.py download-files
```

## Step 4: Start the Voice Agent

Open **3 PowerShell terminals** and run these commands:

### Terminal 1 - LiveKit Server
```powershell
$env:Path = "$env:USERPROFILE\.livekit;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
livekit-server --dev
```

### Terminal 2 - Backend Agent
```powershell
$env:Path = "C:\Users\deepa\.local\bin;$env:Path"
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\backend
uv run python src/agent.py dev
```

### Terminal 3 - Frontend
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025\frontend
pnpm dev
```

## Step 5: Test Your Voice Agent

1. Open browser: **http://localhost:3000**
2. Allow microphone access
3. Click to start conversation
4. Say "Hello!" and test the agent

## Step 6: Complete Day 1 Challenge

1. ✅ Have a conversation with your agent
2. 📹 Record a short video of your session
3. 📱 Post on LinkedIn with:
   - Video of your agent in action
   - Description: "Just completed Day 1 of the Murf AI Voice Agents Challenge! Built my first voice agent using the fastest TTS API - Murf Falcon. #MurfAIVoiceAgentsChallenge #10DaysofAIVoiceAgents"
   - Tag: @Murf AI

## 🎉 You're Done!

Congratulations on completing Day 1! You now have a fully functional voice agent running locally.

---

## 🆘 Need Help?

- **Port in use?** Change ports in the config files
- **Commands not found?** Run the PATH export commands in each terminal
- **No audio?** Check browser permissions for microphone access
- **Agent not responding?** Verify all 3 services are running

## 📝 Quick Commands Reference

```powershell
# Add tools to PATH (run in each new terminal)
$env:Path = "C:\Users\deepa\.local\bin;$env:USERPROFILE\.livekit;$env:Path"

# Navigate to project
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025

# Check service status
# LiveKit: http://localhost:7880
# Frontend: http://localhost:3000
```
