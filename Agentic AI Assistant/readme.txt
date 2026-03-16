# JARVIS AI Assistant Setup Instructions

## Prerequisites
- n8n instance (self-hosted or cloud)
- Telegram account with a bot token from @BotFather
- Gmail account with OAuth2 credentials
- Google Calendar account with OAuth2 credentials
- Google Contacts account with OAuth2 credentials
- Groq API key for fast AI processing
- OpenAI API key for Whisper voice transcription
- Discord webhook URL for message sending and deletion

## Installation Steps

1. **Import the Workflow**
   - Open your n8n instance
   - Go to "Workflows" → "Import"
   - Import the `JARVIS.json` file from this directory

2. **Configure Credentials**
   - Navigate to "Credentials" in n8n
   - Create credentials for:
     * Telegram Bot API (get token from @BotFather)
     * Gmail OAuth2
     * Google Calendar OAuth2
     * Google Contacts OAuth2
     * Groq API
     * OpenAI API (for Whisper)
     * Discord Webhook URL/bot auth

3. **Configure the Workflow**
   - Open the imported JARVIS workflow
   - Update nodes with your credentials:
     * Telegram Bot node
     * Gmail nodes
     * Google Calendar nodes
     * Groq API node
     * Discord webhook node
   - Set up your CV information in the appropriate nodes

4. **Activate Workflow**
   - Click "Publish" button to enable the workflow

5. **Test the Integration**
   - Send a test message to your Telegram bot
   - Verify that JARVIS responds appropriately
   - Check that email and calendar functions work correctly
   - Test Discord integration for sending/receiving messages

## Usage Notes
- JARVIS will automatically respond to Telegram messages
- Voice messages are transcribed using Whisper AI
- Email functions are handled by the Gmail Agent
- Calendar functions are managed by the Calendar Agent
- Discord integration allows sending and deleting messages directly from JARVIS