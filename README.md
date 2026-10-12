# 🎭 CallCeleb — Talk to Celebrity Voice Clones in Real-Time

<p align="center">
  <b>Real-time voice conversations with AI-powered celebrity clones</b><br>
  <i>1-2 second latency • 95% voice similarity • Works on any device</i>
</p>

<p align="center">
  <a href="https://callceleb.online/ru/">🚀 Try it FREE →</a>
</p>

---

## What is this?

Pick a celebrity. Click call. **Talk to them live.**

They respond with their **actual cloned voice** — not generic TTS. Real conversation, like a phone call.

**Available celebrities:**
| 🇷🇺 Russian | 🇺🇸 English |
|------------|-------------|
| Vladimir Putin | Donald Trump |
| Alexei Navalny | Jordan Peterson |
| Garik Kharlamov | Alan Watts |
| Demis Karibidis | JFK, Nixon, Reagan |

---

## ⚡ Performance

| Metric | Value |
|--------|-------|
| **End-to-end latency** | 1-2 seconds |
| **Voice similarity** | ~95% |
| **Concurrent users** | 50+ per region |

---

## 🏗 Architecture

```
User Device (WebRTC + WebSocket)
              │
              ▼
┌─────────────────────────────────┐
│     GATEWAY (Load Balancer)     │
│  • Celebrity-aware routing      │
│  • Health monitoring            │
└───────────────┬─────────────────┘
                │
    ┌───────────┼───────────┐
    ▼           ▼           ▼
┌───────┐  ┌───────┐  ┌───────┐
│Worker │  │Worker │  │Worker │
│US-1   │  │US-2   │  │EU     │
├───────┤  ├───────┤  ├───────┤
│Whisper│  │Whisper│  │Whisper│
│Gemini │  │Gemini │  │Gemini │
│CosyTTS│  │CosyTTS│  │CosyTTS│
└───────┘  └───────┘  └───────┘
 Putin      Putin      Garik
 Navalny    Navalny    Karibidis
```

---

## 🎯 Latency Breakdown

```
User stops speaking
    → 50ms  VAD detects silence
    → 200ms Whisper transcribes  
    → 800ms LLM first sentence (streaming)
    → 400ms TTS first audio chunk
    ─────────────────────────────
    ~1500ms total
```

---

## 🔧 Tech Stack

| Component | Technology |
|-----------|------------|
| ASR | Whisper (faster-whisper) |
| LLM | Gemini 3.8 Flash |
| TTS | CosyVoice / VoxCPM (custom fine-tuned) |
| Transport | WebRTC + WebSocket |
| Infra | AWS Spot g5.xlarge |

---

## 💰 Cost

~$0.02 per minute of conversation

Running on $10K AWS credits.

---

## 💡 The Story

Solo dev. Couldn't code 12 months ago.

Started with ChatGPT — disaster. Switched to Claude — magic.

Now strangers talk to AI Putin about coffee. ☕

---

## 🚀 Try It

**[callceleb.online/ru/](https://callceleb.online/ru/)**

No registration. No payment. Just click and talk.

---

## 📬 Contact

**Licensing / Investment / Collaboration:**

maks.karasev.2020@gmail.com

---

<p align="center"><b>Built with mass amounts of Claude tokens</b></p>
