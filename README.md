# 🧠 Efoyta Therapy — AI-Powered Mental Health Guide

> An intelligent, AI-assisted mental health therapy platform that delivers personalized advice, empathetic conversations, and voice-enabled interactions — built with **Streamlit** and **OpenAI GPT-4**.

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration](#-configuration)
- [Application Workflow](#-application-workflow)
- [Module Documentation](#-module-documentation)
- [Contributing](#-contributing)
- [License](#-license)
- [Developer](#-developer)

---

## 🌟 Overview

**Efoyta Therapy** is a web-based mental health support application that combines the power of OpenAI's GPT-4 language model with an intuitive Streamlit interface. The platform guides users through a personalized questionnaire to understand their mental health needs, then provides AI-generated therapeutic advice, real-time chat support, and text-to-speech audio responses.

The application is designed to offer:

- **Empathetic, AI-driven support** tailored to individual user profiles
- **Voice input/output** capabilities for accessible, hands-free interaction
- **Privacy-first design** with explicit user consent before data processing
- **Personalized recommendations** based on age, gender, health status, and user-described concerns

---

## ✨ Features

| Feature                          | Description                                                                 |
| -------------------------------- | --------------------------------------------------------------------------- |
| 🏠 **Welcome Dashboard**        | Informational landing page with cards highlighting key services             |
| 📝 **Multi-Step Questionnaire** | Guided profile builder collecting personal info, health status, and needs   |
| 🎤 **Voice Input (STT)**        | Record audio to describe symptoms — transcribed via OpenAI Whisper          |
| 💬 **AI Chat Assistant**        | Real-time conversational chatbot powered by GPT-4 Turbo                    |
| 🔊 **Text-to-Speech (TTS)**     | AI responses are automatically converted to audio using OpenAI TTS          |
| 🗺️ **Clinic Finder**           | Interactive PyDeck map displaying nearby mental health clinics              |
| 🔒 **Privacy & Consent**        | Explicit consent collection before any data is used for personalization     |
| 📊 **Feedback System**          | In-app feedback collection to continuously improve advice quality           |

---

## 🛠️ Tech Stack

| Technology              | Purpose                                      |
| ----------------------- | -------------------------------------------- |
| **Python 3.8+**         | Core programming language                    |
| **Streamlit**           | Web application framework & UI               |
| **OpenAI API (GPT-4)**  | AI-powered chat, advice generation           |
| **OpenAI Whisper**      | Speech-to-text transcription                 |
| **OpenAI TTS**          | Text-to-speech audio generation              |
| **Streamlit Card**      | Custom card UI components                    |
| **Streamlit AudioRec**  | In-browser audio recording                   |
| **Pandas**              | Data manipulation for clinic data            |
| **PyDeck**              | Interactive 3D map visualization             |

---

## 📁 Project Structure

```
AI-Mental-Health-Guide-App/
│
├── app.py              # Main application entry point & page routing
├── assistant.py        # OpenAI API integration (chat, TTS, STT)
├── questions.py        # Multi-step questionnaire & user data collection
├── response.py         # Personalized advice display & chat interface
├── clinics.py          # Clinic finder with interactive map
├── figma.py            # UI prototype components & card layouts
├── style.css           # Custom CSS for sidebar button styling
├── requirements.txt    # Python dependencies
├── audio.mp3           # Generated TTS audio output file
│
└── asset/              # Static assets
    ├── petal_cover.png      # Welcome page cover image
    ├── petal-logo-w.png     # Sidebar logo (white variant)
    ├── petal-logo.png       # Standard logo
    ├── mental.png           # Mental health icon
    └── Inclusive SH.jpeg    # Inclusive health imagery
```

---

## 📌 Prerequisites

Before running the application, ensure you have:

1. **Python 3.8 or higher** installed on your system
2. An **OpenAI API key** with access to:
   - GPT-4 Turbo (chat completions)
   - Whisper (audio transcription)
   - TTS (text-to-speech)
3. **pip** (Python package manager)

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/AI-Mental-Health-Guide-App.git
cd AI-Mental-Health-Guide-App
```

### 2. Create a Virtual Environment (Recommended)

```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

The `requirements.txt` includes:

```
openai>=1.2
streamlit-feedback
streamlit-extras
streamlit-card
streamlit-audiorec
pandas
pydeck
```

> **Note:** `streamlit` is installed automatically as a dependency of the Streamlit extension packages.

---

## ▶️ Usage

### Run the Application

```bash
streamlit run app.py
```

The app will launch in your default browser at `http://localhost:8501`.

### Enter Your API Key

1. In the sidebar, paste your **OpenAI API key** into the input field
2. If you don't have one, click the provided link: [Get an OpenAI API Key](https://platform.openai.com/account/api-keys)

---

## ⚙️ Configuration

| Setting           | Location       | Description                                      |
| ----------------- | -------------- | ------------------------------------------------ |
| Page Title        | `app.py`       | Set to `"Efoyta Therapy"` via `st.set_page_config()` |
| OpenAI Model      | `assistant.py` | Uses `gpt-4-turbo` for chat and `gpt-4o-mini` for assistants |
| TTS Voice         | `response.py`  | Set to `"nova"` — can be changed to `alloy`, `echo`, `fable`, `onyx`, or `shimmer` |
| Whisper Model     | `assistant.py` | Uses `whisper-1` for speech-to-text              |
| Layout            | `app.py`       | Wide layout enabled via `layout="wide"`          |

---

## 🔄 Application Workflow

```
┌─────────────────┐
│   Welcome Page   │  ← Landing page with service overview cards
└────────┬────────┘
         │ "Get Started"
         ▼
┌─────────────────┐
│  Questionnaire   │  ← Multi-step form (5 pages):
│                  │     1. Voice/text needs description
│                  │     2. Personal info (age, gender)
│                  │     3. Health status & symptoms
│                  │     4. Additional lifestyle info
│                  │     5. Privacy consent
└────────┬────────┘
         │ "Finish" (with consent)
         ▼
┌─────────────────┐
│ Personalized AI  │  ← GPT-4 generates tailored advice
│   Advice Chat    │  ← Response is read aloud via TTS
│                  │  ← Ongoing chat for follow-up questions
└─────────────────┘
```

---

## 📖 Module Documentation

### `app.py` — Main Application

The entry point of the application. Handles:

- **Page configuration** — Sets the page title, icon, layout, and meta info
- **Sidebar navigation** — Renders navigation buttons (Home, Profile, Personalized Advice, Help) and the API key input
- **Page routing** — Uses `st.session_state['current_page']` to route between `welcome`, `questions`, `chat`, and `clinics` views
- **Welcome page** — Displays a cover image and three informational cards (Mental Health Education, Shared Decision-Making, Personalized Recommendations)

### `assistant.py` — OpenAI Integration (`PetalAssitant` class)

Core AI functionality wrapper around the OpenAI API:

- **`create_openai_assistant_prompt(user_data)`** — Constructs a detailed prompt from the user's profile data (age, gender, health status, description)
- **`generate_response(user_data, api_key)`** — Sends the constructed prompt to GPT-4 Turbo and returns personalized mental health advice
- **`chat(messages)`** — Handles multi-turn conversation by passing the full message history to the model
- **`text_to_speech(text, voice)`** — Converts text to speech using OpenAI's TTS-1 model and saves to `audio.mp3`
- **`transcribe(audio_path)`** — Transcribes audio recordings to text using OpenAI Whisper

### `questions.py` — Questionnaire System

A multi-page questionnaire flow with progress tracking:

- **`collect_user_needs()`** — Audio recording for the user to describe their needs, with Whisper-based transcription
- **`collect_personal_info()`** — Collects age and gender identity
- **`collect_health_status()`** — Captures overall health rating and symptom descriptions
- **`collect_other_info()`** — Free-text input for lifestyle, mental health, and economic factors
- **`privacy_concent()`** — Collects explicit user consent before processing data
- **`compile_user_data()`** — Aggregates all session state data into a structured dictionary for AI processing
- **`navigate()`** — Handles page-to-page navigation with Back/Next buttons

### `response.py` — Personalized Advice & Chat

Manages the AI response display and interactive chat:

- **`display_response()`** — Generates personalized advice using the user's profile, plays it as audio, and initiates an ongoing chat session
- **`autoplay_audio(file_path)`** — Embeds and auto-plays the generated MP3 audio in the browser
- **`save_feedback(user_data, feedback)`** — Placeholder for persisting user feedback (extensible to database integration)

### `clinics.py` — Clinic Finder

Interactive map-based clinic locator:

- Displays nearby clinics on a **PyDeck** interactive map with labeled markers
- Shows clinic names, coordinates, and services offered via tooltips
- Currently uses sample clinic data (extensible to live API integration)

### `figma.py` — UI Prototype Components

Contains alternative UI layout prototypes:

- **`figma_welcome()`** — An alternate welcome page layout with a "MOJO Plan" theme
- **`figma_profile()`** — A stepped card-based profile builder UI with audio recording support
- **`create_card()`** — Reusable card component with custom styling (shadows, borders, rounded corners)

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature-name`
3. **Commit** your changes: `git commit -m "Add your feature"`
4. **Push** to the branch: `git push origin feature/your-feature-name`
5. **Open** a Pull Request

### Development Guidelines

- Follow **PEP 8** coding standards for Python
- Add docstrings to all new functions and classes
- Test your changes locally with `streamlit run app.py` before submitting
- Update this README if you add new features or modify the project structure

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 👩‍💻 Developer

**Bezawit Hayalu**

---

> *Built with ❤️ using Streamlit & OpenAI — empowering mental health support through AI.*
