# 📧 AI-Powered Email Reply Generator

A Chrome Extension for Gmail that uses **Google Gemini API** to automatically generate context-aware, intelligent email replies — directly inside your Gmail inbox.

---

## 🚀 Features

- 🤖 **AI-Powered Replies** — Generates smart, context-aware email responses using Google Gemini API
- 🎭 **Tone Selection** — Choose from Professional, Casual, or Friendly tone
- ⚡ **One-Click Generation** — "AI Reply" button injected directly into Gmail UI
- 🔒 **Privacy First** — No data stored; all processing is real-time and stateless
- 🌐 **Seamless Gmail Integration** — Works natively at `mail.google.com`

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React.js (Vite) + Chrome Extension |
| Backend | Spring Boot (Java 17+) |
| AI Integration | Google Gemini API |
| API Communication | WebClient (REST) |
| Build Tools | Maven (backend), Vite (frontend) |
| IDEs | IntelliJ IDEA, VS Code |

---

## 🏗️ Architecture

```
User (Gmail)
    │
    ▼
Chrome Extension (React UI)
    │  POST /api/email/generate
    ▼
Spring Boot Backend
    │  WebClient
    ▼
Google Gemini API
    │
    ▼
Generated Email Reply → Displayed in Gmail
```

The system follows a clean **3-layer architecture**:
- **Controller Layer** — Handles HTTP requests (`EmailGeneratorController`)
- **Service Layer** — Business logic & Gemini API communication (`EmailGeneratorService`)
- **DTO Layer** — Data transfer between frontend and backend (`EmailRequest`)

---

## 📋 Prerequisites

- Java 17 or above
- Node.js & npm
- Google Chrome Browser
- Google Gemini API Key

### Hardware
- Minimum 4GB RAM
- Active internet connection

---

## ⚙️ Setup & Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-email-reply-generator.git
cd ai-email-reply-generator
```

### 2. Backend Setup (Spring Boot)

```bash
cd backend
```

Set your Gemini API key as an environment variable:

```bash
# Linux/macOS
export GEMINI_KEY=your_gemini_api_key_here

# Windows
set GEMINI_KEY=your_gemini_api_key_here
```

Configure `application.properties`:

```properties
spring.application.name=email-reply-generator
gemini.api.url=https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent
gemini.api.key=${GEMINI_KEY}
```

Run the backend:

```bash
./mvnw spring-boot:run
```

The backend starts at `http://localhost:8080`

### 3. Frontend Setup (React + Vite)

```bash
cd frontend
npm install
npm run dev
```

The frontend runs at `http://localhost:5173`

### 4. Load Chrome Extension

1. Open Chrome and navigate to `chrome://extensions/`
2. Enable **Developer Mode** (top right toggle)
3. Click **Load Unpacked**
4. Select the `extension/` folder from this project
5. Open Gmail — you'll see the **AI Reply** button in your compose/reply toolbar

---

## 📡 API Reference

### Generate Email Reply

**POST** `/api/email/generate`

**Request Body:**
```json
{
  "emailContent": "The email text you want to reply to",
  "tone": "professional"
}
```

**Tone Options:** `professional` | `casual` | `friendly`

**Response:**
```json
"Dear [Name], Thank you for reaching out. I wanted to follow up on..."
```

---

## 🧪 Testing

All major test cases have been validated:

| Test Case | Description | Result |
|-----------|-------------|--------|
| TC01 | Generate reply without tone | ✅ Pass |
| TC02 | Generate reply with professional tone | ✅ Pass |
| TC03 | Generate reply with casual tone | ✅ Pass |
| TC04 | Generate reply with friendly tone | ✅ Pass |
| TC05 | Empty input handling | ✅ Pass |
| TC06 | API failure / invalid key handling | ✅ Pass |

---

## 🔐 Security

- API keys are **never hardcoded** — stored via environment variables
- No user data or email content is persisted
- All communication with Gemini API is over **HTTPS**
- Proper error handling prevents sensitive info leakage

---

## 🔮 Future Scope

- 🌍 **Multi-language Support** — Generate replies in multiple languages
- 🎨 **Advanced Tone Options** — Formal, empathetic, persuasive tones
- 🧵 **Thread Awareness** — Better understanding of long email threads
- 👤 **User Personalization** — Custom writing styles per user
- 📬 **Multi-Platform Support** — Extend to Outlook and other email clients
- 🗂️ **Caching** — Store frequent responses to reduce API calls
- 🎙️ **Voice Input** — Generate replies via voice commands

---

## 📄 License

This project was developed as an academic submission. All rights reserved by the author.

---

> ⭐ If you found this project helpful, give it a star!
