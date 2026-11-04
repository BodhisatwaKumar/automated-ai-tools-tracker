# Automated AI Tools & Content Aggregator

An automated ingestion pipeline built with **n8n**, running inside a cloud container with persistent **PostgreSQL (Neon)** storage. The workflow aggregates AI tool launches from multiple feeds, scores and filters the entries using custom JavaScript logic, synchronizes records with **Google Sheets**, and dispatches automated digests via the **Gmail API**.

---

## Architecture & Data Flow

1. **Scheduled Ingestion:** Runs automatically via a configured cron trigger.
2. **Multi-Source Fetching:** Concurrently pulls latest entries from Hacker News AI discussions and Product Hunt feeds.
3. **Filtering & Scoring Engine:**
   - Evaluates content with regex-based weighted heuristics to score relevance.
   - Filters out non-technical noise and applies payload limits.
4. **Data Sync & Alerts:**
   - Appends filtered entries into a structured Google Sheet.
   - Formats a responsive HTML digest and dispatches it via Gmail API.

---

## Tech Stack & Infrastructure

- **Workflow Orchestration:** n8n
- **Runtime Environment:** Render (Docker container)
- **Database Layer:** Neon Serverless PostgreSQL (persistent state & credentials)
- **Integrations:** Google Sheets API, Gmail API, RSS/Atom Feeds

---

## Setup & Deployment

1. Import `ai-tools-tracker.json` into your n8n workspace.
2. Connect your credentials:
   - **Google Sheets OAuth2 API**
   - **Gmail OAuth2 API**
3. Update the target Google Sheet ID and recipient email in the respective nodes.
4. Toggle the workflow to **Active**.
