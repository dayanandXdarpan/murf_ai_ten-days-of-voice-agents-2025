# 🎯 Day 1: Get Your Starter Voice Agent Running

## ✅ What's Already Done

Your development environment is fully set up:

- ✅ Repository cloned
- ✅ Python 3.11.4 detected
- ✅ Node.js v22.14.0 detected
- ✅ `uv` package manager installed
- ✅ `pnpm` package manager installed
- ✅ LiveKit server installed
- ✅ Backend dependencies installed (127 packages)
- ✅ Frontend dependencies installed (418 packages)
- ✅ Environment files created (`.env.local`)
- ✅ Local development credentials configured

## 🔑 Next Step: Get Your API Keys

You need 3 free API keys to run the voice agent:

### 1. **Google Gemini API Key** (for AI responses)
- 🔗 Get it here: https://aistudio.google.com/app/apikey
- Click "Create API Key"
- Copy the key

### 2. **Murf Falcon API Key** (for ultra-fast text-to-speech)
- 🔗 Get it here: https://murf.ai/api
- Sign up for an account
- Navigate to API dashboard
- Copy your API key

### 3. **Deepgram API Key** (for speech-to-text)
- 🔗 Get it here: https://console.deepgram.com/signup
- Create account
- Go to API Keys
- Copy your key

## 📝 Configure Your API Keys

Edit `backend\.env.local` and add your keys:

```env
LIVEKIT_URL=ws://127.0.0.1:7880
LIVEKIT_API_KEY=devkey
LIVEKIT_API_SECRET=secret
GOOGLE_API_KEY=your_google_gemini_key_here
MURF_API_KEY=your_murf_falcon_key_here
DEEPGRAM_API_KEY=your_deepgram_key_here
```

**Replace** `your_*_key_here` with your actual API keys!

## 🚀 Start Your Voice Agent

I've created 3 convenient PowerShell scripts for you. Open **3 separate PowerShell terminals** and run:

### Terminal 1: Start LiveKit Server
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-livekit.ps1
```

### Terminal 2: Start Backend Agent
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-backend.ps1
```
*Note: This will check if your API keys are configured!*

### Terminal 3: Start Frontend
```powershell
cd c:\Users\deepa\Desktop\murf-ai\ten-days-of-voice-agents-2025
.\start-frontend.ps1
```

## 🌐 Test Your Voice Agent

1. **Open your browser**: http://localhost:3000
2. **Allow microphone access** when prompted
3. **Click to connect** and start talking!
4. **Say something** like "Hello! Can you tell me about yourself?"

## 📹 Complete Day 1 Challenge

### Your Task:
1. ✅ Get the voice agent running (all 3 services)
2. 🎤 Have a conversation with your agent
3. 📹 Record a short video (30-60 seconds) of your session
4. 📱 Post on LinkedIn

### LinkedIn Post Template:

```
Just completed Day 1 of the Murf AI Voice Agents Challenge! 🎉

Built my first voice agent using:
✨ Murf Falcon - The fastest TTS API
🤖 LiveKit Agents framework
🧠 Google Gemini for AI responses

The setup was smooth, and the voice quality is incredible! 
Can't wait to see what we build in the next 9 days.

#MurfAIVoiceAgentsChallenge #10DaysofAIVoiceAgents #AI #VoiceAI

[Tag: @Murf AI]
[Attach your video]
```

## 🔧 Troubleshooting

### PowerShell Script Execution Policy
If you get an error about script execution, run:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### API Keys Not Working?
- Make sure there are no spaces before or after the `=` sign
- Make sure you copied the entire key
- Check that you saved the `backend\.env.local` file

### Port Already in Use?
- Check if another application is using port 3000 or 7880
- Stop other services and try again

### Services Not Starting?
- Make sure you added your API keys to `backend\.env.local`
- Run each terminal command from the project root directory
- Check that all 3 services start without errors

## 📊 What You've Accomplished

🎉 **Congratulations!** You've:
- Set up a complete voice AI development environment
- Learned about LiveKit architecture
- Integrated Murf Falcon TTS (fastest in the market!)
- Built your first working voice agent

## 📚 Resources

- [Murf Falcon TTS Docs](https://murf.ai/api/docs/text-to-speech/streaming)
- [LiveKit Agents Docs](https://docs.livekit.io/agents)
- [Backend README](./backend/README.md)
- [Frontend README](./frontend/README.md)
- [Quick Start Guide](./QUICK_START.md)
- [Detailed Setup Guide](./SETUP_GUIDE.md)

## 🎯 Next Steps

After completing Day 1:
1. Share your success on LinkedIn
2. Join the community discussions
3. Get ready for Day 2 challenges
4. Experiment with different conversation topics

---

**Need help?** Check the troubleshooting section or reach out to the community!

**Ready for more?** Stay tuned for Day 2 challenges! 🚀
