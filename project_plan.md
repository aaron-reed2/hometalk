# 🧠 DIY Smart Home Assistant Project Plan

**Personal-use, extensible, resume-ready voice assistant**  
**Features:** Smart device control + general Q&A + per-user context

---

## 📆 1. Project Goals

Build a **modular, voice-activated home assistant** that:

- Responds to **voice commands** and **general questions**
- Controls smart devices via **Home Assistant**
- Supports **multiple users** with per-user context (voice recognition)
- Uses **OpenAI GPT** for language understanding and conversation
- Is **extensible, shareable**, and resume-worthy

---

## 🔍 2. Core Functionalities (MVP)

| Feature                         | Description |
|----------------------------------|-------------|
| Voice Input                     | Capture speech via mic (manual → always-on) |
| Speech-to-Text (STT)            | Convert audio to text |
| User Identification             | Match voice to user identity |
| GPT Assistant Logic             | Use OpenAI to:  |
|                                 |- Interpret smart commands  |
|                                 |- Respond to general questions |
| Smart Device Control            | Home Assistant + REST API |
| Text-to-Speech (TTS)            | Speak responses |
| Wake Word Listening             | Always-on passive mode via Porcupine |
| Session Memory                  | Per-user thread context with OpenAI |
| Logging                         | Store interaction history for debugging |

---

## 📃 3. Technology Stack

| Layer | Tech / Options | Notes |
|-------|----------------|-------|
| Language | **Python** | Core logic + APIs |
| STT | **OpenAI Whisper (local)**, or Google/AssemblyAI fallback | Whisper is free + high accuracy |
| Speaker Recognition | **Resemblyzer** | Embeds + matches voice to identity |
| Wake Word Detection | **Porcupine (Picovoice)** | Wake word engine, free for personal use |
| NLP | **GPT-4-turbo via OpenAI API** | Per-user context threads |
| Smart Device API | **Home Assistant** + REST | Controls smart lights/devices |
| TTS | **pyttsx3**, Coqui, or Polly/Google TTS | For spoken responses |
| Backend | **FastAPI** or Flask | Request routing, context mgmt |
| Storage | **SQLite or Redis** | Stores context mappings, history |

---

## 🌐 4. Function Modes

### A. Smart Device Control Mode

- "Turn off the hallway light."
- "Dim the living room lamp to 30%."

### B. Conversational / Q&A Mode

- "What’s the weather like today?"
- "What’s the capital of Iceland?"
- "Tell me a joke."

**GPT Routing Logic** auto-detects intent using structured prompts and optionally tags outputs:

```json
{
  "intent": "device_control",
  "action": {...},
  "text": "Turning off the hallway light."
}
```

---

## 🚀 5. Hardware Requirements

| Component | Options | Est. Cost | Notes |
|----------|---------|-----------|-------|
| Server | Use ThinkPad or MacBook Pro (headless) | $0 | Run Home Assistant + backend |
| Mic Input | USB mic / webcam / PS3 Eye | $20–50 | High-quality input improves STT |
| Speaker Output | 3.5mm or Bluetooth speaker | $0–50 | For TTS output |
| Wake Word Hardware | Same as mic input | $0 | Works with Porcupine |
| Smart Devices | Use existing bulbs/switches | $0 | Expand later |
| Optional: Raspberry Pi 4 | $60–80 | For future compact deployment ||

---

## 📊 6. Libraries, APIs, Services

| Function | Tool | Price |
|---------|------|-------|
| STT | **Whisper (local)** | Free |
| Speaker ID | **Resemblyzer** | Free |
| Wake Word | **Porcupine** | Free for personal |
| GPT | **OpenAI GPT-4-turbo** | ~$0.01/1K input, ~$0.03/1K output |
| TTS | pyttsx3 / Coqui / Polly | Free – $4/1M chars |
| Device Control | Home Assistant | Free |
| Backend | FastAPI / Flask | Free |
| DB | SQLite / Redis | Free |

---

## 📏 7. Architecture Overview

```text
[Mic Input] 
  ↓
[STT: Whisper]
  ↓
[Speaker Recognition: Resemblyzer]
  ↓
[Backend: FastAPI]
  ↓
[OpenAI GPT (per-user thread)]
     ↷           ↸
[Smart Device Intent]    [General Answer]
     ↓                      ↓
[Home Assistant API]      [TTS Response]
     ↓                      ↓
[Device Command]         [Audio Out]
```

---

## 📅 8. Development Phases & Timeline

| Phase | Description | Est. Time |
|-------|-------------|-----------|
| Phase 1 | Voice input → GPT → Text response (console) | 3–5 days |
| Phase 2 | Add TTS response output | 1–2 days |
| Phase 3 | Add Home Assistant smart device control | 4–7 days |
| Phase 4 | Add speaker recognition + per-user thread memory | 1–2 weeks |
| Phase 5 | Add wake-word listening with Porcupine | 1 week |
| Phase 6 | Polish: logging, config, GitHub cleanup | 1 week |

**Total Time Estimate:** ~5–8 weeks part-time

---

## 💸 9. Estimated Cost Breakdown

| Item | Price |
|------|-------|
| OpenAI API (GPT-4-turbo, light use) | $5–15/mo |
| Mic | $20–50 |
| Speaker | $0–50 |
| TTS (Coqui or Polly fallback) | $0–5/mo |
| Server (ThinkPad or Mac) | $0 |
| Home Assistant | Free |

**💵 Total Startup Cost:** ~$25–65  
**🔁 Monthly Recurring:** ~$5–15 (OpenAI usage)

---

## 🚀 10. Optional Expansion (Future Phases)

| Feature | Description |
|--------|-------------|
| 🏠 Multi-room awareness | Route commands by device/mic location |
| 📅 Calendar/Weather integration | Add Google Calendar + OpenWeather API |
| 🔺 Display interface | Tablet dashboard (React / Next.js frontend) |
| 🎵 Music/media control | Spotify, Plex, or YouTube playback |
| 🔐 Security alerts | Facial detection + smart camera integration |
| 🤖 Local fallback LLM | Use LLaMA/Mistral for offline GPT |
| 📦 Docker container | Make deployment + sharing easier |
