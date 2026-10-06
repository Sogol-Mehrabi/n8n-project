# Telegram AI Assistant with n8n

A Telegram-based AI assistant built with **n8n** and OpenAI.

The workflow accepts text, voice messages, and images from Telegram and routes them to an AI agent. It can also use connected tools for contacts, email, and product/inventory information.

## What it can do

- 💬 Handle text messages from Telegram
- 🎙️ Transcribe voice messages and send them to the AI agent
- 🖼️ Analyze images with a vision-capable OpenAI model
- 🤖 Generate AI responses using an OpenAI chat model
- 🧠 Keep short conversational memory per Telegram user
- 📧 Send emails through Gmail when requested
- 👤 Look up contact email addresses from Google Sheets
- 📦 Query product/inventory information from Google Sheets
- 🔊 Generate and send audio responses for voice conversations

## Workflow overview

The main flow is:

Telegram → Message Type Detection → AI Processing → Telegram Response

Voice messages follow:

Telegram → Download Voice → Transcription → AI Agent → Response

Image messages follow:

Telegram → Download Image → Image Analysis → Telegram Response

Text messages are passed directly to the AI agent.

The AI agent also has access to a short-term memory component and optional tools for contacts, email, and product information.

## Requirements

Before importing the workflow, you will need:

- n8n
- A Telegram Bot created with BotFather
- An OpenAI API account
- A Gmail account if you want email sending
- Google Sheets access if you want the Contacts and Products tools

## Importing the workflow

1. Download the `telegram-ai-assistant-public.json` file.
2. Open your n8n instance.
3. Create a new workflow.
4. Use **Import from File** and select the JSON file.
5. Open the imported workflow.
6. Reconnect the required credentials:
   - Telegram
   - OpenAI
   - Gmail
   - Google Sheets
7. For the Google Sheets nodes, replace `YOUR_GOOGLE_SHEET_ID` with your own spreadsheet ID.
8. Make sure the required sheet/tab names match your configuration.
9. Test each branch before activating the workflow.
10. Activate the workflow when everything works correctly.

## Google Sheets setup

This workflow expects two kinds of spreadsheet data:

### Contacts

Used by the AI agent to find an email address when the user gives a person's name instead of an email address.

### Products

Used by the AI agent when the user asks about inventory/product information.

The actual spreadsheets are intentionally not included in this repository. Create your own sheets and connect them through n8n.

## Credentials and security

Credentials are **not included** in this repository.

Do not commit any of the following to GitHub:

- Telegram bot tokens
- OpenAI API keys
- Gmail credentials
- Google OAuth tokens
- Private Google Sheet URLs or IDs
- `.env` files containing secrets
- n8n instance credentials or exported credential data

The public workflow file has been cleaned of instance-specific credential information and private Google Sheet references.

## Notes

This repository contains the workflow structure, not a ready-to-run hosted bot.

You still need to connect your own accounts and credentials inside n8n.

## Tech stack

- n8n
- Telegram Bot API
- OpenAI
- Gmail
- Google Sheets

## Project structure

```text
n8n-project/
├── telegram-ai-assistant-public.json
├── README.md
└── .gitignore
```

## License

You can add the license that best matches how you want others to use the workflow. If you are unsure, MIT is a simple option for an open-source project.
