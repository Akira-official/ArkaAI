<![CDATA[<div align="center">

![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)
![Version](https://img.shields.io/badge/Version-0.3.0_Beta-blue?style=flat-square)
![PHP](https://img.shields.io/badge/PHP-8.0+-777BB4?style=flat-square&logo=php&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Auth-FFCA28?style=flat-square&logo=firebase&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

# ✦ Arka AI

**Your Intelligent AI Companion**

[![Powered by NVIDIA](https://img.shields.io/badge/Powered%20by-NVIDIA%20NIM-76B900?style=flat-square&logo=nvidia&logoColor=white)](https://build.nvidia.com)

Arka AI is a premium, full-featured AI assistant built by **Vyoma Group**. It provides intelligent chat, image analysis, file analysis, deep reasoning, and an adaptive personality engine — all wrapped in a clean, modern interface inspired by Claude.ai and Linear.app.

🌐 **Live:** [arka.vyomagroup.online](https://arka.vyomagroup.online) · **Model:** `qwen/qwen3.5-122b-a10b` via NVIDIA NIM

</div>

---

## 📑 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [File Structure](#-file-structure)
- [SVG Icons](#-svg-icons)
- [Quick Start](#-quick-start)
- [Deployment (Hostinger)](#-deployment-hostinger)
- [Firebase Setup](#-firebase-setup)
- [Configuration Reference](#-configuration-reference)
- [localStorage Keys Reference](#-localstorage-keys-reference)
- [Free vs Pro Plan](#-free-vs-pro-plan)
- [Usage Limits](#-usage-limits)
- [Keyboard Shortcuts](#-keyboard-shortcuts)
- [API Reference](#-api-reference)
- [System Prompts](#-system-prompts)
- [Security](#-security)
- [Known Issues / TODO](#-known-issues--todo)
- [Roadmap](#-roadmap)
- [About Vyoma Group](#-about-vyoma-group)
- [License](#-license)

---

## 🌟 Overview

**Arka** (Sanskrit: "Sun" — radiant, powerful, illuminating) is an AI assistant designed to feel like a genius best friend. It adapts to the user's language (English, Hindi, Hinglish), expertise level, and emotional tone in real time.

- **Built by:** Vyoma Group
- **Live URL:** [arka.vyomagroup.online](https://arka.vyomagroup.online)
- **Current Model:** `qwen/qwen3.5-122b-a10b` (Arka Standard) via NVIDIA NIM API
- **Authentication:** Google Sign-In via Firebase (redirect flow)
- **Data Storage:** Chat history stored locally in browser `localStorage`, with optional server-side backup via `history.php`

---

## ✨ Features

### 🔐 Google Authentication (Firebase)

Firebase Authentication with Google Sign-In using the **redirect** flow (`signInWithRedirect`). Handles redirect results before `onAuthStateChanged` to prevent redirect loops on shared hosting.

- **Auth error display** with specific messages for common errors (`popup-blocked`, `unauthorized-domain`, `network-request-failed`, etc.)
- **HTTPS enforcement** in production (auto-redirects HTTP → HTTPS)
- **Safety timeout:** If Firebase takes >5 seconds, the login screen is shown automatically
- **Login screen** features a theme toggle, Google branded button, and branded Arka orb animation
- **localStorage keys:** `arka_user` (stores `name`, `email`, `photo`, `uid`, `plan`, `joinedAt`)

### ⏳ Loading Screen (No Flicker)

A full-screen loading screen shows the Arka logo with a pulsing animation while Firebase resolves auth state. It uses inline styles to render immediately without waiting for CSS, preventing any white flash. Fades out with CSS transition once authentication is resolved.

### 💬 Chat System

Full-featured chat interface with:

- **Markdown rendering** in AI responses (bold, italic, strikethrough, code blocks, headers, blockquotes, lists, links, horizontal rules)
- **Code blocks** with syntax language tags and **Copy** button
- **Auto-resize textarea** for multi-line input (max 150px height)
- **Typing indicator** (three animated dots) while waiting for AI response
- **Message timestamps** on each message
- **User/AI avatars** with letter fallback for missing profile photos
- **Welcome screen** with branded orb and four suggestion cards:
  - Analyze Image
  - Solve & Reason
  - Code Help
  - Learn & Explain
- **Error messages** displayed as styled red bubbles with ⚠ icon
- **Browser notifications** when Arka finishes responding and the tab is inactive
- **Disclaimer:** "Arka can make mistakes. Verify important info."

### 📂 Chat History (Star, Rename, Delete)

Client-side chat history stored per-user in `localStorage`, with server-side backup to `history.php`.

- **Per-user storage** keyed by Firebase UID (`arka_chats_{uid}`)
- **Starred chats** appear at the top of the sidebar list
- **Inline rename** — click rename from context menu, edit in-place, press Enter to save
- **Context menu** on each chat (3-dot button):
  - ⭐ Star / Unstar
  - ✏️ Rename
  - 📁 Add to Project (placeholder — shows "Coming Soon")
  - 🗑 Delete
- **Export current chat** as `.txt` file
- **Clear All** chats with confirmation dialog
- Auto-generates chat title from first user message (truncated to 40 chars)

### 🖼 Image Analysis

Vision-native image analysis using the qwen3.5-122b-a10b model via NVIDIA NIM:

- **Upload methods:** File picker, Ctrl+V paste, drag & drop
- **Attachment preview** with thumbnail and remove button
- **Lightbox** for full-size image viewing on click
- **Image sent as base64** data URL in the API payload
- **Free plan limit:** 5 images per day (24h rolling window)
- **Pro plan:** Unlimited
- **Max file size:** 10 MB
- **localStorage key:** `arka_image_usage_{uid}` (stores `count` and `resetTime`)

### 📄 File Analysis (PDF, Code, Docs)

Full file analysis pipeline with text extraction:

- **Supported formats:** `.pdf`, `.doc`, `.docx`, `.txt`, `.md`, `.csv`, `.json`, `.js`, `.py`, `.php`, `.html`, `.css`, `.ts`, `.jsx`, `.tsx`, `.java`, `.cpp`, `.c`, `.rb`, `.go`, `.rs`, `.swift`, `.kt`
- **PDF extraction** via PDF.js (`pdfjsLib`) — extracts text from all pages
- **File preview chip** shows file icon (colored by type), filename, and size
- **File content truncation** at 50,000 characters with notice
- **File size limits:** Free: 10 MB, Pro: 50 MB
- **Free plan limit:** 5 files per day (24h rolling window)
- **localStorage key:** `arka_file_usage_{uid}` (stores `count` and `resetTime`)
- **Attach popup menu** with two options: Upload Image / Upload File — each showing remaining daily count

### 🧠 Deep Reasoning Toggle

Activates a separate reasoning system prompt with structured analysis output:

- **Toggle button** in the input bar with brain icon
- **Active indicator:** Orange dot on button + "Deep Reasoning ON" pill above input
- **Visual indicator** on AI messages that used reasoning (brain icon + "Deep Reasoning" label)
- **Sends `reasoning: true`** in API payload, which adds `{ "reasoning": { "effort": "high" } }` to the NVIDIA request
- **Free plan limit:** 3 deep reasoning uses per day
- **Auto-disables** when limit is exhausted; shows warning badge
- **localStorage key:** `arka_reasoning_usage_{uid}`

### 🎭 Adaptive Personality Engine

Real-time profile analysis that shapes Arka's responses:

- **Language detection:** English, Hindi, Hinglish (via character analysis and keyword matching)
- **Expertise detection:** Beginner, Intermediate, Expert (based on technical vocabulary density)
- **Tone detection:** Casual, Formal, Emotional (based on word choice, exclamations, emojis)
- **Topic tracking:** Detects topics across 10 categories (coding, maths, science, career, finance, health, writing, learning, legal, philosophy) — keeps last 15
- **Message statistics:** Running count and average message length
- **Profile summary** sent as context with every API request
- **Blended expertise** — updates gradually (60% old, 40% new) to avoid sudden jumps
- **localStorage key:** `arka_profile_{uid}`

### 🧠 Memory System

Local-first persistent memory organized into 5 categories:

- **Categories:** Instructions, Identity, Career, Projects, Preferences
- **Auto-extraction** from user messages via pattern matching:
  - "always respond…" → Instructions
  - "my name is…" → Identity
  - "I'm building…" → Projects
  - "I prefer…" → Preferences
- **Memory Manager modal** — view, edit, delete, and add memories per category
- **Import Memory** from other AI providers (ChatGPT, Claude, Gemini) via structured prompt + paste
- **Export Memories** as `.txt` file
- **Memory context** injected into system prompt (max 500 words)
- **Toggle on/off** in Settings → Capabilities
- **localStorage keys:** `arka_memory_{uid}`, `arka_settings_{uid}.memoryEnabled`

### ⚙️ Settings Modal (6 Tabs)

Full-screen settings panel with sidebar navigation:

#### General Tab
- Full name (editable, syncs to `arka_user`)
- Nickname (what Arka calls you)
- Occupation selection (10 preset pills + custom "Other" input):
  - Developer/Engineer, Designer, Student, Business/Finance, Healthcare, Legal, Creative/Content, Marketing, Research/Science, Other
- Freeform preferences textarea ("always respond in Hinglish…")
- Link to Vyoma's Guidelines
- Response completion notifications toggle (uses browser Notification API)
- Save Changes button

#### Account Tab
- User card with photo/avatar, name, email, plan badge
- Connected Google Account display
- Account info table: User ID (copyable), Email, Plan, Joined date, Last Active
- Current Session card: Device/OS, Browser, Location (via ipapi.co), Login Time, Status
- Usage Stats (2×2 grid): Images, Deep Reasoning, Files Analyzed, Total Chats
- Danger Zone: Clear all chat history, Delete Account (type "DELETE" to confirm)

#### Privacy Tab
- Expandable sections: "How we protect your data", "How we use your data"
- Privacy toggles (instant-save):
  - Location metadata
  - Help improve Arka (anonymized usage data)
  - Marketing emails
- Data actions: Export Data (modal with date range filters), Clear conversation history

#### Billing Tab
- Current plan card with icon and upgrade button
- Free plan features checklist (7 items)
- Pro benefits grid (6 cards, some with "Coming Soon" chips)
- Pricing card with Monthly/Yearly toggle:
  - Monthly: ₹299/month
  - Yearly: ₹2,499/year (save 30%)
- "Join Pro Waitlist" CTA

#### Capabilities Tab
- Memory toggle (generate memory from chat history)
- Memory info box explaining local-first processing
- Manage Memories button → opens Memory Manager modal
- Import Memory button → opens Import Memory modal
- Tool Access mode (radio buttons):
  - Load tools when needed (default)
  - Tools always loaded

#### Appearance Tab
- Dark mode toggle (live preview)
- Font size pills: Small, Medium, Large
- Compact mode toggle

### 🆘 Help Center Widget

Slide-in panel with two tabs (Home / Help):

**Home tab:**
- System status card ("All Systems Operational")
- "Send us a message" → mailto:support@vyomagroup.com
- Search bar with live filtering
- 8 FAQ items with article detail view

**Help tab:**
- Article search bar
- 7 collection categories (Getting Started, Chat & Features, Image Analysis, Free & Pro Plans, Privacy & Security, Troubleshooting, About Vyoma)

### 👤 Profile Menu

Dropdown from user avatar in sidebar footer:

- Email display
- **Settings** (with `Ctrl ,` shortcut hint)
- **Language** submenu (12 languages: English, Hindi, Spanish, French, German, Portuguese, Japanese, Korean, Chinese, Arabic, Italian, Indonesian)
- **Get Help** → opens Help Center panel
- **Upgrade Plan** → opens Upgrade modal
- **Learn More** submenu:
  - About Vyoma (vyomagroup.com)
  - About Arka (vyomagroup.com/arka)
  - Tutorials (vyomagroup.com/tutorials)
  - Usage Policy (vyomagroup.com/guidelines)
  - Privacy Policy (vyomagroup.com/privacy)
  - Keyboard Shortcuts → opens shortcuts modal
- **Log out**

### 🌐 Language Selector

12-language selector available from the profile dropdown submenu. Saves selection to `arka_language` in localStorage. Active language is marked with ✓.

### 🎹 Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + K` | New Chat |
| `Ctrl + F` | Search Chats |
| `Enter` | Send Message |
| `Shift + Enter` | New Line |
| `Ctrl + D` | Toggle Theme |
| `Ctrl + ,` | Open Settings |
| `Esc` | Close Modal / Submenu |

### 🌗 Dark / Light Mode

- Default: Dark mode
- Toggle via: login screen button, appearance settings, or `Ctrl + D`
- Persisted in `arka-theme` localStorage key
- Uses CSS custom properties for full theme coverage
- Dark: `#0c0c0c` background, warm neutrals
- Light: `#faf8f5` background, earthy tones
- Accent color: `#e8622a` (consistent across both themes)

### 💎 Free / Pro Plan System

Client-side plan management with upgrade path:

- Plan stored in `arka_user.plan` (`"free"` or `"pro"`)
- Upgrade modal with benefits list and "Join Pro Waitlist" CTA
- Plan badge in sidebar (Free/Pro) and settings
- Upgrade button hidden for Pro users
- Usage badges hidden for Pro users

### 📊 Usage Tracking

Per-user, 24-hour rolling window usage tracking:

- **Image uploads:** tracked in `arka_image_usage_{uid}`
- **File analyses:** tracked in `arka_file_usage_{uid}`
- **Deep reasoning:** tracked in `arka_reasoning_usage_{uid}`
- **Total chats:** counted from `arka_chats_{uid}`
- Displayed in top bar (image/reasoning badges) and Account settings (2×2 usage grid)
- Warning badges appear when limits are reached

### 🎤 Voice Input (Dictation)

Browser-native speech recognition via Web Speech API:

- Microphone button in input bar
- Uses `SpeechRecognition` / `webkitSpeechRecognition`
- Default language: `en-IN`
- Appends dictated text to existing input
- Visual recording indicator on mic button
- Hidden if browser doesn't support Speech Recognition
- Shows toast if microphone access is denied

### 📜 Vyoma's Guidelines Modal

Full usage policy modal (effective March 30, 2026) with sections:

- Our Mission
- What Arka is designed for
- What is NOT allowed
- Important Disclaimers
- Your Privacy
- Contact: arka.ai.support@gmail.com

### 📤 Export Data System

Export modal with:

- Date range filters: All, Last 30 days, Last 90 days
- Includes: Conversations (with count), Profile settings, Account info
- Exports as JSON file: `arka-data-export-{date}.json`

---

## 🛠 Tech Stack

| Layer | Technology | Details |
|-------|-----------|---------|
| **Frontend** | HTML5, CSS3, JavaScript (ES Modules) | Single-page application, no framework |
| **Styling** | Vanilla CSS with CSS Custom Properties | Design tokens, dark/light theme, 4500+ lines |
| **Fonts** | Google Fonts | Playfair Display (serif), Inter (sans), JetBrains Mono (mono) |
| **Icons** | Material Symbols Rounded + inline SVGs + custom SVG files | Lucide-style icon set |
| **Auth** | Firebase Authentication v12.11.0 | Google Sign-In (redirect flow) |
| **AI Backend** | PHP 8.0+ | cURL to NVIDIA NIM API |
| **AI Model** | qwen/qwen3.5-122b-a10b | Via NVIDIA `integrate.api.nvidia.com/v1/chat/completions` |
| **PDF Parsing** | PDF.js 3.11.174 | Client-side PDF text extraction |
| **Voice** | Web Speech API | Browser-native speech recognition |
| **SSL** | cacert.pem bundle | For cURL on Windows/XAMPP environments |
| **Hosting** | Hostinger (Apache) | .htaccess for HTTPS, cache control, file protection |

---

## 📁 File Structure

```
arka/
├── index.html            # Main SPA (1268 lines) — login, chat, settings, modals
├── style.css             # Complete stylesheet (4508 lines) — design system, all components
├── script.js             # Frontend logic (3344 lines) — Firebase, chat, profiling, settings
├── api.php               # Backend API (305 lines) — routes requests to NVIDIA NIM
├── config.php            # Configuration (342 lines) — API keys, system prompts, rate limits
├── history.php           # Chat history manager (217 lines) — CRUD for server-side chat storage
├── .htaccess             # Apache config — HTTPS, cache control, file protection
├── .gitignore            # Excludes config.php, chat_history/, IDE files
├── cacert.pem            # SSL CA bundle for cURL on Windows
├── README.md             # This file
├── arka.zip              # Distribution archive
├── chat_history/         # Server-side chat storage directory (created by history.php)
└── svg/                  # Custom SVG icons
    ├── brain-svgrepo-com.svg          # Deep reasoning brain icon
    ├── files-svgrepo-com.svg          # Attach file icon
    ├── mic-svgrepo-com.svg            # Microphone / voice input icon
    ├── send-alt-svgrepo-com.svg       # Send message icon
    └── warning-1-svgrepo-com.svg      # Usage limit warning icon
```

---

## 🎨 SVG Icons

| File | Size | Used In |
|------|------|---------|
| `brain-svgrepo-com.svg` | 5.4 KB | Deep reasoning toggle button, reasoning pill, reasoning indicator on AI messages |
| `files-svgrepo-com.svg` | 719 B | Attach menu button (image/file upload trigger) |
| `mic-svgrepo-com.svg` | 783 B | Voice input (dictation) button |
| `send-alt-svgrepo-com.svg` | 993 B | Send message button |
| `warning-1-svgrepo-com.svg` | 664 B | Usage limit warning badges (images + reasoning) |

All SVGs use CSS `filter` for dark/light mode adaptation (`brightness(0) invert(1)` for white, or hue-rotate for accent color).

---

## 🚀 Quick Start

```bash
# Clone the repository
git clone https://github.com/vyomagroup/arka-ai.git
cd arka

# Add your NVIDIA API key
# Edit config.php → set NVIDIA_API_KEY

# Start the PHP development server
php -S localhost:8000

# Open in browser
# Navigate to http://localhost:8000
```

> **Prerequisites:** PHP 8.0+ with cURL extension enabled.

---

## 🌐 Deployment (Hostinger)

### Step-by-Step

1. **Upload files** via Hostinger File Manager to your domain's `public_html/` directory (or subdomain directory)

2. **Set your NVIDIA API key** in `config.php`:
   ```php
   define('NVIDIA_API_KEY', 'nvapi-your-key-here');
   ```

3. **Add domain to Firebase authorized domains:**
   - Go to [Firebase Console](https://console.firebase.google.com)
   - Navigate to **Authentication → Settings → Authorized domains**
   - Add: `arka.vyomagroup.online` (or your domain)

4. **Ensure HTTPS is enabled** on your Hostinger domain (usually automatic with Hostinger)

5. **Verify `.htaccess`** is uploaded and Apache mod_rewrite is enabled:
   - Forces HTTPS
   - Prevents caching of `index.html`
   - Blocks direct access to `config.php` and `history.php`
   - Protects `chat_history/` directory

6. **Upload `cacert.pem`** — required for SSL verification in cURL requests. Download from [curl.se/ca/cacert.pem](https://curl.se/ca/cacert.pem) if not included.

---

## 🔥 Firebase Setup

### Step-by-Step

1. **Create a Firebase project** at [console.firebase.google.com](https://console.firebase.google.com)

2. **Enable Google Sign-In:**
   - Go to **Authentication → Sign-in method**
   - Enable **Google** provider
   - Set support email

3. **Add authorized domains:**
   - Go to **Authentication → Settings → Authorized domains**
   - Ensure these are listed:
     - `localhost`
     - `arka.vyomagroup.online`
     - Any other deployment domains

4. **Firebase config is already in `script.js`:**
   ```javascript
   const firebaseConfig = {
     apiKey: "AIzaSyBbv5mvJvQxA_H3WXQzCcaJ8SOwYfG7tzo",
     authDomain: "arkaai-b3d16.firebaseapp.com",
     projectId: "arkaai-b3d16",
     storageBucket: "arkaai-b3d16.firebasestorage.app",
     messagingSenderId: "510357032532",
     appId: "1:510357032532:web:5574d7b1750ef737f667c1",
     measurementId: "G-WQ4J7YRWV8"
   };
   ```

5. **Firebase SDK:** Loaded via ES modules from `gstatic.com` (v12.11.0) — no npm required.

---

## ⚙️ Configuration Reference

All constants defined in `config.php`:

| Constant | Value | Description |
|----------|-------|-------------|
| `AI_PROVIDER` | `'nvidia'` | AI provider identifier (NVIDIA NIM exclusively) |
| `NVIDIA_API_KEY` | `'nvapi-...'` | NVIDIA NIM API key for authentication |
| `NVIDIA_MODEL` | `'qwen/qwen3.5-122b-a10b'` | The AI model used for all requests |
| `AVAILABLE_MODELS` | `['nvidia' => [...]]` | Registry of available models (single model) |
| `SYSTEM_PROMPT` | *(heredoc)* | Default personality prompt (~225 lines) |
| `REASONING_SYSTEM_PROMPT` | *(heredoc)* | Deep reasoning mode prompt (~80 lines) |
| `RATE_LIMIT_REQUESTS` | `30` | Max requests per rate limit window |
| `RATE_LIMIT_WINDOW` | `60` | Rate limit window in seconds |
| `HISTORY_DIR` | `__DIR__ . '/chat_history'` | Path to server-side chat history storage |
| `MAX_CONTEXT_MESSAGES` | `20` | Max messages sent as context to the AI |
| `MAX_TOKENS` | `8192` | Max response tokens (defined but API uses 4096) |
| `TEMPERATURE` | `0.75` | Model temperature (defined but API uses 1) |

---

## 💾 localStorage Keys Reference

| Key | Description | Structure |
|-----|-------------|-----------|
| `arka_user` | Current user account data | `{ name, email, photo, uid, plan, joinedAt }` |
| `arka_chats_{uid}` | All chat conversations (per-user) | `{ chatId: { id, title, messages[], model, provider, starred, projectId, createdAt, updatedAt } }` |
| `arka_profile_{uid}` | Adaptive personality profile | `{ language, expertise, tone, emojiUsage, topicsDiscussed[], messageCount, avgMessageLength, lastActive, nickname, occupation, preferences }` |
| `arka_settings_{uid}` | User settings & preferences | `{ notifications, privacyLocation, privacyImprove, privacyMarketing, fontSize, compactMode, memoryEnabled, toolAccessMode }` |
| `arka_image_usage_{uid}` | Daily image upload counter | `{ count, resetTime }` |
| `arka_reasoning_usage_{uid}` | Daily reasoning usage counter | `{ count, resetTime }` |
| `arka_file_usage_{uid}` | Daily file analysis counter | `{ count, resetTime }` |
| `arka_memory_{uid}` | Persistent memory entries | `{ enabled, lastUpdated, instructions[], identity[], career[], projects[], preferences[] }` |
| `arka-theme` | Current theme selection | `"dark"` or `"light"` |
| `arka-provider` | Selected AI provider | `"nvidia"` |
| `arka-model` | Selected AI model | `"qwen/qwen3.5-122b-a10b"` |
| `arka_language` | Selected UI language | Language code (e.g., `"en"`, `"hi"`) |

---

## 💎 Free vs Pro Plan

| Feature | Free | Pro |
|---------|------|-----|
| Chat messages | ✅ Unlimited | ✅ Unlimited |
| Image analysis | 5 / day | ✅ Unlimited |
| File analysis | 5 / day | ✅ Unlimited |
| Deep reasoning | 3 / day | ✅ Unlimited |
| File upload size | 10 MB | 50 MB |
| Arka Standard model | ✅ | ✅ |
| Chat history & export | ✅ | ✅ |
| Adaptive personality | ✅ | ✅ |
| Memory system | ✅ | ✅ |
| Priority access | ❌ | ✅ |
| Mindmap generation | ❌ | 🔜 Coming Soon |
| AI Agent roles | ❌ | 🔜 Coming Soon |
| Voice I/O | ❌ | 🔜 Coming Soon |

**Pricing (Coming Soon):**
- Monthly: ₹299 / month
- Yearly: ₹2,499 / year (save 30%)

---

## 📊 Usage Limits

| Feature | Free Limit | Reset |
|---------|-----------|-------|
| Image analysis | 5 / day | 24 hours (rolling) |
| File analysis | 5 / day | 24 hours (rolling) |
| Deep reasoning | 3 / day | 24 hours (rolling) |
| API rate limit | 30 requests / 60s | Per-IP, file-based |

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + K` | New Chat |
| `Ctrl + F` | Search Chats |
| `Enter` | Send Message |
| `Shift + Enter` | New Line (in message input) |
| `Ctrl + D` | Toggle Dark / Light Theme |
| `Ctrl + ,` | Open Settings |
| `Ctrl + V` | Paste Image from clipboard |
| `Esc` | Close active modal, submenu, or panel |

---

## 🔌 API Reference

### Endpoint

```
POST /api.php
```

### Request Body

```json
{
  "messages": [
    { "role": "user", "content": "Hello" },
    { "role": "assistant", "content": "Hi there!" },
    { "role": "user", "content": "How are you?" }
  ],
  "provider": "nvidia",
  "model": "qwen/qwen3.5-122b-a10b",
  "image": "data:image/png;base64,...",
  "reasoning": false,
  "stream": false,
  "userProfile": "[USER PROFILE] Language: english | Expertise: intermediate | ...",
  "userContext": "User's full name: Alice. User prefers to be called: Ali. ..."
}
```

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `messages` | array | ✅ | Conversation messages (user/assistant roles) |
| `provider` | string | ❌ | AI provider (forced to `"nvidia"` server-side) |
| `model` | string | ❌ | Model ID (forced to configured model server-side) |
| `image` | string | ❌ | Base64 data URL for image analysis |
| `reasoning` | boolean | ❌ | Enable deep reasoning mode |
| `stream` | boolean | ❌ | Enable streaming responses (SSE) |
| `userProfile` | string | ❌ | Adaptive profile summary for context |
| `userContext` | string | ❌ | Identity context (name, nickname, occupation) |

### Response

**Success (200):**
```json
{
  "reply": "Here's my response..."
}
```

**Error (4xx/5xx):**
```json
{
  "error": "Error description message"
}
```

### Model List Endpoint

```
GET /api.php?action=models
```

Returns:
```json
{
  "models": {
    "nvidia": {
      "qwen/qwen3.5-122b-a10b": "Arka Standard"
    }
  }
}
```

### Error Handling

- `400` — Invalid request (missing `messages` field)
- `405` — Method not allowed (non-POST/GET)
- `429` — Rate limit exceeded (30 req/60s per IP)
- `500` — API error (NVIDIA API failure, missing key, invalid response)

---

## 🧠 System Prompts

### Normal System Prompt (SYSTEM_PROMPT)

Defines Arka's core personality across these sections:

- **Core Identity** — Name, creator (Vyoma Group), personality traits
- **Personality** — Warm, witty, emoji-natural, energy-matching, humor-driven
- **Language Adaptation** — English, Hindi, Hinglish mirroring
- **Adaptive Intelligence** — Adjusts depth based on expertise/emotional state/intent
- **Knowledge & Capabilities** — Expert across 12+ domains
- **Response Style** — Lead with answer, use markdown formatting, code blocks with comments
- **Memory & Continuity** — Reference conversation context, use names
- **Honesty & Integrity** — Never fabricates, adds professional disclaimers
- **What Arka Never Does** — No images/audio generation, no prompt leaking, no harmful advice, no corporate-speak openers
- **Special Behaviors** — Origin deflection ("built by Vyoma Group"), emotional awareness
- **About Arka & Vyoma** — Consistent branding response with link to vyomagroup.com
- **File Analysis Behavior** — Type-specific analysis instructions for PDFs, code, data, documents

### Reasoning System Prompt (REASONING_SYSTEM_PROMPT)

Activates structured analysis output format:

```
🧠 **Analysis:** [Step-by-step thinking]
✅ **Answer:** [Clear final answer]
💡 **Additional considerations:** [Caveats, alternatives]
```

Retains all personality traits from the normal prompt. Used for complex math, multi-step coding, ethics, strategy, debugging, and research.

### User Context (buildUserContext)

Assembled from settings and sent with every message:

- Full name
- Preferred nickname (or "call by first name")
- Occupation/background
- Personal preferences
- Language preference
- Expertise level

---

## 🔒 Security

### .htaccess Rules

- **Force HTTPS** via `mod_rewrite` (301 redirect)
- **Cache-Control headers** on `index.html` (no-cache, no-store, must-revalidate)
- **PHP handler** explicitly set for `.php` files
- **Direct access blocked** for:
  - `config.php` (Order deny,allow → Deny from all)
  - `history.php` (Order deny,allow → Deny from all)
- **chat_history/ directory** protected (Require all denied)

### Additional Security Measures

- **API key never exposed** to frontend (stored server-side in `config.php`)
- **`config.php` in `.gitignore`** — never committed to version control
- **Error output suppressed** in PHP (`error_reporting(0)`, `display_errors = 0`)
- **Output buffering** (`ob_start()`) prevents accidental HTML from corrupting JSON responses
- **Rate limiting** — File-based per-IP rate limiting (30 requests per 60 seconds)
- **SSL verification** — Uses `cacert.pem` CA bundle for NVIDIA API requests; fallback to no-verify on development
- **Firebase domain restrictions** — Only authorized domains can use Google Sign-In
- **HTTPS enforcement** — JS-level redirect for production hosts
- **Input sanitization** — Chat history filenames sanitized via regex (`/[^a-zA-Z0-9_\-]/`)
- **Cache-control meta tags** in `index.html` (no-cache, no-store, must-revalidate, Pragma: no-cache, Expires: 0)

---

## 🐛 Known Issues / TODO

- **`history.php` is blocked** by `.htaccess` (`Deny from all`), which may prevent server-side chat history from working in production. The frontend falls back to localStorage gracefully.
- **`MAX_TOKENS` (8192)** and **`TEMPERATURE` (0.75)** are defined in `config.php` but the API handler uses hardcoded values of `4096` and `1` respectively.
- **"Add to Project"** in chat context menu shows "Coming Soon" toast — feature not yet implemented.
- **Search Chats** (`Ctrl+F`) shortcut is listed in the keyboard shortcuts modal but the search functionality is not implemented in the sidebar.

---

## 🗺 Roadmap

Based on "Coming Soon" placeholders found in the codebase:

| Feature | Found In | Status |
|---------|----------|--------|
| **Mindmap Generation** | Upgrade modal, Billing → Pro benefits | 🔜 Coming Soon |
| **AI Agent Roles** (Legal, Financial, Health, Career) | Upgrade modal, Billing → Pro benefits | 🔜 Coming Soon |
| **Voice Input/Output** | Billing → Pro benefits (basic input exists) | 🔜 Coming Soon |
| **Pro Plan Payment** | Billing → pricing note | 🔜 Coming Soon |
| **Projects System** | Chat context menu → "Add to Project" | 🔜 Coming Soon |
| **Help Center Articles** | Help panel collections → shows "Articles being added" toast | 🔜 Coming Soon |
| **Vyoma Group Website** | System prompt, Learn More → "(page coming soon!)" | 🔜 Coming Soon |

---

## 🏢 About Vyoma Group

- **Company:** Vyoma Group
- **Website:** [vyomagroup.online](https://vyomagroup.online)
- **Arka Live:** [arka.vyomagroup.online](https://arka.vyomagroup.online)
- **Support Email:** [arka.ai.support@gmail.com](mailto:arka.ai.support@gmail.com)
- **Support (Help Center):** [support@vyomagroup.com](mailto:support@vyomagroup.com)
- **Mission:** Building the next generation of intelligent AI tools for everyone.
- **Guidelines:** Effective March 30, 2026

---

## 📄 License

MIT License

Copyright (c) 2026 Vyoma Group

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

<div align="center">

Built with ♥ by **Vyoma Group**

Powered by **NVIDIA NIM**

✦

</div>
]]>
