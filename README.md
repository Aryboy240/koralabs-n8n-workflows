# koralabs-n8n-workflows

My personal automation suite using agentic AI and workflows built with n8n. This repository contains various automation workflows that I've built to streamline daily tasks and enhance productivity.

## 📁 Workflows

### Job Scraper 🎯

A powerful automated job application pipeline that scrapes job listings, analyzes them for compatibility with your profile, generates cover letters, and scores opportunities.

**Features:**
- 🤖 AI-powered job analysis and scoring
- ✍️ Automatic cover letter generation
- 📊 Smart job filtering (Junior/Graduate roles)
- 🔍 Skills extraction from job descriptions
- 📈 Compatibility scoring (0-5 scale)
- 📝 Job summarization
- 💬 Discord notifications for new matches
- 📅 Automated scheduling (weekly)
- 🚀 Enhanced AI capabilities
- ⏳ Rate limit prevention for web scraping

**Workflow Overview:**

The Job Scraper workflow runs on a schedule (every week) and:

1. **Clear Sheet** - Prepares the Google Sheets spreadsheet for new data
2. **CV** - Stores your CV information for AI processing
3. **CV Skills** - Extracts all technical skills from your CV
4. **J*b Scraper** - Scrapes jobs from multiple platforms
5. **Split Out** - Organizes job data
6. **Graduate/Junior Filter** - Filters for suitable roles
7. **Remove Duplicates** - Ensures unique job listings
8. **Job Description** - Summarizes each job role (2-3 sentences)
9. **Job Skills** - Extracts required skills from job descriptions
10. **Send Job Skills** - Splits data for parallel processing
11. **Cover Letter** - Generates tailored cover letters for each job
12. **Job Scoring** - AI compatibility scoring (0-5)
13. **Loop & Aggregate** - Processes all jobs and prepares output
14. **Wait** - Delays between job processing
15. **Job Sheet** - Appends jobs to Google Sheets
16. **Discord** - Sends notifications for new matches

**Integration with AI Services:**
- **Ollama** - Local LLM for CV skills extraction, job summarization, and cover letter generation
- **Groq API** - Fast language model for job scoring
- **Apify** - Web scraping capabilities
- **Google Sheets** - Data storage and tracking
- **Discord** - Real-time notifications

**Workflow Diagram:**

```
Schedule Trigger → Clear Sheet → CV → CV Skills → Job Scraper → Split Out → Graduate/Junior Filter → Remove Duplicates → Job Description → Job Skills
          ↓                                                          ↓
        CV Skills -------------------------------------------------> Send Job Skills → Cover Letter → Job Scoring → Wait for Response → Send Job Skills → Loop → Aggregate → Discord → Wait → Job Sheet
```

**Screenshots:**

![Job Scraper Workflow Part 1](Screenshots/Job%20scraper/Workflow%201.png)

![Job Scraper Workflow Part 2](Screenshots/Job%20scraper/Workflow%202.png)

![Job Scraper Workflow Part 3](Screenshots/Job%20scraper/Workflow%203.png)

![Job Scraper Workflow Part 4](Screenshots/Job%20scraper/Workflow%204.png)

![Job Scraper full Workflow](Screenshots/Job%20scraper/Entire%20Job%20Scraper%20workflow.png)

![Job Scraper Google Sheets](Screenshots/Job%20scraper/Job%20Scraper%20Google%20Sheets.png)

![Discord Updates](Screenshots/Job%20scraper/Discord%20updates.png)

**Prerequisites:**
- n8n instance (self-hosted or cloud)
- Google Sheets account with OAuth credentials
- Discord webhook for notifications
- Apify account
- Ollama account (for local LLM)
- Groq API account
- CV stored in the workflow

**Setup Instructions:**
1. Import the `Job Scraper/Job Scraper Workflow.json` file into your n8n instance
2. Configure credentials for Google Sheets, Discord, Apify, Ollama, and Groq
3. Update the schedule trigger to match your preferences
4. Enter your CV data in the "CV" node
5. Add your CV to n8n as a credential or node
6. Activate the workflow

**Output:**
- Google Sheet with analyzed jobs, summaries, cover letters, and scores
- Discord notifications for high-scoring matches

---

### Gmail Labels 📧

An intelligent email automation workflow that automatically categorizes, labels, and can respond to your incoming emails using AI.

**Features:**
- 🤖 AI-powered email categorization (7 categories)
- 🏷️ Automatic Gmail label assignment
- ⏰ Real-time monitoring (every minute)
- ✍️ AI-generated reply drafts for important emails
- 📩 Smart email filtering and organization
- 📧 Multiple label support (Promotions, Social, Security, Jobs, Orders, Personal, Misc)
- 📝 Professional email response generation

**Workflow Overview:**

The Gmail Labels workflow runs on a schedule (every minute) and:

1. **Gmail Trigger** - Monitors for unread emails
2. **Email Categoriser** - Uses Ollama to classify emails into categories
3. **Switch** - Routes emails based on category
4. **Label Assignment** - Adds appropriate labels to each email:
   - **Promotions** - Marketing emails, offers, discounts
   - **Social** - Social platform notifications
   - **Misc** - Anything that doesn't fit other categories
   - **Security** - Password resets, login alerts, 2FA
   - **J*b** - Job application related emails
   - **Orders** - E-commerce and shipping notifications
   - **Personal** - Time-sensitive emails requiring attention
5. **Mark as Read** - Marks emails as processed
6. **Email Responder** - For "Personal" emails, generates professional reply drafts
7. **Create Draft** - Saves AI-generated replies as drafts

**Integration with AI Services:**
- **Ollama** - Email categorization and reply generation
- **Gmail** - Email fetching, labeling, and drafting
- **n8n** - Workflow orchestration and automation

**Workflow Diagram:**

```
Gmail Trigger (poll every minute) → Email Categoriser (AI) → Switch (7 categories)
                                                    ↓
            Promotions → Mark as Read          Social → Mark as Read
            Security → Mark as Read            Misc → Mark as Read
            J*b → Mark as Read                  Orders → Mark as Read
            Personal → Email Responder (AI) → Create Draft
```

**Screenshots:**

![Gmail Labels Workflow](Screenshots/Gmail%20Labeler/Gmail%20Labeler.png)

![Gmail Labels Workflow](Screenshots/Gmail%20Labeler/Labels.png)

**Prerequisites:**
- n8n instance (self-hosted or cloud)
- Gmail account with OAuth2 credentials
- Ollama account (for AI processing)

**Setup Instructions:**
1. Import the `Automatic Gmail Labeler/Gmail Labels Workflow.json` file into your n8n instance
2. Configure Gmail OAuth2 credentials
3. Configure Ollama API credentials
4. Activate the workflow
5. Monitor your email automation in real-time

**Categories:**
- **Promotions**: Marketing emails, offers, discounts, sales blasts
- **Socials**: Notifications from social platforms (YouTube, Instagram, Facebook, LinkedIn, etc.)
- **Personal**: Emails requiring attention, time-sensitive, or from real people
- **Orders**: E-commerce emails (order confirmations, shipping, returns, tracking, receipts)
- **Security**: Password resets, login alerts, 2FA, account verification, suspicious activity
- **Jobs**: Job applications, interview invites, rejections, recruiter responses
- **Misc**: Anything that doesn't clearly fit the above categories

**Output:**
- Automatically labeled emails in your Gmail inbox
- Draft replies for important/personal emails
- Organized email inbox for better productivity

---

### JARVIS 🤖

**Features:**
- 📞 Telegram-powered voice messaging (yes, it hears you)
- 🎙️ Whisper AI for voice-to-text transcription
- 📧 Gmail mastery (send, reply, label, find emails)
- 📅 Google Calendar domination (create, find, delete events)
- 💬 Discord messaging integration
- 🧠 Memory-enhanced conversation context
- 🎯 Intelligent task delegation
- 🚀 Multi-agent orchestration system
- ⚡ Ultra-fast Groq-powered responses
- 🔍 Advanced job matching with score filtering (4+ matches)
- 📤 Discord message sending and deletion capabilities

**Workflow Overview:**

```
Telegram Message (Voice/Text)
         ↓
┌─────────────────────────────────────────────────┐
│         JARVIS - The Decision Master            │
│  "I understand you want to do X. Let me delegate" │
└─────────────────────────────────────────────────┘
         ↓
    ┌────┴────┬───────────┬─────┐
    ↓         ↓           ↓     ↓
Gmail    Calendar    Voice    AI
Agent    Assistant   Processing  Model
```

**New Features:**
- 🔍 **Job Matching Filter**: Ask JARVIS for jobs with a match score of 4+ from your CV
- 💬 **Enhanced Discord Integration**: Send and delete messages directly from JARVIS

**JARVIS's Multi-Agent System:**

1. **Main JARVIS Agent** - The mastermind that analyzes your requests and delegates to the right specialist
2. **Gmail Agent** - Handles all email operations:
   - 📤 Send emails with Google Contacts integration
   - 🔍 Find/search emails with advanced filters
   - ✉️ Reply to existing emails
   - 🏷️ Label emails with custom categories
3. **Calendar Agent** - Manages your schedule:
   - ➕ Create events with conflict detection
   - 🔎 Find/search events by date/time
   - 🗑️ Delete unwanted events
4. **Discord Agent** - Sends messages through to Discord (can be replaced with other social media platforms):
5. **Voice Processing** - If you send a voice message:
   - 📥 Download and convert audio files
   - 🔊 Whisper AI transcription
   - 🧠 Integrate with main AI

**Integration with AI Services:**
- **Groq API** - Ultra-fast GPT-oss-120b language model
- **Whisper (OpenAI)** - Voice-to-text transcription
- **Telegram Bot API** - Message receiving and sending
- **Gmail API** - Email management
- **Google Calendar API** - Event management
- **Google Contacts API** - Contact lookup
- **n8n AI Agents** - Multi-agent orchestration
- **n8n Memory Buffer** - Context-aware conversation

**Voice Message Support:**

JARVIS understands you when you're too lazy to type:
1. Send a voice message via Telegram
2. He'll download, transcribe, and process it
3. Responds with text (sorry, no synthesized Jarvis voice yet)
4. Maintains conversation context from previous messages

**Agent Delegation Rules:**

JARVIS knows when to delegate and when to handle things itself:
- ✅ **Delegates to Gmail Agent** - Email sending, replying, finding, labeling
- ✅ **Delegates to Calendar Agent** - Event creation, management, deletion
- 🤖 **Handles directly** - Voice processing, system intelligence
- ❌ **Never duplicates work** - Critical rule!

**Setup Instructions:**
1. Import the `Agentic AI Assistant/AI Agent JARVIS.json` file into your n8n instance
2. Configure Telegram Bot credentials (get a token from @BotFather)
3. Configure Gmail OAuth2 credentials
4. Configure Google Calendar OAuth2 credentials
5. Configure Google Contacts OAuth2 credentials
6. Configure Groq API credentials
7. Configure Whisper API (OpenAI) for voice processing
8. Configure Discord webhook for message sending and deletion
9. Activate the workflow
10. Start chatting with your AI assistant

**Usage Examples:**

```
You: "Send an email to my mom about dinner on Friday"
JARVIS: *Sends email to mom@example.com about dinner Friday*

You: "Book a meeting with Sarah next Tuesday at 2pm"
JARVIS: *Checks calendar, confirms no conflicts, creates event*

You: [Sends voice message: "Reply to that email about the job offer"]
JARVIS: *Transcribes voice, replies to email with professional response*

```

**Screenshots:**

![JARVIS Workflow](Screenshots/JARVIS/JARVIS%20Workflow.png)

![Recommended Jobs Workflow](Screenshots/JARVIS/Recommending%20subworkflow.png)

![Telegram Prompt 1](Screenshots/JARVIS/Jobs.png)

![Telegram Prompt 2](Screenshots/JARVIS/Calendar.png)

![Telegram Prompt 2](Screenshots/JARVIS/Discord.png)

![Telegram Prompt 2](Screenshots/JARVIS/Email.png)

**Tech Stack:**
- **AI Framework:** n8n LangChain Agents
- **LLM:** Groq GPT-oss-120b (120B parameter model!)
- **Voice Recognition:** OpenAI Whisper Large V3
- **Communication:** Telegram Bot API
- **Memory Management:** BufferWindow with 10-turn context
- **OAuth Providers:** Gmail, Google Calendar, Google Contacts

**Note:** If you're ever stuck in a cave with a box of scraps and need help, this workflow isn't guaranteed to help. But it will definitely help you manage your emails and schedule. That's something, right? 😄

---

## 🛠️ Technologies Used

- **n8n** - Workflow automation platform
- **Ollama** - Local LLM inference
- **Groq API** - Fast language model processing
- **Apify** - Web scraping services
- **Google Sheets** - Data management
- **Discord** - Notifications

## 📚 n8n Documentation

n8n is an open-source workflow automation tool that lets you connect different services and automate tasks. Key features include:

- **Visual Workflow Builder** - Drag and drop interface
- **200+ Integrations** - Connect with popular apps and services
- **AI/LLM Nodes** - Native support for language models
- **Custom Functions** - JavaScript execution
- **Webhooks** - Trigger workflows from external sources
- **Split in Batches** - Process large datasets efficiently
- **Aggregate Node** - Combine processed items
- **Error Handling** - Retry logic and error nodes

**Official Documentation:**
- [n8n Documentation](https://docs.n8n.io)
- [n8n Community](https://community.n8n.io)

**Getting Started with n8n:**
1. Install n8n via Docker: `docker run -it --rm --name n8n -p 5678:5678 -v ~/.n8n:/home/node/.n8n n8nio/n8n`
2. Access the web interface at `http://localhost:5678`
3. Import workflows from JSON files
4. Configure credentials and integrations
5. Activate workflows and monitor execution

## 🚀 Contributing

Feel free to fork this repository and modify the workflows to suit your needs. Contributions and improvements are welcome!

## 📄 License

This repository is provided as-is for personal automation purposes.

## 👤 Author

**Aryan Kora**
- Linktree: [https://linktr.ee/AryanKora](https://linktr.ee/AryanKora)
- Contact: Aryan240@outlook.com

---

## 🔗 Useful Resources

- [n8n GitHub](https://github.com/n8n-io/n8n)
- [n8n Tutorials](https://www.youtube.com/c/n8nIO)
- [Apify Documentation](https://apify.com/docs)
- [Ollama Documentation](https://ollama.ai)
- [Groq API Docs](https://groq.com/docs)

---

*Note: This repository contains personal automation workflows. Always ensure you comply with the Terms of Service of the platforms you're integrating with.*
