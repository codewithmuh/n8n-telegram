# AI Telegram Assistant – n8n Integration

This project sets up an AI-powered assistant using n8n and integrates it with multiple tools to automate tasks based on user input received via Telegram.

## 🧠 Overview

The assistant listens for messages via Telegram and uses the following tools:

### 🤖 OpenAI Model
- Understands user intent.
- Summarizes, rephrases, or extracts info from text.

### 📅 Google Calendar
- Creates or updates events.
- Parses date/time, titles, descriptions, and attendees from messages.

### 📧 Gmail
- Sends professional or casual emails.
- Extracts subject, recipients, body, and attachments.

### 📊 Google Sheets
- Appends or updates data (e.g., logs, records, metrics).

### 📇 Get Contacts
- Retrieves saved contacts to use in email/calendar actions.

## 📥 Input Examples

- “Schedule a call with Alex at 5pm tomorrow.” → Calendar Event.
- “Send an email to HR about my leave.” → Gmail Email.
- “Log today’s attendance.” → Google Sheet entry.

## ⚙️ System Instructions

The AI assistant operates under the following system message:

> You are an AI assistant receiving messages from Telegram. Today is {{ $now }}. You can perform actions using the following tools:

- **🧠 OpenAI Model** – Understand and respond to text naturally.
- **📅 Google Calendar** – Create, update, or fetch events.
- **📧 Gmail** – Send emails with context.
- **📊 Google Sheets** – Read/write data entries.
- **📇 Get Contacts** – Lookup contacts for reference.

Be proactive in asking for missing details (e.g., “What time?”). Always maintain context and data privacy.

## 🛠 Setup Notes

1. Use n8n to create Telegram trigger.
2. Use Switch nodes to check type of input (voice vs text).
3. Enable "Convert types where required" in conditional nodes.
4. Voice detection: `{{ !!$json.message.voice?.file_id }}`
5. Text detection: `{{ $json.message.text || "" }}`

## 🔐 Privacy

No user data is stored unless explicitly requested via Google Sheets or other services. Ensure proper OAuth permissions are configured in n8n for secure API access.

---

Created by [CodeWithMuh](https://cal.com/codewithmuh/discovery-call) 💡
