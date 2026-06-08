# AI Job Application Tracker 🤖

An automated job tracking system built with n8n and Claude AI that finds remote jobs, scores them for fit, drafts personalized outreach, and delivers a daily email digest — completely on autopilot.

---

## What It Does

- Fetches remote job listings from We Work Remotely every 6 hours
- Uses Claude AI to score each job for fit (1–10) based on my skills and background
- Uses Claude AI to draft a personalized outreach message for each role
- Logs every job with score, reason, and outreach draft to Google Sheets
- Sends a daily email digest every morning with the top new matches

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation (self-hosted) |
| Claude AI (claude-sonnet-4-6) | Job scoring + outreach drafting |
| We Work Remotely RSS | Job data source |
| Google Sheets | Job tracking database |
| Gmail SMTP | Daily digest delivery |

---

## Workflow Architecture

### Workflow 1 — Job Fetcher (runs every 6 hours)
```
Schedule Trigger
→ HTTP Request (We Work Remotely RSS)
→ XML Parser
→ Code Node (extract top 10 jobs)
→ Loop Over Items
  → Claude AI (score job 1-10)
  → Claude AI (draft outreach message)
  → Google Sheets (append row)
```

### Workflow 2 — Daily Digest (runs at 8am daily)
```
Schedule Trigger
→ Google Sheets (get new jobs)
→ Code Node (build HTML email)
→ Send Email (Gmail SMTP)
```

---

## Google Sheets Structure

| Column | Description |
|--------|-------------|
| Job ID | Unique identifier (job URL) |
| Job Title | Role name |
| Company | Hiring company |
| Location | Remote / region |
| URL | Direct link to job posting |
| Date Found | Timestamp when logged |
| Fit Score | Claude AI score (1-10) |
| Score Reason | Why Claude scored it that way |
| Outreach Draft | Ready-to-send connection message |
| Status | New / Applied / Rejected |

---

## Setup Instructions

### Prerequisites
- n8n (self-hosted or cloud)
- Anthropic API key
- Google Cloud project with Sheets + Drive APIs enabled
- Gmail account with App Password enabled

### Step 1: Google Sheets
1. Create a spreadsheet named `AI Job Tracker`
2. Add two sheets: `Jobs` and `Config`
3. Set up columns as shown in the table above

### Step 2: Google Service Account
1. Create a Service Account in Google Cloud Console
2. Enable Google Sheets API and Google Drive API
3. Download the JSON key file
4. Share the spreadsheet with the service account email (Editor access)

### Step 3: n8n Credentials
- **Google Sheets:** Service Account (paste JSON key)
- **Gmail:** SMTP with App Password (smtp.gmail.com, port 587)
- **Claude API:** HTTP Request headers (x-api-key + anthropic-version)

### Step 4: Import Workflows
1. Download the workflow JSON files from this repo
2. In n8n: New Workflow → Import from file
3. Update all credentials to your own
4. Set your Spreadsheet ID in the Google Sheets nodes
5. Activate both workflows

---

## Sample Output

**Google Sheets row example:**
```
Job Title:    Senior Automation Engineer
Company:      Acme Corp
Fit Score:    8
Score Reason: Strong match — requires n8n and API integration experience
Outreach:     Hi [Name], I came across the Automation Engineer role at Acme Corp...
Status:       New
```

---

## What I Learned

- Connecting APIs in n8n using HTTP Request nodes with custom headers
- Parsing XML RSS feeds into structured JSON data
- Using Claude AI inside automation workflows for intelligent scoring
- Service Account authentication for Google Sheets (no OAuth needed)
- Building HTML email templates inside n8n Code nodes

---

## Week 3 of Building in Public

This is Week 3 of my journey transitioning into No-Code / Low-Code AI Automation Engineering.

- **Week 1:** LinkedIn post ideas AI workflow
- **Week 2:** LinkedIn post generator with webhook
- **Week 3:** AI Job Application Tracker (this project)

Follow my journey on [LinkedIn](https://linkedin.com/in/your-profile) | [GitHub](https://github.com/your-username)

---

## Author

**Kashish Trivedi**  
AI Automation Builder | Career Shifter  
Building in public — one workflow at a time.

---

*Built with n8n + Claude AI by Kashish Trivedi*
