# Smart Home Assistant

A DIY smart home and AI voice assistant powered by FastAPI, OpenAI's GPT-4-turbo, and Home Assistant. Supports smart device control, general conversation, and per-user voice-based context switching.

---

## Features
- Voice input using STT (Whisper or similar)
- Per-user memory with voice recognition (Resemblyzer)
- Smart device control via Home Assistant
- General Q&A and conversation using GPT
- Wake-word support (Porcupine)
- TTS audio response (optional)

---

## Project Structure
```
smart-home-assistant/
├── app/
│   └── main.py              # Main FastAPI backend
├── .env                    # Environment variables (e.g., API keys)
├── .gitignore              # Ignore .env and other sensitive files
├── requirements.txt        # Python dependencies
└── README.md               # Project info and setup
```

---

## Setup Instructions

### 1. Clone the repository
```bash
git clone https://github.com/your-username/smart-home-assistant.git
cd smart-home-assistant
```

### 2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Add your API keys in a `.env` file
Create a file named `.env` in the root directory:
```env
OPENAI_API_KEY=your-openai-api-key
```

### 5. Run the server
```bash
uvicorn app.main:app --reload
```

The server will be available at `http://localhost:8000`

---

## Environment Variables
| Variable | Description |
|----------|-------------|
| `OPENAI_API_KEY` | Your OpenAI API key |

---

## Future Features
- Whisper-based local speech-to-text
- TTS output using Coqui or pyttsx3
- Wake-word detection
- Smart scene automation
- Multi-room audio routing

---

## License
MIT License

