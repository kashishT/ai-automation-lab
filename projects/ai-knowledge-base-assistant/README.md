# AI-Powered Knowledge Base Assistant (n8n + AI Tagging + Retrieval)

## Overview

Built an AI-powered internal knowledge base chatbot using n8n.

The chatbot helps teams manage frequently asked questions by automatically organizing answers and returning relevant responses to end users.

The workflow is split into two separate automations:

---

## Workflow 1 — Knowledge Ingestion & Auto Tagging

### Purpose

Allow company employees to add questions and answers into the knowledge base.

### How it works

1. Employee submits:

- question
- answer

2. AI analyzes the content

3. AI automatically generates relevant tags

Example tags:

- billing
- refunds
- login
- account access
- product support

4. Question + answer + AI-generated tags are saved into database

### Outcome

Knowledge base becomes structured automatically without manual tagging.

---

## Workflow 2 — Customer Q&A Assistant

### Purpose

Help users get answers from the stored knowledge base.

### How it works

1. User asks a question

2. AI analyzes user query

3. Workflow searches database

4. Matches tags with relevant entries

5. Returns best answer

6. If no answer is found:

User receives fallback message:

“Sorry, I could not find an answer. Please connect with support.”

### Outcome

Fast self-service support with fallback to human support.

---

## Tools Used

- n8n
- AI model / LLM
- database
- workflow automation

---

## Key Features

- AI auto-tagging
- searchable FAQ database
- retrieval-based responses
- support fallback
- no-code / low-code workflow design

---

## Skills Demonstrated

- AI workflow automation
- prompt-based tagging
- knowledge retrieval logic
- database automation
- chatbot design in n8n
- business process automation

---

## Use Cases

- customer support FAQ
- internal knowledge base
- onboarding help desk
- support automation

---

## Screenshot

client workflow to ingest knowledge.

<img width="1134" height="516" alt="knowledge-ingestion-workflow" src="https://github.com/user-attachments/assets/49c28379-bf30-4e2b-9585-fdab798fac02" />

user workflow

<img width="767" height="449" alt="customer-qa-workflow" src="https://github.com/user-attachments/assets/b6794f25-8824-4dc9-8b13-c1e578b6f4bf" />

