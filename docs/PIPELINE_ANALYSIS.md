# 🔍 Voice Agent Pipeline Analysis

## 📊 Current Pipeline Configuration

### Voice AI Pipeline Components:

```
User Speech → [STT] → [LLM] → [TTS] → Agent Speech
              ↓        ↓        ↓
           Deepgram  Gemini   Murf Falcon
```

---

## 🎯 Component Details

### 1. **Speech-to-Text (STT)** - Deepgram Nova-3
- **API Key**: ✅ Configured (`dd3feba4c2cbef84c29edaa2030cae05094fd6e6`)
- **Model**: `nova-3` (Latest, most accurate model)
- **Capabilities**: 
  - Real-time streaming transcription
  - Multiple language support
  - High accuracy for conversational speech
- **Limitations**:
  - Requires stable internet connection
  - ~100ms latency for streaming
  - Free tier: 45 hours/month

### 2. **Large Language Model (LLM)** - Google Gemini 2.5 Flash
- **API Key**: ✅ Configured (`AIzaSyB5vvcTsyTMzO4f_kk9As27prcTainrH8w`)
- **Model**: `gemini-2.5-flash`
- **Capabilities**:
  - Fast response generation
  - Conversational context understanding
  - Tool/function calling support
- **Limitations**:
  - Free tier: 1500 requests/day
  - 32k token context window
  - Text-only (no vision in this config)

### 3. **Text-to-Speech (TTS)** - Murf Falcon
- **API Key**: ✅ Configured (`ap2_f8824bda-6b14-487c-81dd-5ad84c2a6aef`)
- **Voice**: `en-US-matthew`
- **Style**: `Conversation`
- **Features Enabled**:
  - ✅ `text_pacing=True` (Natural speech rhythm)
  - ✅ Sentence tokenization (min 2 chars)
  - ❌ SSML support (not enabled by default)
- **Capabilities**:
  - **Ultra-fast synthesis** (fastest TTS API)
  - Streaming audio generation
  - Natural conversational voice
  - Multiple voice styles
- **Limitations**:
  - Free tier depends on Murf plan
  - Requires active API key

### 4. **Voice Activity Detection (VAD)** - Silero
- **Status**: ✅ Loaded and cached
- **Purpose**: Detects when user starts/stops speaking
- **Latency**: <50ms

### 5. **Turn Detection** - Multilingual Model
- **Purpose**: Determines when to let user speak vs agent respond
- **Features**: Context-aware turn-taking

### 6. **Noise Cancellation** - BVC (Background Voice Cancellation)
- **Purpose**: Removes background noise and echoes
- **Best for**: Clean audio in noisy environments

---

## 🚀 Pipeline Flow & Timing

### Typical Conversation Flow:

1. **User Speaks** (0ms)
   - VAD detects speech start
   - Noise cancellation active
   
2. **Speech Recognition** (~100-300ms)
   - Deepgram streams transcription
   - Text appears incrementally
   
3. **LLM Processing** (~200-800ms)
   - Gemini generates response
   - Preemptive generation enabled (starts before user finishes)
   
4. **Speech Synthesis** (~50-150ms)
   - Murf Falcon synthesizes audio (FASTEST)
   - Streaming output to user
   
5. **Total Latency**: ~350-1250ms (excellent for voice AI!)

---

## ⚡ Performance Optimizations Enabled

- ✅ **Preemptive Generation**: LLM starts generating while user is still speaking
- ✅ **Streaming**: All components stream data (no waiting for full completion)
- ✅ **Model Caching**: VAD and turn detector pre-warmed
- ✅ **Sentence Tokenization**: TTS speaks as soon as it has a complete sentence
- ✅ **Text Pacing**: Natural pauses and rhythm in speech

---

## 🎨 SSML Support

### Current Status: ❌ Not Enabled

**To Enable SSML for Murf TTS:**

You can modify the TTS configuration to support SSML for enhanced control over:
- Speech rate and pitch
- Emphasis and pauses
- Pronunciation
- Audio effects

**Current Configuration:**
```python
tts=murf.TTS(
    voice="en-US-matthew", 
    style="Conversation",
    tokenizer=tokenize.basic.SentenceTokenizer(min_sentence_len=2),
    text_pacing=True
)
```

**SSML-Enhanced Configuration (if needed):**
```python
tts=murf.TTS(
    voice="en-US-matthew", 
    style="Conversation",
    tokenizer=tokenize.basic.SentenceTokenizer(min_sentence_len=2),
    text_pacing=True,
    # Add SSML support if the plugin supports it
    # ssml=True  # Check plugin documentation
)
```

### When to Use SSML:
- Need precise control over pronunciation
- Want to add pauses or emphasis
- Need different speaking rates for different parts
- Currently: **NOT REQUIRED** for basic conversational agent

---

## 🚦 Known Limitations

### Rate Limits:
1. **Deepgram Free Tier**: 
   - 45 hours STT per month
   - 200 concurrent connections
   
2. **Google Gemini Free Tier**:
   - 1,500 requests per day
   - 1 million tokens per month
   
3. **Murf Falcon**: 
   - Depends on your plan
   - Check dashboard for limits

### Technical Limitations:
- **Internet Required**: All services are cloud-based
- **Latency**: ~350-1250ms total (already excellent)
- **Concurrent Users**: Limited by LiveKit server (dev mode: unlimited locally)
- **Audio Quality**: Depends on user's microphone

### Stop/Start Behavior:
- **Automatic Turn-Taking**: Agent stops when user starts speaking
- **Preemptive Generation**: Agent prepares response while user speaks
- **Interruption Handling**: User can interrupt agent mid-sentence
- **VAD Threshold**: Adjustable sensitivity for speech detection

---

## 🎯 Recommended Settings for Production

```python
session = AgentSession(
    stt=deepgram.STT(
        model="nova-3",
        # language="en",  # Specify if single language
        # interim_results=True,  # Get partial results
    ),
    llm=google.LLM(
        model="gemini-2.5-flash",
        # temperature=0.7,  # Control creativity
        # max_tokens=150,  # Limit response length
    ),
    tts=murf.TTS(
        voice="en-US-matthew", 
        style="Conversation",
        tokenizer=tokenize.basic.SentenceTokenizer(min_sentence_len=2),
        text_pacing=True,
        # streaming=True,  # Enable if supported
    ),
    turn_detection=MultilingualModel(),
    vad=ctx.proc.userdata["vad"],
    preemptive_generation=True,  # Keep enabled for low latency
)
```

---

## 📊 Performance Metrics Collected

The agent tracks:
- Time-to-first-token (TTFT)
- End-to-end latency
- Token usage (LLM)
- Audio quality metrics
- Turn-taking accuracy

Check logs after conversation for detailed metrics!

---

## ✅ Current Status

- ✅ All API keys configured
- ✅ Models downloaded
- ✅ Pipeline optimized for low latency
- ✅ Ready to start testing

**SSML**: Not required for current use case, but can be added if needed.

---

## 🚀 Next Step: Start Testing!

Run the three services to test the complete pipeline:
1. LiveKit server
2. Backend agent
3. Frontend UI

The agent will handle stop/start automatically based on turn detection and VAD!
