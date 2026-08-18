# AI Telegram Task & Reminder Agent

An AI-powered personal task and reminder assistant built with n8n, Telegram, Google Sheets, and Qwen.

The assistant allows users to manage tasks and reminders through natural language messages in both Arabic and English.

## Features

- Create tasks through Telegram
- Create reminders linked to tasks
- Complete tasks and reminders
- Snooze reminders
- Scheduled reminder notifications
- Follow-up notifications
- User-specific task and reminder isolation
- Arabic and English language support
- AI-powered natural language understanding
- Conversation memory
- Google Sheets as the data store
- Automatic date and time resolution

## Workflow Architecture

text
Telegram
   ↓
AI Agent
   ↓
Task & Reminder Tools
   ↓
Google Sheets
   ↓
Scheduled Reminder Engine
   ↓
Telegram Notifications
