# Job Scraper Setup Instructions

## Prerequisites
- n8n instance (self-hosted or cloud)
- Google Sheets account with OAuth2 credentials
- Discord webhook URL for notifications
- Apify account (for web scraping)
- Ollama account (for local LLM processing)
- Groq API account (for fast AI processing)
- CV stored in the workflow

## Installation Steps

1. **Import the Workflow**
   - Open your n8n instance
   - Go to "Workflows" → "Import"
   - Import the `J_b Scraper.json` file from this directory

2. **Configure Credentials**
   - Navigate to "Credentials" in n8n
   - Create credentials for:
     * Google Sheets OAuth2
     * Discord Webhook URL
     * Apify API
     * Ollama API
     * Groq API

3. **Configure the Workflow**
   - Open the imported Job Scraper workflow
   - Update nodes with your credentials:
     * Google Sheets nodes
     * Discord webhook node
     * Apify API node
     * Ollama API node
     * Groq API node
   - Enter your CV data in the "CV" node
   - Configure any additional settings in the appropriate nodes

4. **Activate Workflow**
   - Click "Publish" button to enable the workflow

5. **Test the Integration**
   - Verify that the workflow runs on schedule (weekly by default)
   - Check that job listings are scraped from multiple platforms
   - Confirm that jobs are filtered for Junior/Graduate roles
   - Validate that job summaries, skills, and cover letters are generated
   - Test Discord notifications for new high-scoring matches
   - Ensure job data is properly appended to your Google Sheets

## Usage Notes
- The workflow runs on a schedule (weekly by default)
- Job listings are scraped from multiple platforms using Apify
- AI-powered job analysis and scoring (0-5 scale)
- Automatic cover letter generation for each job
- Discord notifications for new high-scoring matches (4+ score)
- Jobs are filtered for Junior/Graduate roles by default
- Rate limit prevention built into the web scraping process
- Enhanced AI capabilities for better job matching