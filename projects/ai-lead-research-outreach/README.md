# 🤖 AI Lead Research + LinkedIn Outreach Assistant (n8n + AI)

## 📌 Overview

Built an AI-powered lead research and personalized outreach workflow using n8n.

This automation helps sales, partnerships, and growth teams research target companies, identify relevant outreach opportunities, generate personalized LinkedIn messages, and save everything into a structured tracker.

The goal was to create a practical AI workflow that reduces manual research time while improving outreach quality.

---

## ⚙️ Workflow Architecture

text Lead Input (Company + Website + Target Role)         
↓ 
AI researches company         
↓ 
AI summarizes company + industry         
↓ 
AI identifies outreach angle         
↓ 
AI generates personalized LinkedIn message         
↓ 
Save results to Google Sheets         
↓ 
Track outreach status 

---

## 🔍 Workflow 1 — AI Lead Research

### Purpose

Research target companies automatically.

### Input

- Company name
- Website
- Target role

### AI returns

- company summary
- industry
- likely business goals
- possible outreach angle

### Example

Input:

text Tradeify tradeify.com Head of Partnerships 

Output:

text Company Summary: Trading platform focused on futures and crypto.  Industry: Fintech / Trading Infrastructure  Likely Business Goals: User acquisition and community growth  Outreach Opportunity: Partnership automation and lead tracking 

---

## 💬 Workflow 2 — Personalized LinkedIn Outreach

### Purpose

Generate personalized outreach messages based on company research.

### AI creates

- LinkedIn connection message
- personalized outreach angle

### Example Output

Hi [Name], I admire your work in Partnerships Manager. At OpenAI, we're keen to explore collaborative ways to advance AI responsibly and broaden its impact. Would love to connect and share ideas on fostering innovation and accessibility together!

---

## 📊 Workflow 3 — Lead Tracking

Results are automatically stored in Google Sheets.

Tracked fields:

- Date
- Company
- Website
- Target role
- Company summary
- Industry
- Outreach angle
- LinkedIn message
- Status

This creates a lightweight outreach CRM.

---

## 🛠 Tools Used

- n8n
- AI / LLM
- Google Sheets
- workflow automation

---

## 🚀 Business Impact

This workflow helps reduce repetitive prospect research and speeds up outreach preparation.

### Benefits

- saves manual lead research time
- creates personalized outreach faster
- improves lead organization
- supports sales / partnerships workflows
- keeps all outreach activity structured

---

## 👨‍💻 My Role

Designed and built the full workflow, including:

- workflow structure in n8n
- AI prompt creation
- company research logic
- outreach message generation
- Google Sheets integration
- workflow testing end-to-end

---

## 🎯 Use Cases

- sales prospecting
- partnerships outreach
- growth operations
- event sponsorship outreach
- lead qualification

