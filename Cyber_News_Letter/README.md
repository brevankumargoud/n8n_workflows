# 📰 Cyber News Letter – n8n Automation

## 📌 Overview

**Cyber News Letter** is an automated n8n workflow that fetches the latest cybersecurity news and events from multiple sources, summarizes them using an AI model, and delivers a clean, email-ready cyber news digest directly to your inbox **every day**.

This workflow is designed to save time, reduce information overload, and provide a concise daily overview of important cybersecurity developments.

---

## 🚀 What This Workflow Does

On a daily schedule, the workflow:

1. Fetches the latest cybersecurity articles from trusted RSS feeds  
2. Collects information about upcoming and recent cyber events in India using a search engine API  
3. Merges all collected news into a single data stream  
4. Sends the aggregated data to an LLM (Gemini)  
5. The LLM:
   - Visits each article
   - Reads and understands the content
   - Generates a short, easy-to-read summary
   - Formats the output as an email-ready newsletter  
6. Delivers the final cyber news email via Gmail  

---

## 🧠 Data Sources

- **Securelist** – Malware research and threat intelligence  
- **WeLiveSecurity (ESET)** – Security research and industry insights  
- **Search Engine Events API (SerpAPI)** – Latest cyber events in India  

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---------|--------|
| **n8n** | Workflow automation and orchestration |
| **RSS Feeds** | Fetching newly published cybersecurity articles |
| **SerpAPI** | Retrieving cyber-related event information |
| **Google Gemini (LLM)** | Reading, summarizing, and formatting news content |
| **Gmail API** | Email delivery of the final newsletter |

---

## ⏰ Automation Schedule

- **Trigger Type:** Schedule Trigger  
- **Frequency:** Daily  
- **Timezone:** Asia/Kolkata  

The workflow automatically runs every day and sends the newsletter at the configured time without any manual intervention.

---

## 📧 Email Format

Each email includes:
- A clear subject line: **“Today's Cyber News”**
- Headlines in **ALL CAPS**
- 3–4 sentence summaries for each article
- Direct links to read full articles
- Clean and readable formatting for quick consumption

---

## 📂 Files Included

- `News_Letter.json` – Exported n8n workflow file  

You can import this JSON directly into your n8n instance.

---

## 🔧 How to Use

1. Import the workflow JSON into your n8n instance  
2. Configure credentials:
   - Gmail OAuth
   - SerpAPI key
   - Google Gemini API key  
3. Adjust the schedule time if needed  
4. Activate the workflow  

That’s it — you’ll start receiving daily cyber news automatically.

---

## 🔐 Notes & Security

- API keys and credentials **should not be committed** to public repositories  
- Use environment variables or n8n credentials for secure configuration  
- This repository contains **only the workflow logic**, not sensitive secrets  

---

## 🙌 Author

Created and maintained by **Revan Kumar Goud Bommagoni**  
Focused on cybersecurity automation, offensive security, and AI-driven workflows.

---

⭐ If you find this workflow useful, feel free to star the repository and adapt it for your own use.
