# AI News → LinkedIn Post Ideas

An n8n automation that runs every morning, pulls the latest AI news, and uses Claude AI to generate ready-to-post LinkedIn content ideas — automatically saved to a file.

Built as part of my journey learning agentic AI automation.

---

## What It Does

Every day at 8am this workflow:

1. Pulls the 5 latest articles from TechCrunch AI
2. Sends each article to Claude (Haiku) via the Anthropic API
3. Generates 3-5 LinkedIn post bullet points + an engagement question
4. Saves everything to a markdown file

No manual work. Open the file, pick a post, publish.

---

## Workflow

```
Schedule Trigger (8am daily)
  → RSS Read (TechCrunch AI feed)
    → Loop Over Items (one article at a time)
      → HTTP Request (Claude API)
        → Wait (3 seconds — rate limit buffer)
          → Set (format title, link, post idea)
            → Code (append to output file)
```

---

## Output Example

```
---
Title: OpenAI Releases New Model for Agents
Link: https://techcrunch.com/...

• OpenAI's new model is optimized for multi-step reasoning tasks [S1]
• Early benchmarks show 40% improvement on agentic workflows
• Key use cases: coding assistants, research agents, customer support bots

What's the one agentic use case you're most excited to see production-ready?
```

---

## Stack

| Tool | Purpose |
|---|---|
| n8n (Docker) | Workflow orchestration |
| Claude Haiku | Article summarization + post generation |
| TechCrunch RSS | Live AI news feed |
| Docker | Local n8n hosting |

---

## Setup

### Prerequisites
- Docker installed and running
- Anthropic API key — get one at [console.anthropic.com](https://console.anthropic.com)

### 1. Start n8n

```bash
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -e NODE_FUNCTION_ALLOW_BUILTIN=fs \
  -v ~/.n8n:/home/node/.n8n \
  -v /path/to/output:/output \
  n8nio/n8n:latest
```

Replace `/path/to/output` with the folder where you want post ideas saved.

### 2. Build the Workflow in n8n

Open `http://localhost:5678` and recreate the workflow using these nodes:

1. **Schedule Trigger** — daily at 8am
2. **RSS Read** — `https://techcrunch.com/category/artificial-intelligence/feed/`
3. **Loop Over Items** — batch size 1
4. **HTTP Request** — POST to `https://api.anthropic.com/v1/messages`
5. **Wait** — 3 seconds
6. **Set** — extract title, link, post_idea
7. **Code** — append to `/output/linkedin-post-ideas.md`

### 3. Add Your API Key

In the HTTP Request node, add these headers:

| Header | Value |
|---|---|
| `x-api-key` | `your-anthropic-api-key` |
| `anthropic-version` | `2023-06-01` |
| `content-type` | `application/json` |

### 4. Run It

Click **Execute Workflow** — check your output folder for `linkedin-post-ideas.md`.

---

## Lessons Learned

- n8n's Docker setup requires volume mounts for both data persistence and file output
- Anthropic's free tier has rate limits — a 3-second Wait node between calls prevents errors
- The `NODE_FUNCTION_ALLOW_BUILTIN=fs` flag is required to write files from n8n's Code node

---

## What's Next

- [ ] Add more RSS feeds (The Verge, MIT Tech Review)
- [ ] Auto-post directly to LinkedIn via API
- [ ] Add a filter to skip articles below a relevance score

---

## About

I'm building AI automations in public while learning agentic AI.
Follow my progress on [LinkedIn](https://linkedin.com/in/) and GitHub.
