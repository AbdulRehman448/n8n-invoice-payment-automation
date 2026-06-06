# 💰 Invoice & Payment Follow-up Automation — n8n

Automated invoice payment reminder system that monitors due dates daily, sends personalized emails for upcoming, due today, and overdue invoices, and logs all activity to Google Sheets automatically — zero manual effort.

## 🚀 What It Does

- 📋 Reads all unpaid invoices from Google Sheets daily
- 📅 Calculates due date difference for each invoice dynamically
- 🔀 Routes invoices into 3 categories: Upcoming, Due Today, Overdue
- 📧 Sends personalized reminder emails via Gmail for each category
- 📊 Logs all sent reminders to a Reminders Log sheet with timestamps
- ✅ Automatically skips invoices marked as Paid
- ⏰ Runs every 24 hours — fully hands-off collection system

## 🏗️ Workflow Architecture
Daily Schedule → Read Invoices → Check Due Dates → Check Skip →
Route by Reminder Type →
├── Upcoming (1-5 days)  → Send Upcoming Reminder Email
├── Due Today (0 days)   → Send Due Today Reminder Email
└── Overdue (past due)   → Send Overdue Reminder Email
↓
Log to Reminders Sheet

## ✨ Advanced Features

- **Dynamic due date calculation** — works for any due date, not just hardcoded days
- **3-tier email routing** — different tone for upcoming, due today, and overdue
- **Paid invoice skip** — change status to Paid in sheet, reminders stop automatically
- **Upsert logging** — no duplicate rows even if workflow runs multiple times
- **Pakistan timezone** — all timestamps in Asia/Karachi time

## 🛠️ Tech Stack

| Tool | Usage |
|------|-------|
| n8n Cloud | Workflow orchestration |
| Google Sheets | Invoice storage and reminders log |
| Gmail OAuth2 | Personalized email dispatch |
| JavaScript (Code node) | Dynamic due date calculation |
| Switch node | Three-way email routing |

## 📋 Google Sheets Structure

**Invoices tab columns:**
| client_name | client_email | invoice_number | amount | due_date | status |
|------------|-------------|---------------|--------|----------|--------|
| John Smith | john@example.com | INV-001 | $500 | 2026-06-01 | Unpaid |

**Reminders Log tab columns:**
`client_name | client_email | invoice_number | amount | due_date | reminder_type | sent_at`

## ⚙️ Setup

1. Import `workflow.json` into n8n Cloud
2. Connect Google Sheets OAuth2 credentials
3. Connect Gmail OAuth2 credentials
4. Create Google Sheet with Invoices and Reminders Log tabs
5. Update Spreadsheet ID in all Google Sheets nodes
6. Add your invoices to the Invoices tab
7. Activate workflow — runs daily automatically

## 📧 Email Types

| Reminder Type | When Sent | Tone |
|--------------|-----------|------|
| Upcoming | 1-5 days before due date | Friendly reminder |
| Due Today | On the due date | Urgent notice |
| Overdue | Any day past due date | Firm follow-up |

## 📬 Contact

**Abdul Rehman Ali**

[LinkedIn](https://www.linkedin.com/in/abdul-rehman-ali/) | [Portfolio](https://abdulrehmanali.netlify.app/) | abdulrehman.tp.786@gmail.com
