# Automatic Gmail Labeler Setup Instructions

## Prerequisites
- n8n instance (self-hosted or cloud)
- Gmail account with OAuth2 credentials
- Ollama account (for AI processing)
- Groq API key (for fast AI processing)

## Installation Steps

1. **Import the Workflow**
   - Open your n8n instance
   - Go to "Workflows" → "Import"
   - Import the `Gmail Labels Workflow.json` file from this directory

2. **Configure Credentials**
   - Navigate to "Credentials" in n8n
   - Create credentials for:
     * Gmail OAuth2
     * Ollama API

3. **Configure the Workflow**
   - Open the imported Gmail Labels workflow
   - Update nodes with your credentials:
     * Gmail nodes
     * Ollama API node
     * Groq API node
   - Set up any additional configuration in the appropriate nodes

4. **Activate Workflow**
   - Click "Publish" button to enable the workflow

5. **Test the Integration**
   - Send test emails to your Gmail account
   - Verify that emails are automatically categorized and labeled
   - Check that reply drafts are created for "Personal" category emails
   - Confirm that email filtering works correctly

## Usage Notes
- The workflow runs on a schedule (every minute) by default
- Emails are automatically categorized into 7 categories:
  * Promotions (marketing emails, offers, discounts)
  * Social (social platform notifications)
  * Security (password resets, login alerts, 2FA)
  * Jobs (job application related emails)
  * Orders (e-commerce and shipping notifications)
  * Personal (time-sensitive emails requiring attention)
  * Misc (anything that doesn't fit other categories)
- AI-generated reply drafts are created for "Personal" category emails
- All email processing is handled automatically without manual intervention