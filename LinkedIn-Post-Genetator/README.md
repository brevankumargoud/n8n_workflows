# 🚀 LinkedIn Post Creator — n8n State-Driven Automation Workflow

An advanced, AI-powered, **state-controlled LinkedIn publishing pipeline** built using:

**n8n • Google Sheets • Google Gemini • Google Drive • LinkedIn API**

This workflow enforces structured content generation, precision editing, multi-stage approval validation, and controlled publishing using a single orchestrated workflow architecture.

---

## 🧠 Core Design Philosophy

This is not a simple automation.

It is a **state machine built inside n8n**.

The workflow:

- Generates content
- Waits
- Re-checks sheet state
- Applies modifications precisely
- Validates approval
- Re-validates before publishing
- Merges binary + text
- Publishes
- Marks final status

No blind publishing.  
No uncontrolled execution.  
Everything is state-gated.

---

## 🧩 High-Level Architecture Flow

```
Google Sheets Trigger (Row Added)
        ↓
Writer (Gemini – Structured Generation Engine)
        ↓
Primary_Output (Write to "Output")
        ↓
Wait (10s polling delay)
        ↓
Get (Fetch Approval status)
        ↓
IF Approval == Approved?

If FALSE →
    Get1 (Fetch Output + Modifications)
    Editor (Precision modification engine)
    Update Row
    IF1 (Approval re-check)
        If FALSE → Wait again (loop)
        If TRUE → Continue

If TRUE → Continue

        ↓
Get2 (Fetch Final Modified Output)
        ↓
Download Image (Drive ID regex parsing)
        ↓
Merge (Combine binary + JSON by position)
        ↓
LinkedIn Create Post (IMAGE + PUBLIC)
        ↓
Update Status = POSTED
```

---

## 🔁 What Changed in This Version

### ✅ Dual Approval Gate

Approval is checked:
1. Before modification processing  
2. After modification processing  

This prevents:
- Accidental publishing
- Stale state execution
- Partial edit publishing

---

### ✅ True Loop-Based State Polling

If `Approval ≠ "Approved"`:

Workflow cycles:

```
Wait → Get → IF → Edit → Re-check → Loop
```

It behaves like a controlled polling engine.

---

### ✅ Binary + JSON Merge Strategy

**Merge Node Configuration:**

- Mode: Combine  
- Combine By: Position  
- Clash Handling: Add Suffix  

Ensures:
- Text payload remains intact  
- Image binary remains intact  
- No overwrite collision  

---

### ✅ Regex-Based Dynamic Drive File Extraction

The Google Drive node extracts the file ID dynamically from the sheet-provided URL using regex.

No manual parsing required.

---

## 📊 Google Sheets Structure

| Column                | Purpose |
|------------------------|----------|
| Description            | Core source of truth for content |
| Images                 | Google Drive share link |
| Links                  | GitHub repository link |
| Output                 | First AI-generated draft |
| Modifications/If any   | Explicit edit instructions |
| Modified Output        | Final precision-edited version |
| Approval               | Must equal `Approved` |
| Status                 | Set to `POSTED` after publish |

---

## 🧠 AI Layer Breakdown

### ✍ Writer Node (Gemini)

- Detects post type (Project / Certificate)
- Detects domain (Cyber / AI / DevOps / etc.)
- Applies structured formatting rules
- Controls emoji usage by domain
- Writes to `Output`

---

### 🧩 Editor Node (Gemini – Precision Mode)

This is not a rewriter.

It follows strict logic:

- If no modifications → return output EXACTLY  
- If modifications exist → apply ONLY requested changes  

Preserves:
- Structure  
- Emojis  
- Headings  
- Hashtags  
- Tone  

Acts like a diff-based refinement layer.

---

## 🛠 Nodes Used

- Google Sheets Trigger  
- Google Sheets (Read / Update)  
- Wait Node  
- IF Node (x2)  
- Gemini Chat Model (x2)  
- Google Drive Download  
- Merge (Binary + JSON)  
- LinkedIn Create Post  

---

## 🔐 Required Credentials

- Google Sheets OAuth2  
- Google Drive OAuth2  
- Google Gemini API  
- LinkedIn OAuth2  

---

## 🚀 How To Use

1. Import the JSON workflow into n8n  
2. Configure credentials  
3. Create Google Sheet with required columns  
4. Add a new row (Description + Image link + GitHub link)  
5. AI generates `Output`  
6. Add modifications if needed  
7. Set `Approval = Approved`  
8. Post publishes automatically  
9. Status updates to `POSTED`

---

## 🎯 Engineering Principles Demonstrated

- State-driven workflow design  
- Controlled human-in-the-loop AI  
- Double validation gating  
- Deterministic publishing  
- Binary + JSON merging  
- Poll-based state refresh  
- Single-workflow orchestration  

---

## 📌 Future Improvements

- Engagement analytics tracking  
- Scheduled publish windows  
- Brand-tone memory layer  
- Multi-account posting engine  
- Version history logging  

---

## 👨‍💻 Author

Built by **Revan Kumar Goud Bommagoni**

Offensive Cybersecurity Focused.  
Automation Architect.  
Systematic Builder.

---

## ⭐ Final Note

This is not just a LinkedIn post generator.

It is a structured publishing control system built inside n8n.
