# NOVA Local Assistant

A local, privacy-focused AI companion named **NOVA** that runs entirely on your personal computer using open-source technologies.

## Prerequisites

- Node.js v16 or higher
- npm (or yarn)
- Git
- System dependencies for Vision (OpenCV, Tesseract) and audio
  - On Ubuntu/Debian: `sudo apt install libopencv-dev tesseract-ocr`
  - On macOS using Homebrew: `brew install opencv tesseract`

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/nova-local-assistant.git
   cd nova-local-assistant
   ```
2. Install Node.js dependencies:
   ```bash
   npm install
   ```

## Configuration

1. Create a `.env` file in the project root with the following variables:
   ```dotenv
   OKIBI_API_KEY=YOUR_OKIBI_API_KEY
   MODEL_API_KEY=YOUR_MODEL_API_KEY
   CHROMA_DB_DIR=./data/chroma
   WHISPER_MODEL_PATH=./models/whisper
   COQUI_TTS_MODEL_PATH=./models/coqui-tts
   ```
2. Download and place model files:
   - **Whisper**: download your preferred Whisper model (e.g., `small`) from Hugging Face into `./models/whisper`
   - **Coqui TTS**: download a Coqui TTS model from the Coqui repository into `./models/coqui-tts`
3. Ensure the `CHROMA_DB_DIR` folder exists (it will be created automatically if not).

## Running NOVA

### Development Mode

```bash
npm run dev
```

- Starts the server on port `9000` with hot-reload
- Checks for environment variables and required models

### Production Build

```bash
npm run build
npm start
```

- Compiles TypeScript into `dist/` and runs the compiled server

## Using the API

### HTTP Endpoint

Send a POST request to interact with NOVA:

```bash
curl -X POST http://localhost:9000/execute \
  -H 'Content-Type: application/json' \
  -d '{"query":"haan bhai, Nova ko bolo hello bolo"}'
```

Response:
```json
{
  "response": "haan bhai, Nova bol raha hai!",
  "executionId": "some-unique-id",
  "files": [],
  "output": null
}
```

### WebSocket (Optional)

Connect to `ws://localhost:9000` for interactive, streaming conversations and tool notifications.

## Next Steps

- Flesh out tool handlers in `src/tools/*` (Whisper inference, Coqui TTS, OpenCV routines)
- Customize system prompts or add new tools
- Grant NOVA permission for system commands when prompted

---

*Bhai, sab set hai! `.env` fill karo, models download karo, `npm run dev` karo — Nova turant online ho jayega.*

