أيوه، نعمله من الأول بالـ **Qwen** بدل Gemini، وده النسخة اللي أنصحك تحطيها في `README.md`:

````markdown
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


## Tech Stack

* n8n
* Telegram Bot API
* Google Sheets
* Qwen
* AI Agent
* JavaScript

## How It Works

### 1. Task Creation

The user sends a natural language request through Telegram.

Example:

> Remind me tomorrow at 10 AM to pay the internet bill.

The AI Agent:

1. Understands the user's request.
2. Resolves the date and time using the Africa/Cairo timezone.
3. Creates the task.
4. Creates a reminder linked to the task.
5. Stores the data in Google Sheets.

### 2. Task Completion

When the user says:

> Done

The agent searches for the relevant task before completing it.

The task and its associated reminder are then marked as completed.

The agent does not guess task IDs and only confirms completion after the required operations succeed.

### 3. Snoozing Reminders

Users can postpone reminders using natural language.

Example:

> Snooze it for 1 hour.

The agent:

1. Searches for the correct reminder.
2. Finds its exact reminder ID.
3. Calculates the new reminder time.
4. Updates the reminder status.
5. Reschedules the notification.

### 4. Scheduled Notifications

A scheduled workflow periodically checks pending reminders.

When a reminder is due:

1. The related task is retrieved.
2. A Telegram notification is sent to the user.
3. The reminder status is updated.
4. The sending timestamp and attempt count are recorded.

### 5. Follow-up Notifications

The workflow can also handle follow-up reminders associated with tasks.

This allows the system to continue notifying the user when additional follow-up actions are required.

## AI Agent Tools

The AI Agent uses dedicated tools to interact with the task and reminder data.

### Task Tools

* Create Task
* Search Tasks
* Complete Task

### Reminder Tools

* Create Reminder
* Search Reminders
* Complete Reminder
* Snooze Reminder

The agent is instructed to search for existing records before performing operations that require an exact task or reminder ID.

## Data Structure

### Tasks

The Tasks sheet stores:

* `task_id`
* `user_id`
* `title`
* `description`
* `status`
* `priority`
* `due_date`
* `due_time`
* `recurrence`
* `category`
* `created_at`
* `completed_at`

### Reminders

The Reminders sheet stores:

* `reminder_id`
* `task_id`
* `user_id`
* `reminder_time`
* `status`
* `snooze_until`
* `sent_at`
* `attempt_count`
* `created_at`

## User Isolation

Each task and reminder is associated with the user's Telegram chat ID.

The AI Agent is instructed to only access and modify data belonging to the current user.

This prevents the assistant from accidentally accessing or modifying another user's tasks or reminders.

## Timezone Handling

All task and reminder dates are resolved using:

text
Africa/Cairo


Relative expressions such as:

* today
* tomorrow
* yesterday
* after one hour
* بعد ساعة
* بكرة

are converted into exact date and time values before being stored.

The workflow stores dates using:

text
YYYY-MM-DD


Times using:

text
HH:mm


Reminder timestamps using:

text
YYYY-MM-DD HH:mm:ss


## Multilingual Support

The assistant supports both Arabic and English.

It responds in the same language used by the user.

Example:

> بكرة الساعة 10 الصبح فكرني أدفع فاتورة النت

or:

> Remind me tomorrow at 10 AM to pay the internet bill.

## Memory

The workflow uses conversation memory to maintain context between Telegram messages.

This allows the assistant to handle short follow-up messages such as:

> Snooze it.

after a previous reminder-related conversation.

## Security

Sensitive credentials and personal identifiers have been removed from the published workflow.

Before importing and running the workflow, configure your own:

* Telegram credentials
* Google Sheets credentials
* Qwen credentials
* Google Spreadsheet ID

The published workflow does not contain the author's private credentials.

## Demo

A demonstration video showing the workflow in action:

**[Add Demo Link]**

## Future Improvements

Possible future improvements include:

* Replace Google Sheets with PostgreSQL
* Add recurring task management
* Add calendar integration
* Add more notification channels
* Add advanced error handling and retry logic
* Add task analytics and statistics
* Add priority-based notifications
* Add a web dashboard

## Project Structure

```text
ai-telegram-task-reminder-agent/
│
├── workflow.json
├── README.md
└── .gitignore
```

## Installation

1. Import `workflow.json` into n8n.
2. Configure your Telegram credentials.
3. Configure your Google Sheets credentials.
4. Configure your Qwen model credentials.
5. Connect the workflow to your own Google Spreadsheet.
6. Configure the required Google Sheets structure.
7. Activate the workflow.
8. Start interacting with the assistant through Telegram.

