<div align="center">

```
 █████╗ ██████╗ ██╗  ██╗ █████╗ 
██╔══██╗██╔══██╗██║ ██╔╝██╔══██╗
███████║██████╔╝█████╔╝ ███████║
██╔══██║██╔══██╗██╔═██╗ ██╔══██║
██║  ██║██║  ██║██║  ██╗██║  ██║
╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝╚═╝  ╚═╝
```

### ✦ *Your Intelligent AI Companion*

<br/>

[![Status](https://img.shields.io/badge/Status-Live_Beta-e8622a?style=for-the-badge&logo=statuspage&logoColor=white)](https://arka.vyomagroup.online)
[![Version](https://img.shields.io/badge/Version-0.3.0_Beta-1a1714?style=for-the-badge&logo=semver&logoColor=white)](https://vyomagroup.online/changelog/)
[![PHP](https://img.shields.io/badge/PHP-8.0+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![Firebase](https://img.shields.io/badge/Firebase-v12.11.0-FFCA28?style=for-the-badge&logo=firebase&logoColor=black)](https://firebase.google.com)
[![License](https://img.shields.io/badge/License-MIT-22c55e?style=for-the-badge)](LICENSE)
[![Made in India](https://img.shields.io/badge/Made_in-India_🇮🇳-FF9933?style=for-the-badge)](https://vyomagroup.online)

<br/>

**[🌐 Live App](https://arka.vyomagroup.online) • [📚 Docs](https://vyomagroup.online/docs/) • [📖 Blog](https://vyomagroup.online/blog/) • [💬 Contact](https://vyomagroup.online/contact/)**

<br/>

<img src="https://img.shields.io/badge/NVIDIA-NIM-76B900?style=flat-square&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/Qwen-3.5_122B-6366f1?style=flat-square&logoColor=white" />
<img src="https://img.shields.io/badge/Google-Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black" />
<img src="https://img.shields.io/badge/Vanilla-JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black" />

</div>

---

<div align="center">

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  AI that learns you. Remembers you. Adapts to you.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

</div>

---

## ⚡ What is Arka?

**Arka** *(Sanskrit: अर्क — The Sun)* is an intelligent AI companion built by **[Vyoma Group](https://vyomagroup.online)** — India's next-generation AI company. Unlike generic chatbots, Arka doesn't just respond. It **listens, adapts, remembers, and evolves** with every conversation.

> *"Most AI talks at you. Arka talks with you."*

Whether you're a student solving calculus, a developer debugging code, a professional drafting reports, or just someone who wants a brilliant friend to think things through — **Arka is built for you.**

---

## 🌟 Feature Showcase

<div align="center">

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│   🎭  ADAPTIVE PERSONALITY      🧠  DEEP REASONING          │
│   ────────────────────────      ──────────────────          │
│   Speaks your language.         Step-by-step thinking       │
│   Matches your expertise.       for complex problems.       │
│   Mirrors your energy.          Shows its work.             │
│                                                             │
│   🖼️  IMAGE ANALYSIS            📄  FILE ANALYSIS           │
│   ──────────────────            ─────────────────           │
│   Upload, paste, or drag.       PDFs, docs, code.           │
│   Instant visual insight.       Deep document Q&A.          │
│   No image generation.          CSV data analysis.          │
│                                                             │
│   💾  MEMORY SYSTEM             🌐  MULTILINGUAL            │
│   ─────────────────             ──────────────              │
│   Remembers across chats.       English, Hindi,             │
│   Learns your projects.         Hinglish — natural          │
│   Imports from ChatGPT.         language detection.         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

</div>

---

## 🚀 Quick Start

```bash
# 1. Clone the repository
git clone https://github.com/your-username/arka-ai.git
cd arka-ai/arka

# 2. Configure your API key
# Edit config.php and add your NVIDIA API key:
# define('NVIDIA_API_KEY', 'nvapi-xxxxxxxxxxxx');
# Get a free key at: https://build.nvidia.com

# 3. Start the server
php -S localhost:8000

# 4. Open in browser
# → http://localhost:8000
# → Sign in with Google
# → Start chatting with Arka! 🎉
```

---

## 📁 Project Structure

```
arka-ai/
│
├── 📁 arka/                      # Main application
│   ├── 📄 index.html             # Full app UI (auth + chat)
│   ├── 🎨 style.css              # All styles (~3000 lines)
│   ├── ⚡ script.js              # Frontend logic (~2000 lines)
│   ├── 🔧 api.php                # AI backend router
│   ├── ⚙️  config.php            # API keys & configuration
│   ├── 📝 history.php            # Server-side chat backup
│   ├── 📁 svg/                   # Custom SVG icon system
│   │   ├── brain-svgrepo-com.svg
│   │   ├── mic-svgrepo-com.svg
│   │   ├── files-svgrepo-com.svg
│   │   ├── send-alt-svgrepo-com.svg
│   │   └── warning-1-svgrepo-com.svg
│   ├── 📁 chat_history/          # Server-side chat backup
│   ├── 📁 .well-known/           # AI plugin discovery
│   └── 📄 .htaccess              # Server config & HTTPS
│
├── 📁 seo/                       # SEO optimization files
│   ├── meta-tags.html
│   ├── structured-data.js
│   └── SETUP_GUIDE.md
│
├── 🤖 robots.txt                 # Crawler rules
├── 🗺️  sitemap.xml               # Google sitemap
├── 🧠 llms.txt                   # AI crawler reference
├── 📖 llms-full.txt              # Detailed AI reference
└── 📄 README.md                  # You are here
```

---

## ✨ Features In Depth

### 🎭 Adaptive Personality Engine

Arka doesn't just answer — it **adapts in real-time** to who you are:

| What Arka Detects | How It Adapts |
|-------------------|---------------|
| 🌐 Language (English/Hindi/Hinglish) | Responds in your exact language mix |
| 🎓 Expertise Level (Beginner → Expert) | Adjusts depth and vocabulary |
| 💬 Tone (Casual/Formal/Emotional) | Mirrors your energy and style |
| 😄 Emoji Usage | Uses emojis if you do |
| 📚 Topics Discussed | Builds context across conversation |

```javascript
// User profile stored locally — NEVER on servers
{
  language: 'hinglish',
  expertise: 'intermediate', 
  tone: 'casual',
  emojiUsage: true,
  topicsDiscussed: ['coding', 'ai', 'startups'],
  messageCount: 47,
  lastActive: 1712000000000
}
```

---

### 🧠 Deep Reasoning Mode

Toggle the **brain icon** to activate step-by-step analytical thinking:

```
Normal Mode:  Fast, conversational, direct answers
              ─────────────────────────────────────
Reasoning:    🧠 Analysis → Step-by-step thinking
              ✅ Answer → Clear final conclusion  
              💡 Considerations → Caveats & follow-ups
```

**When to use Deep Reasoning:**
- Complex mathematics
- Multi-step debugging  
- Strategic decisions
- Scientific analysis
- Legal/financial questions *(with disclaimers)*

**Limits:** Free: 3/day · Pro: Unlimited

---

### 🖼️ Image Analysis

Three ways to analyze images:

```
📁 Upload Button  →  Click the files icon → Upload Image
📋 Ctrl+V Paste   →  Copy any image → paste in chat input
🖱️  Drag & Drop   →  Drag image directly onto input area
```

**Supported formats:** JPG, PNG, GIF, WebP, BMP (max 10MB)  
**⚠️ Important:** Arka **analyzes** images — it does NOT generate them.

**Limits:** Free: 5/day · Pro: Unlimited

---

### 📄 File Analysis

Arka reads and understands your files:

```
Documents  →  PDF, DOC, DOCX, TXT, MD
Data       →  CSV, JSON  
Code       →  JS, TS, PY, PHP, HTML, CSS, and all major languages
```

**What Arka does with files:**
- Summarizes content
- Answers questions about the document
- Reviews and explains code
- Analyzes data patterns
- Translates content

**Limits:** Free: 5/day · Pro: Unlimited (50MB max)

---

### 💾 Memory System

Arka remembers across ALL conversations:

```
┌─────────────────────────────────────────┐
│  Memory Categories                      │
│  ─────────────────                      │
│  📋 Instructions  → Rules you've set    │
│  👤 Identity      → Your background     │
│  💼 Career        → Your work context   │
│  🚀 Projects      → What you're building│
│  ⭐ Preferences   → How you like things │
└─────────────────────────────────────────┘
```

**Import memory from other AIs:**
Copy a special prompt → paste into ChatGPT/Claude/Gemini → import the response into Arka. Your context follows you.

**Privacy:** Memory lives in YOUR browser. We literally cannot see it.

---

## 💎 Free vs Pro

| Feature | 🆓 Free | ✨ Pro |
|---------|:-------:|:-----:|
| Chat messages | ∞ Unlimited | ∞ Unlimited |
| Image analysis | 5 / day | ∞ Unlimited |
| File analysis | 5 / day | ∞ Unlimited |
| Deep reasoning | 3 / day | ∞ Unlimited |
| File upload size | 10 MB | 50 MB |
| AI models | Standard | All models |
| Memory system | ✅ Full | ✅ Full |
| Chat history | ✅ Full | ✅ Full |
| Mindmap generation | ❌ | 🔜 Soon |
| Agent roles | ❌ | 🔜 Soon |
| Voice I/O | ❌ | 🔜 Soon |
| Priority speed | Normal | ⚡ Fast |
| **Price** | **₹0 forever** | **₹299/month** |

---

## ⚙️ Configuration

All settings live in `config.php`:

```php
<?php
// ═══════════════════════════════════════
//  ARKA AI — Configuration
// ═══════════════════════════════════════

// AI Provider (currently: nvidia)
define('AI_PROVIDER', 'nvidia');

// NVIDIA NIM API Key
// Get yours free at: https://build.nvidia.com
define('NVIDIA_API_KEY', 'nvapi-xxxxxxxxxxxx');

// Default Model
define('NVIDIA_MODEL', 'qwen/qwen3.5-122b-a10b');

// Production Mode (switch to OpenRouter)
define('IS_PRODUCTION', false);

// Response Settings
define('MAX_TOKENS', 8192);
define('TEMPERATURE', 0.75);

// Rate Limiting
define('RATE_LIMIT_REQUESTS', 30);
define('RATE_LIMIT_WINDOW', 60);
?>
```

### Full Configuration Reference

| Constant | Default | Description |
|----------|---------|-------------|
| `AI_PROVIDER` | `'nvidia'` | Active AI provider |
| `NVIDIA_API_KEY` | `''` | NVIDIA NIM API key |
| `NVIDIA_MODEL` | `'qwen/qwen3.5-122b-a10b'` | AI model (122B params) |
| `SYSTEM_PROMPT` | *(heredoc)* | Arka's full personality |
| `REASONING_SYSTEM_PROMPT` | *(heredoc)* | Deep reasoning personality |
| `MAX_TOKENS` | `8192` | Max response length |
| `TEMPERATURE` | `0.75` | Creativity (0.0–1.0) |
| `RATE_LIMIT_REQUESTS` | `30` | Max req/window |
| `RATE_LIMIT_WINDOW` | `60` | Window in seconds |
| `HISTORY_DIR` | `./chat_history` | Backup storage |

---

## 🔑 The AI Model

Arka is powered by **`qwen/qwen3.5-122b-a10b`** via NVIDIA NIM:

```
┌──────────────────────────────────────────────┐
│  Qwen 3.5 — 122B Parameters                  │
│  ────────────────────────────                │
│  Architecture: Mixture of Experts (MoE)      │
│  Total params: 122 Billion                   │
│  Active params: 10 Billion per request       │
│  Result: Massive knowledge, fast responses   │
│                                              │
│  Vision: ✅ Image analysis supported         │
│  Reasoning: ✅ Extended thinking mode        │
│  Languages: ✅ Hindi, English, Hinglish      │
└──────────────────────────────────────────────┘
```

---

## 🔒 Privacy & Security

```
YOUR DATA LIVES HERE:
─────────────────────────────────────────────────
Browser localStorage  →  Your device only
                          We CANNOT see this

Firebase Auth         →  Only your Google UID
                          No conversations stored

NVIDIA API            →  Processes your message
                          Does NOT store it
─────────────────────────────────────────────────
```

### localStorage Keys Reference

| Key | Contents | Scope |
|-----|----------|-------|
| `arka_user` | Name, email, plan, joined date | Global |
| `arka_chats_{uid}` | All conversations | Per-user |
| `arka_profile_{uid}` | Adaptive personality data | Per-user |
| `arka_memory_{uid}` | Long-term memory entries | Per-user |
| `arka_image_usage_{uid}` | Daily image count + reset | Per-user |
| `arka_file_usage_{uid}` | Daily file count + reset | Per-user |
| `arka_reasoning_usage_{uid}` | Daily reasoning count | Per-user |
| `arka_settings_{uid}` | App preferences | Per-user |
| `arka-theme` | `dark` or `light` | Global |
| `arka_language` | Selected UI language | Global |

---

## ⌨️ Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Enter` | Send message |
| `Shift + Enter` | New line in message |
| `Ctrl + K` | New chat |
| `Ctrl + D` | Toggle dark/light mode |
| `Ctrl + ,` | Open settings |
| `Escape` | Close any modal or menu |

---

## 🗺️ Roadmap

```
PHASE 1 — Core ✅ COMPLETE
──────────────────────────
[x] Google Auth (Firebase)
[x] Multi-provider AI backend  
[x] Adaptive personality engine
[x] Chat history (star/rename/delete)
[x] Image analysis (upload/paste/drag)
[x] File analysis (PDF/docs/code)
[x] Deep reasoning toggle
[x] Memory system + import
[x] Free/Pro plan system
[x] Premium dark/light UI
[x] Settings (5-tab full page)
[x] Help center widget
[x] Language selector (12 languages)
[x] Mobile responsive UI
[x] Google Search Console setup
[x] AI SEO (llms.txt)
[x] Deployed at arka.vyomagroup.online

PHASE 2 — Growth 🚧 IN PROGRESS
─────────────────────────────────
[ ] NVIDIA API live testing
[ ] Pro plan payments (Razorpay)
[ ] Performance optimization
[ ] PWA mobile app
[ ] Web search integration

PHASE 3 — Agents 🔮 COMING SOON
─────────────────────────────────
[ ] 🧑‍⚖️  Legal Advisor Agent
[ ] 💰 Financial Advisor Agent
[ ] 🏥 Health Counselor Agent
[ ] 💼 Career Coach Agent
[ ] 🗺️  Mindmap generation
[ ] 🎤 Voice input/output
[ ] 📱 Mobile app (React Native)
[ ] ☁️  Cloud sync (Firebase Firestore)
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript (ES Modules) |
| **Backend** | PHP 8.0+ with cURL |
| **AI Model** | qwen/qwen3.5-122b-a10b via NVIDIA NIM |
| **Auth** | Firebase v12.11.0 (Google Sign-In) |
| **Storage** | Browser localStorage (client-side) |
| **Icons** | Custom SVG system (Lucide-style) |
| **Fonts** | Playfair Display + Inter (Google Fonts) |
| **Hosting** | Hostinger (PHP-compatible) |
| **Domain** | arka.vyomagroup.online |

---

## 🚀 Deployment Guide

### Local Development

```bash
cd arka
php -S localhost:8000
# Open: http://localhost:8000
```

### Hostinger Deployment

```
1. Upload all files via File Manager
   → public_html/ or subdomain root

2. Set API key in config.php
   → define('NVIDIA_API_KEY', 'your-key');

3. Add authorized domain in Firebase
   → console.firebase.google.com
   → Authentication → Settings
   → Authorized domains → Add domain
   → yourdomain.com

4. Verify HTTPS is active
   → Google Auth requires HTTPS

5. Submit sitemap to Google Search Console
   → search.google.com/search-console
```

### Firebase Setup (5 minutes)

```
1. Go to console.firebase.google.com
2. Create new project
3. Add web app (</> icon)
4. Select "Use a <script> tag"
5. Copy the firebaseConfig object
6. Paste into index.html (already configured)
7. Enable Google Authentication:
   Authentication → Sign-in method → Google → Enable
8. Add your domain to Authorized Domains
```

---

## 🔧 Troubleshooting

<details>
<summary><b>🔴 "Sorry, I encountered an error"</b></summary>

```
Cause 1: NVIDIA_API_KEY not set in config.php
Fix: Add your key from build.nvidia.com

Cause 2: Rate limit exceeded  
Fix: Wait 1-2 minutes and try again

Cause 3: Network issue
Fix: Check internet connection
```
</details>

<details>
<summary><b>🔴 Google login not working on Hostinger</b></summary>

```
Cause: Domain not in Firebase authorized list
Fix:
1. Go to console.firebase.google.com
2. Authentication → Settings → Authorized domains
3. Add your domain: yourdomain.com
4. Enable HTTPS on Hostinger
5. Use popup auth (not redirect) for shared hosting
```
</details>

<details>
<summary><b>🔴 Chat history not saving</b></summary>

```
Cause: localStorage blocked or private browsing
Fix: 
- Disable private/incognito mode
- Allow site storage in browser settings
- Check if localStorage is available:
  Open console → type: localStorage
```
</details>

<details>
<summary><b>🔴 Images not uploading</b></summary>

```
Cause 1: Daily limit reached (5/5)
Fix: Wait 24 hours or upgrade to Pro

Cause 2: File too large
Fix: Image must be under 10MB

Cause 3: Unsupported format
Fix: Use JPG, PNG, GIF, WebP, or BMP
```
</details>

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│                    USER BROWSER                      │
│  ┌─────────────┐  ┌──────────┐  ┌───────────────┐  │
│  │  index.html │  │ style.css│  │  script.js    │  │
│  │  (App UI)   │  │ (Styles) │  │  (Logic)      │  │
│  └──────┬──────┘  └──────────┘  └───────┬───────┘  │
│         │                               │           │
│         └───────────── XHR ────────────┘           │
│                         │                           │
│         localStorage ◄──┤                           │
│         (user data)      │                          │
└──────────────────────────┼──────────────────────────┘
                           │ POST /api.php
┌──────────────────────────┼──────────────────────────┐
│                PHP SERVER│                           │
│  ┌────────────────────── ▼ ─────────────────────┐   │
│  │              api.php                          │   │
│  │         (Request Router)                      │   │
│  │  ┌────────────────────────────────────────┐  │   │
│  │  │ config.php → SYSTEM_PROMPT             │  │   │
│  │  │            → REASONING_PROMPT          │  │   │
│  │  │            → Rate Limiter              │  │   │
│  │  └──────────────────┬─────────────────────┘  │   │
│  └─────────────────────┼────────────────────────┘   │
└────────────────────────┼────────────────────────────┘
                         │ HTTPS API Call
┌────────────────────────┼────────────────────────────┐
│              NVIDIA NIM│                             │
│  ┌───────────────────  ▼ ────────────────────────┐  │
│  │     qwen/qwen3.5-122b-a10b                    │  │
│  │     (122B params, 10B active — MoE)           │  │
│  │     Vision ✅  Reasoning ✅  Hindi ✅          │  │
│  └───────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────┘
```

---

## 📊 Usage Limits at a Glance

```
                 FREE PLAN        PRO PLAN
                 ─────────        ────────
Chat Messages    ∞ Unlimited      ∞ Unlimited
Images/day       ████░░ 5         ∞ Unlimited  
Files/day        ████░░ 5         ∞ Unlimited
Reasoning/day    ███░░░ 3         ∞ Unlimited
File size        ██░░░ 10MB       █████ 50MB
Reset time       ⏰ 24 hours      N/A
Price            ₹0 forever       ₹299/month
```

---

## 🌐 Live URLs

| Resource | URL |
|----------|-----|
| 🤖 Arka AI App | [arka.vyomagroup.online](https://arka.vyomagroup.online) |
| 🏠 Vyoma Group | [vyomagroup.online](https://vyomagroup.online) |
| 📚 Documentation | [vyomagroup.online/docs/](https://vyomagroup.online/docs/) |
| 📖 Blog | [vyomagroup.online/blog/](https://vyomagroup.online/blog/) |
| 📋 Guidelines | [vyomagroup.online/guidelines/](https://vyomagroup.online/guidelines/) |
| 🔄 Changelog | [vyomagroup.online/changelog/](https://vyomagroup.online/changelog/) |
| 🟢 Status | [vyomagroup.online/status/](https://vyomagroup.online/status/) |

---

## 📬 Contact & Support

| Channel | Address | Response |
|---------|---------|----------|
| 💬 Support | support@vyomagroup.online | < 48 hrs |
| 💼 Business | hello@vyomagroup.online | < 48 hrs |
| 🛡️ Safety | safety@vyomagroup.online | < 24 hrs |

---

## 🤝 Contributing

Arka AI is currently a closed-source project. However:

- 🐛 **Bug Reports** → Open an issue with full details
- 💡 **Feature Ideas** → Email hello@vyomagroup.online
- 📖 **Documentation** → PRs for docs improvements welcome

---

## 📄 License

```
MIT License

Copyright (c) 2026 Vyoma Group

Permission is hereby granted, free of charge, to any person 
obtaining a copy of this software and associated documentation 
files (the "Software"), to deal in the Software without 
restriction, including without limitation the rights to use, 
copy, modify, merge, publish, distribute, sublicense, and/or 
sell copies of the Software...

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.
```

---

<div align="center">

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  
  ✦  Built with passion in India, for the world  ✦

  Powered by NVIDIA NIM · Secured by Firebase
  
  © 2026 Vyoma Group · Intelligence for Everyone

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

[![Try Arka AI](https://img.shields.io/badge/Try_Arka_AI-Free_Forever-e8622a?style=for-the-badge&logo=sparkles&logoColor=white)](https://arka.vyomagroup.online)

*"The best AI is the one that feels like it was built just for you."*

</div>
