# 🤖 AI Personal Assistant

![n8n](https://img.shields.io/badge/n8n-automation-orange)
![WhatsApp](https://img.shields.io/badge/WhatsApp-integrated-25D366)
![Google Gemini](https://img.shields.io/badge/Google-Gemini%20AI-4285F4)

> An intelligent WhatsApp-based personal assistant powered by n8n automation and Google Gemini AI. Manage emails, calendar events, contacts, and research queries through natural language conversations.

---



## 🌟 Overview

This is a full-stack AI automation system that uses n8n workflows to create an intelligent personal assistant accessible via WhatsApp. The system takes text or voice messages, processes them through Google Gemini AI, and performs actions across multiple services including Gmail, Google Calendar, and web research. Built with a multi-agent architecture, each specialized sub-agent handles specific tasks while maintaining conversational context.

### ✨ Key Features

- 🗣️ **Voice & Text Input** - Send messages or voice notes via WhatsApp
- 🎙️ **Speech Recognition** - Automatic voice transcription using Google Gemini
- 🔊 **Voice Responses** - Text-to-speech conversion with ElevenLabs
- 📧 **Email Management** - Send and retrieve Gmail messages naturally
- 📅 **Calendar Control** - Create, update, and query Google Calendar events
- 📊 **Contact Database** - Search contacts from Google Sheets
- 🔍 **Web Research** - Real-time information from SerpAPI, Hacker News, Wikipedia
- 💬 **Conversational Memory** - Context-aware responses with history tracking
- 🤖 **Multi-Agent Architecture** - Specialized sub-agents for different tasks

---

## 🏗️ System Architecture

```
┌──────────────┐
│   WhatsApp   │ (User Interface)
│   Messages   │
└──────┬───────┘
       │
       ▼
┌─────────────────────────────────────────┐
│        Main AI Agent (Orchestrator)     │
│         Google Gemini + n8n             │
└─────────┬───────────────────────────────┘
          │
    ┌─────┴─────┬──────────┬──────────┐
    ▼           ▼          ▼          ▼
┌────────┐ ┌─────────┐ ┌────────┐ ┌──────────┐
│ Email  │ │Calendar │ │ Sheet  │ │Research  │
│ Agent  │ │  Agent  │ │ Lookup │ │  Agent   │
└────────┘ └─────────┘ └────────┘ └──────────┘
    │           │          │           │
    ▼           ▼          ▼           ▼
┌────────┐ ┌─────────┐ ┌────────┐ ┌──────────┐
│ Gmail  │ │ Google  │ │ Google │ │ SerpAPI  │
│  API   │ │Calendar │ │ Sheets │ │Wikipedia │
└────────┘ └─────────┘ └────────┘ └──────────┘
```

### Workflow Components

**Main Workflow:** `personal assistant`
- WhatsApp message receiver
- Voice transcription
- Intent analysis & routing
- Text-to-speech conversion
- Response delivery

**Sub-Agents:**
1. **Email Agent** - Gmail operations (send, retrieve, summarize)
2. **Calendar Agent** - Schedule management (create, update, query)
3. **Research Agent** - Web search and information retrieval

---

## 🚀 Getting Started

### Prerequisites

- n8n instance (self-hosted or cloud)
- WhatsApp Business account with API access
- Google Cloud Platform account with enabled APIs:
  - Gmail API
  - Google Calendar API
  - Google Sheets API
  - Google Gemini API
- ElevenLabs API account
- SerpAPI account

### Installation

1. **Clone the repository**
   ```bash
   git clone  https://github.com/ARMemon231/personal-ai-butler.git
   cd n8n-personal-assistant
   ```

2. **Install n8n** (if not already installed)
   ```bash
   npm install n8n -g
   ```

3. **Import workflows into n8n**
   - Open n8n dashboard
   - Go to **Workflows** → **Import**
   - Import each JSON file:
     - `main agent personal assistant.json`
     - `sub agent email agent.json`
     - `sub agent calender tool.json`
     - `sub agent reasearch agent.json`

4. **Configure credentials in n8n**
   
   Navigate to **Settings** → **Credentials** and add:
   
   - **WhatsApp API**
     - Phone Number ID
     - Access Token
     - Webhook verification token
   
   - **Google Gemini (PaLM) API**
     - API Key from Google AI Studio
   
   - **Gmail OAuth2**
     - Client ID
     - Client Secret
     - Authorize access
   
   - **Google Calendar OAuth2**
     - Client ID
     - Client Secret
     - Authorize access
   
   - **Google Sheets OAuth2**
     - Client ID
     - Client Secret
     - Authorize access
   
   - **ElevenLabs API**
     - API Key
     - Voice ID (Amelia recommended)
   
   - **SerpAPI**
     - API Key

5. **Update workflow settings**
   
   **WhatsApp Configuration:**
   - Update phone number ID in WhatsApp nodes
   - Set webhook URL in Meta Developer Console
   
   **Google Sheet:**
   - Update document ID: `1GHZPg1VJp127lxkmyKuNd4A0ZfRtid2_TgrHrrHJVKc`
   - Or create your own with columns: Name, Email
   
   **Calendar Settings:**
   - Update calendar ID (default: primary calendar)
   - Verify timezone: `Asia/Karachi` (PKT/UTC+5)

6. **Activate workflows**
   ```
   - Activate "personal assistant" (main workflow)
   - Sub-agents remain inactive (called by main workflow)
   ```

7. **Test the assistant**
   - Send a WhatsApp message to your configured number
   - Try: "Schedule a meeting tomorrow at 4 PM"

---

## 📖 User Preferences

**Preferred communication style:** Simple, everyday language.

The AI assistant communicates naturally and avoids technical jargon, making it accessible for everyday use.

---

## 💬 Usage Examples

### Email Operations
```
"Send email to ali@gmail.com about the meeting"
"Get my last 5 emails from Google"
"Summarize recent emails from Sarah"
"Email John to remind him about tomorrow's call"
```

### Calendar Management
```
"Schedule a meeting tomorrow at 4 PM with Ahmed"
"What's on my calendar today?"
"Move my 10 AM meeting to 2 PM next Friday"
"Cancel my 3 PM appointment"
"Do I have any meetings on Monday?"
```

### Contact Lookup
```
"Get email address for Sarah"
"Find contact info for Ali"
"Who is John Smith?"
```

### Web Research
```
"Who is the founder of Reddit?"
"Latest news on artificial intelligence"
"Search for information about quantum computing"
"What's the weather forecast?"
```

### Voice Interaction
- Send a voice note via WhatsApp
- Assistant transcribes your message
- Processes the request
- Responds with a voice message

---

## 🛠️ Technology Stack

### Automation Platform
- **n8n** - Workflow automation and orchestration

### AI & Machine Learning
- **Google Gemini 2.5 Flash Lite** - Language model for intent analysis
- **ElevenLabs** - Natural text-to-speech conversion

### Communication
- **WhatsApp Business API** - Messaging interface
- **WhatsApp Webhook** - Real-time message receiving

### Google Services
- **Gmail API** - Email operations
- **Google Calendar API** - Event management
- **Google Sheets API** - Contact database

### Research Tools
- **SerpAPI** - Web search capabilities
- **Hacker News API** - Tech news aggregation
- **Wikipedia API** - Factual information retrieval

---

## 📁 Project Structure

```
n8n-personal-assistant/
├── main agent personal assistant.json    # Main orchestrator workflow
├── sub agent email agent.json            # Gmail operations
├── sub agent calender tool.json          # Calendar management
├── sub agent reasearch agent.json        # Web research
├── n8n demo.mp4                          # Demo video
├── n8n personal assistant demo.png       # Screenshot
├── voiceover_script.md                   # Demo narration script
├── README.md                             # This file
├── .gitignore                            # Git ignore rules
└── LICENSE                               # MIT License
```

---

## 🔧 Configuration Details

### WhatsApp Setup

1. **Create WhatsApp Business Account**
   - Visit [Meta for Developers](https://developers.facebook.com/)
   - Create an app with WhatsApp product
   - Get Phone Number ID and Access Token

2. **Configure Webhook**
   ```
   Webhook URL: https://your-n8n-instance.com/webhook/whatsapp
   Verify Token: your_custom_token
   Subscribe to: messages
   ```

3. **Update Workflow Nodes**
   - WhatsApp Trigger: Add webhook credentials
   - Send Message nodes: Update Phone Number ID

### Google Sheet Contact Database

**Sheet Structure:**
| Name  | Email                | Phone          | Notes        |
|-------|---------------------|----------------|--------------|
| Ali   | ali@example.com     | +92-XXX-XXXX  | Team member  |
| Sarah | sarah@example.com   | +92-XXX-XXXX  | Manager      |

**Update in Workflow:**
```javascript
Document ID: 1GHZPg1VJp127lxkmyKuNd4A0ZfRtid2_TgrHrrHJVKc
Sheet Name: 20 recods in google sheet with name,email...
```

### Timezone Configuration

Calendar agent uses **Pakistan Standard Time (PKT, UTC+5)**.

To change timezone:
1. Open `sub agent calender tool.json`
2. Find system prompt
3. Replace `Asia/Karachi` with your timezone
4. Update UTC offset (e.g., `+05:00`)

---

## 🧠 How It Works

### Complete Workflow Process

1. **Message Reception**
   - User sends text/voice to WhatsApp
   - WhatsApp Trigger captures message
   - Switch node routes based on type

2. **Voice Processing** (if voice message)
   - Download media via HTTP Request
   - Transcribe using Google Gemini audio API
   - Convert to text format

3. **Intent Analysis**
   - Main AI Agent receives text
   - Analyzes user intent with context
   - Determines required action

4. **Tool Selection & Execution**
   - Email queries → Email Agent
   - Calendar requests → Calendar Agent
   - Contact lookup → Google Sheets
   - Information needs → Research Agent

5. **Response Generation**
   - Sub-agent completes task
   - Returns result to main agent
   - Summarization chain processes output

6. **Voice Response** (optional)
   - Convert text to speech (ElevenLabs)
   - Extract audio file
   - Convert to WhatsApp format

7. **Delivery**
   - Send text or voice message
   - User receives response on WhatsApp

### Memory System

The assistant maintains conversation context:
- Buffer window memory stores recent exchanges
- Session key based on user ID
- Enables multi-turn conversations
- Remembers previous requests

---

## 🔐 Security & Privacy

### Best Practices

- ✅ Store all API keys in n8n credentials (encrypted)
- ✅ Use OAuth2 for Google services
- ✅ Enable webhook verification for WhatsApp
- ✅ Regularly rotate API tokens
- ✅ Review access permissions periodically
- ✅ Use environment variables for sensitive data
- ✅ Implement rate limiting on webhooks
- ⚠️ Never commit credentials to Git

### Data Privacy

- User conversations are not stored permanently
- Memory buffer has configurable retention
- Google Sheets contains only provided contacts
- No data shared with third parties
- Complies with WhatsApp Business policies

---

## 🐛 Troubleshooting

### Common Issues

**1. Voice transcription fails**
```
Problem: Audio not transcribed
Solution:
- Verify Gemini API key is valid
- Check audio format (should be OGG/OPUS)
- Ensure file size under 10MB
- Check n8n logs for errors
```

**2. Calendar events show wrong time**
```
Problem: Events created in wrong timezone
Solution:
- Verify timezone in calendar agent: Asia/Karachi
- Check system timezone on n8n server
- Ensure datetime format includes UTC offset
```

**3. Email sending fails**
```
Problem: Gmail API errors
Solution:
- Confirm OAuth2 credentials are authorized
- Check Gmail API is enabled in Google Cloud
- Verify email format is correct
- Check sender permissions in Gmail
```

**4. WhatsApp messages not received**
```
Problem: Webhook not triggering
Solution:
- Verify webhook URL is accessible
- Check SSL certificate is valid
- Confirm subscription in Meta Dashboard
- Review n8n execution logs
```

**5. Sub-agent not responding**
```
Problem: Tool calls timing out
Solution:
- Check sub-workflow is saved (not just active)
- Verify workflow IDs match in tool nodes
- Check API rate limits not exceeded
- Review sub-agent execution logs
```

---

## 📊 Workflow Details

### Main Agent System Prompt

The main agent uses intelligent routing logic:

```
- Calendar terms → calenderagent
- Email keywords → emailagent
- Contact lookup → sheet (Google Sheets)
- General queries → reasearch agent
- Chat messages → Natural response
```

**Email Name Resolution:**
1. User mentions name in email request
2. System searches Google Sheets first
3. If found → Use email address
4. If not found → Ask user for email

### Sub-Agent Capabilities

**Email Agent:**
- Send emails with auto-generated subjects
- Search by sender, date, keywords
- Retrieve last N emails
- Generate summaries of inbox

**Calendar Agent:**
- Two-step flow: parse date → execute action
- Natural language date parsing
- Create/update/delete events
- List upcoming appointments
- Timezone-aware (PKT default)

**Research Agent:**
- SerpAPI: Web search results
- Hacker News: Tech news and discussions
- Wikipedia: Factual encyclopedic data
- Combines multiple sources

---



### Add New Sub-Agen

1. Create new workflow in n8n
2. Add "Execute Workflow Trigger"
3. Build your agent logic
4. Add Tool: Workflow node in main agent
5. Update system prompt with tool description

### Modify Voice Settings

Change ElevenLabs voice:
```json
{
  "voice": {
    "value": "VOICE_ID_HERE"
  }
}
```

Popular voices:
- Amelia: Young and enthusiastic
- Adam: Deep and authoritative
- Bella: Friendly and warm

---

## 📈 Performance Optimization

### Tips for Better Performance

1. **Reduce Voice Processing Time**
   - Use streaming for audio responses
   - Cache common responses
   - Optimize audio quality settings

2. **Minimize API Calls**
   - Batch operations where possible
   - Use result caching
   - Implement request queuing

3. **Improve Response Time**
   - Use async execution
   - Optimize workflow logic
   - Reduce unnecessary nodes

4. **Handle Rate Limits**
   - Implement exponential backoff
   - Queue requests during high load
   - Monitor API quotas

---

## 📋 Roadmap

- [ ] Add SMS integration (Twilio)
- [ ] Support multiple languages
- [ ] Integrate with Slack/Discord
- [ ] Add database for persistent storage
- [ ] Implement user authentication
- [ ] Create mobile app frontend
- [ ] Add Telegram bot integration
- [ ] Support for file attachments
- [ ] Advanced analytics dashboard
- [ ] Multi-user support
- [ ] Custom voice training
- [ ] Integration with CRM systems

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/AmazingFeature
   ```
3. **Make your changes**
4. **Test thoroughly**
5. **Commit your changes**
   ```bash
   git commit -m 'Add some AmazingFeature'
   ```
6. **Push to the branch**
   ```bash
   git push origin feature/AmazingFeature
   ```
7. **Open a Pull Request**

### Contribution Guidelines

- Follow existing code structure
- Test all workflows before submitting
- Update documentation for new features
- Add comments for complex logic
- Ensure credentials are not committed

---



## 👤 Author

**Your Name**
- GitHub:    [https://github.com/ARMemon231]
- LinkedIn:  [https://www.linkedin.com/in/armemon225]
- Email:     [armemon695@gmail.com]

---

## 🙏 Acknowledgments

- **n8n Community** - Amazing automation platform
- **Google Gemini Team** - Powerful AI capabilities
- **ElevenLabs** - Natural voice synthesis
- **WhatsApp Business** - Reliable messaging platform
- **Open Source Community** - Inspiration and support

Special thanks to all contributors and users who have helped improve this project!

---


### Resources

- [n8n Documentation](https://docs.n8n.io/)
- [WhatsApp Business API Docs](https://developers.facebook.com/docs/whatsapp)
- [Google Gemini API Guide](https://aistudio.google.com/)
- [ElevenLabs Voice Library](https://elevenlabs.io/voices)

---

## ⭐ Show Your Support

If you find this project helpful, please consider:

- ⭐ Starring the repository
- 🍴 Forking for your own projects
- 📢 Sharing with others
- 💬 Providing feedback
- 🐛 Reporting issues
- 🔧 Contributing improvements

---

<div align="center">

**Made with ❤️ using n8n, Google Gemini AI, and lots of ☕**

[⬆ Back to Top](#-ai-personal-assistant)

</div>
