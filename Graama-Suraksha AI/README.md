# Graama-Suraksha AI 🛡️

### AI-Powered Cyber Fraud Detection & Community Alert System

Graama-Suraksha AI is an **AI-driven cyber safety assistant designed to help rural and non-technical users detect online scams instantly through WhatsApp.**

The system analyzes suspicious messages using **Google Gemini AI**, explains the risk in **simple language**, and builds a **community fraud intelligence network** that automatically warns users when scam patterns begin spreading.

This project was built during the **Aadhya 3.0 Hackathon**.

---

# 🚨 The Problem

Cyber fraud is growing rapidly, especially through:

* Phishing messages
* Fake customer care numbers
* OTP scams
* Investment scams
* KYC update scams
* Lottery scams
* Job scams

Many victims are **non-technical users who cannot easily determine whether a message is legitimate or fraudulent.**

Existing solutions often require:

* Cybersecurity knowledge
* Installing applications
* Technical understanding

Graama-Suraksha AI solves this by providing a **simple WhatsApp-based scam detection system**.

---

# 💡 Solution Overview

Users simply **forward a suspicious message to a WhatsApp bot.**

The system then:

1. Detects the **user's intent**

2. Analyzes the message using **AI**

3. Determines:

   * Fraud Type
   * Risk Level
   * Fraud Probability

4. Explains the scam in **simple language**

5. Responds in the **user’s preferred language**

6. Stores fraud reports for **pattern analysis**

7. Triggers **community fraud alerts when similar scams appear repeatedly**

---

# ⚡ Key Features

## AI Fraud Detection

Messages are analyzed using **Google Gemini AI** with a carefully engineered prompt designed for cyber fraud detection.

The AI evaluates signals such as:

* Suspicious keywords
* Urgency tactics
* Requests for money
* OTP / PIN requests
* Impersonation attempts
* Phishing links
* Fake service numbers

---

## Multilingual Support 🌍

The chatbot supports multiple languages:

* English
* Telugu
* Tamil
* Hindi

Users select their preferred language from an **interactive WhatsApp menu**, and the AI generates responses accordingly.

---

## WhatsApp-Based Cyber Assistant 📱

Users interact with the system directly through WhatsApp.

Workflow:

1. User sends a suspicious message
2. Bot asks user to choose language
3. AI analyzes the message
4. Bot returns scam analysis and safety advice

This design ensures the system is **accessible even to rural and non-technical users**.

---

## Voice Guidance Support 🔊

The system can also send **audio responses in the user's selected language**, improving accessibility for users who may prefer listening over reading.

Supported voice responses:

* English
* Telugu
* Tamil
* Hindi

---

## Fraud Intelligence Logging 📊

Every analyzed message is stored in **Google Sheets** with the following details:

* Phone number
* Fraud type
* Risk level
* Timestamp
* Alert status

This enables the system to track **fraud trends and repeated scam patterns**.

---

# 🚨 Community Fraud Alert System

Graama-Suraksha AI includes a **community threat intelligence mechanism**.

When **multiple users report the same fraud pattern**, the system automatically:

1. Detects repeated fraud types
2. Generates a **community alert message using AI**
3. Broadcasts warnings to registered users via WhatsApp

This creates a **crowdsourced cyber defense network**.

---

# ⚙️ System Architecture

The system is built using **n8n automation workflows**.

Two primary workflows power the system.

```
User → WhatsApp Bot → AI Fraud Detection → Fraud Logging → Alert System
```

---

# 🧠 Main Workflow: `Fraud_Detection.json`

Responsible for:

* Receiving WhatsApp messages
* Language selection
* AI scam detection
* Extracting fraud indicators
* Logging fraud reports
* Triggering the alert system

### Key Components

**WhatsApp Trigger**

Receives incoming user messages.

**Message Processor**

Separates language selection events from message content.

**Language Menu**

Allows users to choose their preferred language.

**Gemini AI Analysis**

Analyzes suspicious messages and generates fraud assessment.

**Data Extraction Node**

Extracts:

* Intent
* Fraud type
* Risk level
* Fraud probability

**Fraud Logging**

Stores results in Google Sheets.

**Voice Response Node**

Sends language-specific audio guidance.

**Alert Workflow Trigger**

Activates the community alert system when fraud is detected.

---

# 🚨 Secondary Workflow: `Alert_Sender.json`

Responsible for detecting **community-level fraud patterns**.

### How It Works

1. Reads all fraud entries from Google Sheets

2. Identifies the **last processed alert**

3. Counts repeated fraud patterns

4. If a fraud type appears **5 or more times**, it triggers a community alert.

---

## Alert Generation

Alerts are generated using an **LLM (Groq Chat Model)**.

The AI produces a WhatsApp alert message containing:

* Fraud type detected
* Explanation of the scam
* Safety advice
* Cybercrime reporting details

Example alert message:

```
⚠ COMMUNITY FRAUD ALERT

Multiple reports of a phishing scam have been detected.

Scammers are sending messages asking users to share OTPs or click suspicious links.

Do NOT share OTP, PIN, or banking details.

Report Cybercrime:
Helpline: 1930
https://cybercrime.gov.in
```

---

# 🛠 Tech Stack

| Technology         | Purpose                            |
| ------------------ | ---------------------------------- |
| n8n                | Workflow automation                |
| Google Gemini AI   | Fraud detection                    |
| Groq LLM           | Community alert generation         |
| WhatsApp Cloud API | User interaction                   |
| Google Sheets      | Fraud logging                      |
| JavaScript         | Workflow logic and data processing |

---

# 🔄 Repository Structure

```
/workflows
   Fraud_Detection.json
   Alert_Sender.json

README.md
```

---

# 🚀 Example User Flow

1. User receives suspicious message

2. User forwards it to the WhatsApp bot

3. Bot asks user to choose language

4. AI analyzes the message

5. Bot returns:

* Risk level
* Fraud probability
* Fraud type
* Safety advice

6. System logs fraud report

7. If repeated reports occur → **community alert broadcast**

---

# 🔮 Future Improvements

Possible future upgrades:

* Web dashboard for fraud analytics
* Real-time fraud map visualization
* Machine learning-based fraud pattern prediction
* SMS integration for users without WhatsApp
* Voice input support
* Integration with national cybercrime databases

---

# 👥 Team

Built during **Aadhya 3.0 Hackathon**

Team Members:

* Machabathuni Vishnu Vardhan
* Naga Sai Nikhila Katta
* Bee Bee Reshma Shaik
* Akhila Vooke
* **Revan Kumar Goud Bommagoni**

---

# 🛡️ Vision

Graama-Suraksha AI aims to build a **community-driven cyber defense network**.

Instead of responding **after money is lost**, the goal is to:

**Detect scams early, warn users quickly, and prevent cyber fraud before it spreads.**
