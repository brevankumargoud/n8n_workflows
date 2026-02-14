# 🚀 LinkedIn Post Generator -- n8n Workflow

An AI-powered, state-driven LinkedIn post automation system built using
**n8n**, **Google Sheets**, **Google Gemini**, **Google Drive**, and
**LinkedIn API**.

This workflow transforms structured sheet inputs into professionally
formatted LinkedIn posts, allows controlled human refinement, and
publishes only after approval.

------------------------------------------------------------------------

## 📌 Overview

This workflow automates the complete lifecycle of LinkedIn content
creation:

1.  📝 Generate post using AI
2.  ✏️ Allow structured modifications
3.  ✅ Wait for approval
4.  🖼️ Attach image from Google Drive
5.  🚀 Publish to LinkedIn
6.  📊 Update posting status in Google Sheets

It is designed as a **single workflow**, using conditionals, loops, and
state checks --- not sub-workflows.

------------------------------------------------------------------------

## 🧠 Architecture Flow

Google Sheets Trigger (Row Added)\
↓\
Writer (AI Content Generation - Gemini)\
↓\
Primary_Output (Update "Output" column)\
↓\
Wait (Polling Delay)\
↓\
Get (Fetch latest row data)\
↓\
Editor (Apply modifications if any)\
↓\
Update Row ("Modified Output")\
↓\
IF Approval == Approved\
↙️ ↘️\
Wait Again Merge Image + Text\
↓\
LinkedIn Post\
↓\
Update Status = POSTED

------------------------------------------------------------------------

## 📊 Google Sheets Structure

| Column                | Purpose                                   |
|------------------------|-------------------------------------------|
| Description            | Project or Certificate description        |
| Images                 | Google Drive image link                  |
| Links                  | GitHub repository link                   |
| Output                 | AI-generated first draft                 |
| Modifications/If any   | User refinement instructions              |
| Modified Output        | Final AI-refined content                  |
| Approval               | Must be set to `Approved`                 |
| Status                 | Updated to `POSTED` after publishing      |


## 🔍 Detailed Node Explanation

### 1️⃣ Google Sheets Trigger

-   Event: `rowAdded`
-   Polls every minute
-   Activates when new content is added

### 2️⃣ Writer (Gemini LLM)

-   Uses Google Gemini Chat Model
-   Analyzes:
    -   Description
    -   GitHub link
-   Determines:
    -   Project OR Certificate
    -   Domain (Cybersecurity / AI / Web / DevOps / etc.)
-   Generates structured LinkedIn-ready content
-   Writes to `Output` column

### 3️⃣ Wait Node

Introduces a delay before checking for modifications or approval.
Enables manual review and prevents accidental publishing.

### 4️⃣ Get Node

Fetches updated row data including: - Output - Modifications - Approval
status

### 5️⃣ Editor (Gemini LLM -- Precision Mode)

-   Returns content exactly as-is if no modification is given
-   Applies only explicitly mentioned changes
-   Preserves structure, emojis, formatting
-   Avoids unnecessary rewriting
-   Writes result to `Modified Output`

### 6️⃣ IF Node (Approval Gate)

Condition:

    Approval == "Approved"

If FALSE → Loop back to wait and apply the modifications given by the user
If TRUE → Continue to publishing

### 7️⃣ Google Drive -- Download Image

Extracts image file using dynamic Drive file ID parsing.

### 8️⃣ Merge Node

Combines: - Modified Output (text) - Image binary data

### 9️⃣ LinkedIn Node -- Create Post

-   Share category: IMAGE
-   Visibility: PUBLIC
-   Uses Modified Output as post text

### 🔟 Final Google Sheets Update

Updates:

    Status = POSTED

------------------------------------------------------------------------

## 🎯 Key Design Principles

✅ State-Driven Publishing\
✅ Human-in-the-Loop AI\
✅ Controlled Editing Logic\
✅ Single Workflow Architecture\
✅ Automated Publishing After Approval\

------------------------------------------------------------------------

## 🔐 Required Credentials

-   Google Sheets OAuth
-   Google Drive OAuth
-   Google Gemini API
-   LinkedIn OAuth2

------------------------------------------------------------------------

## 🛠 Technologies Used

-   n8n
-   Google Sheets API
-   Google Drive API
-   Google Gemini (LLM)
-   LinkedIn API
-   Conditional Logic (IF nodes)
-   Merge node (Binary + JSON)

------------------------------------------------------------------------

## 🚀 How To Use

1.  Import the workflow JSON into n8n.
2.  Configure credentials.
3.  Create Google Sheet with required columns.
4.  Add a new row with Description, Image link, and GitHub link.
5.  Wait for AI to generate Output.
6.  Add modifications (optional).
7.  Set Approval to `Approved`.
8.  Post gets published automatically.
9.  Status becomes `POSTED`.

------------------------------------------------------------------------

## 📌 Future Improvements

-   Auto hashtag analytics
-   Time-based scheduling
-   Engagement tracking
-   Multi-account posting
-   Vector memory for brand tone

------------------------------------------------------------------------

## 👨‍💻 Author

Built by Revan Kumar Goud Bommagoni \
Passionate about Offensive Cybersecurity, automation-driven tooling, and building intelligent security systems.

------------------------------------------------------------------------

⭐ If you find this workflow useful, feel free to star the repository and adapt it for your own use.

