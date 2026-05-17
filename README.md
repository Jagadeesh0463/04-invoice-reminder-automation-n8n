
# 📄 Invoice Reminder & Escalation Automation

Automated invoice follow-up workflow built with **n8n**, **Gmail API**, and **Google Sheets**.
Detects unpaid invoices, calculates overdue days, and sends escalating reminders — reducing manual follow-up and improving payment collection.

---

![n8n](https://img.shields.io/badge/Built%20with-n8n-orange)
![Gmail](https://img.shields.io/badge/Email-Gmail-red)
![Google Sheets](https://img.shields.io/badge/Tracker-Google%20Sheets-green)
![License](https://img.shields.io/badge/license-MIT-blue)

---

## 🚀 Features

✔ Auto-fetch unpaid invoices from Google Sheets
✔ Calculate overdue days dynamically
✔ Route reminders by escalation stage (Day 3 / Day 7 / Day 14)
✔ Send personalized reminder emails via Gmail
✔ Update reminder stage in tracker automatically
✔ Flag invoices for manual follow-up at Day 14

---

## 📌 Problem Statement

56% of small businesses are owed money from unpaid invoices, averaging $17.5K (QuickBooks, 2024).
Manual follow-up is awkward, repetitive, and easy to forget.

This workflow automatically:
- Detects overdue invoices daily
- Sends friendly → urgent → final notice emails
- Tracks reminder status in Google Sheets
- Flags critical invoices for manual intervention

Result:
**Less awkward chasing → Faster payments → Better cash flow**

---

## 🏗 Workflow Architecture

text
Schedule Trigger (Daily)
        ↓
Fetch Unpaid Invoices (Google Sheets)
        ↓
Calculate Overdue Days
        ↓
Route Reminder Stage (Switch)
    ↓         ↓         ↓
  DAY3      DAY7      DAY14
        ↓
Set Reminder Content
        ↓
Send Reminder Email (Gmail)
        ↓
Update Reminder Stage (Google Sheets)
        ↓
Flag Manual Follow-up (Google Sheets)

---

## 📷 Workflow Screenshots

text
screenshots/
├── workflow-overview.png
├── reminder-email-day3.png
├── reminder-email-day7.png
├── reminder-email-day14.png
└── google-sheets-tracker.png
```

![Workflow](screenshots/workflow-overview.png)

---

## 🧠 Escalation Stages

| Stage | Trigger | Tone |
|-------|---------|------|
| DAY3 | 3 days overdue | Friendly reminder |
| DAY7 | 7 days overdue | Urgent follow-up |
| DAY14 | 14+ days overdue | Final notice + manual flag |

---

## ⚙ Tech Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow orchestration |
| Google Sheets | Invoice tracker / CRM |
| Gmail API | Sending reminder emails |
| JavaScript | Overdue day calculation |

---

## 📦 Repository Structure

text
.
├── workflow/
│     invoice-reminder-automation.json
│
├── screenshots/
│     workflow-overview.png
│     reminder-email-day3.png
│     reminder-email-day7.png
│     reminder-email-day14.png
│     google-sheets-tracker.png
│
├── .env.example
├── .gitignore
└── README.md

---

## 🗂 Google Sheets Structure

Your sheet must have these columns:

| Invoice ID | Client Name | Client Email | Amount | Due Date | Status | Reminder Stage | Manual Follow-up | Last Reminder Sent |
|-----------|------------|-------------|--------|----------|--------|---------------|-----------------|-------------------|

Set `Status` to `UNPAID` for invoices to be picked up by the workflow.

---

## 🔧 Prerequisites

- n8n instance running
- Gmail OAuth configured
- Google Sheets OAuth configured
- Google Sheet set up with correct columns

---

## 🚀 Installation

Clone repository:
bash
git clone https://github.com/your-username/n8n-invoice-reminder-automation.git
cd n8n-invoice-reminder-automation
```

Create env:
bash
cp .env.example .env

Fill credentials:
env
GMAILOAUTH2_ID=
GMAILOAUTH2_NAME=
GOOGLESHEETSOAUTH2API_ID=
GOOGLESHEETSOAUTH2API_NAME=
DOCUMENTID=
SHEETNAME=
N8N_INSTANCE_ID=
WEBHOOK_ID_1=

Import workflow:
1. Open n8n
2. Workflows → Import
3. Select `workflow/invoice-reminder-automation.json`
4. Reconnect credentials
5. Set your Google Sheet ID and Sheet name
6. Activate workflow

---

## 📩 Sample Reminder Emails

**Day 3 — Friendly Reminder**
text
Dear [Client Name],

This is a friendly reminder that Invoice INV-001 amounting to ₹15,000
was due on 2026-05-01 and remains unpaid.

We kindly request you to process the payment at your earliest convenience.

Thank you for your business.
Regards, Finance Team

**Day 7 — Urgent Follow-up**
text
Dear [Client Name],

Our records indicate that Invoice INV-001 for ₹15,000 remains outstanding
beyond the due date.

Please arrange payment as soon as possible to avoid delays in future services.

Regards, Finance Team


**Day 14 — Final Notice**
text
Dear [Client Name],

This is a final reminder regarding overdue Invoice INV-001 amounting to ₹15,000.
The invoice has remained unpaid for 14+ days. Kindly treat this as urgent.
Further follow-up may be required if payment is not received.

Regards, Finance Team
```

---

## 🔒 Security

Never commit:
- Real credential IDs
- Google Sheet IDs or URLs
- Gmail tokens or API keys

Use placeholders before pushing to GitHub.

---

## 🛣 Roadmap

- [ ] WhatsApp reminders via Twilio
- [ ] Slack escalation alerts
- [ ] PDF invoice attachment
- [ ] Multi-currency support
- [ ] Dashboard analytics

---

## 👨‍💻 Author

**Jagadeesh S**
Built using:
n8n + Gmail API + Google Sheets + JavaScript

If you found this useful, consider starring ⭐ the repository.
