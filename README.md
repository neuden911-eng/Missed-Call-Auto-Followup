<<<<<<< HEAD
# 📵 Missed Call Auto-Followup
> Automatically follow up with anyone who called but got no answer — via WhatsApp. Built with n8n, Twilio & Telegram.

![n8n](https://img.shields.io/badge/n8n-workflow-orange?style=flat-square)
![Twilio](https://img.shields.io/badge/Twilio-WhatsApp-red?style=flat-square)
![Telegram](https://img.shields.io/badge/Telegram-Bot-blue?style=flat-square)
![Google Sheets](https://img.shields.io/badge/Google-Sheets-green?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)

---

## 🔥 What It Does

Every time someone calls your business and nobody picks up:

1. **Detects** the missed call via Twilio webhook
2. **Instantly sends** a WhatsApp message to the caller:
   > *"Hi! Sorry we missed your call 🙏 We'd love to help — what can we assist you with?"*
3. **Notifies the owner** on Telegram with caller details
4. **Logs the missed call** to Google Sheets
5. When the caller **replies on WhatsApp** → forwards their message to the owner on Telegram instantly
6. **Updates the Google Sheet** with their reply and marks the lead as needing follow-up

---

## 🏗️ Architecture

```
📞 Missed Call
      │
      ▼
Twilio Webhook ──► Was Call Missed? ──► Extract Details
                                               │
                        ┌──────────────────────┼──────────────────────┐
                        ▼                      ▼                      ▼
               Send WhatsApp          Log to Google Sheets    Notify Owner
               to Caller                                      on Telegram

💬 Caller Replies on WhatsApp
      │
      ▼
Twilio Webhook ──► Extract Reply ──► Forward to Owner (Telegram) ──► Update Sheet
```

---

## 🛠️ Tech Stack

| Service | Purpose | Cost |
|---|---|---|
| [n8n](https://n8n.io) | Workflow automation engine | Free (self-hosted) |
| [Twilio](https://twilio.com) | Receive calls + send WhatsApp | Free trial ~$15 credit |
| [Telegram Bot](https://t.me/BotFather) | Notify business owner | Free forever |
| [Google Sheets](https://sheets.google.com) | Log calls and replies | Free forever |

---

## ⚡ Quick Start

### 1. Prerequisites
- n8n instance running (self-hosted or cloud)
- Twilio account (free trial works)
- Telegram bot token (create via [@BotFather](https://t.me/BotFather))
- Google account

### 2. Import the Workflow
1. Open your n8n instance
2. Go to **Workflows → Import from File**
3. Upload `Missed-Call-Auto-Followup.json`

### 3. Configure Credentials

**Twilio:**
- Account SID + Auth Token from [Twilio Console](https://console.twilio.com)
- Add as "Twilio API" credential in n8n

**Google Sheets:**
- Connect your Google account in n8n
- Select your spreadsheet in both Google Sheets nodes

**Telegram:**
- Create a bot via [@BotFather](https://t.me/BotFather) → copy the token
- Get your Chat ID via [@userinfobot](https://t.me/userinfobot)
- Replace `YOUR_TELEGRAM_CHAT_ID` in both Telegram nodes

### 4. Set Up Your Google Sheet

Create a spreadsheet with these exact column headers:

| CallerPhone | CalledNumber | CallTime | Status | FollowedUp | LeadReply | ReplyTime |
|---|---|---|---|---|---|---|

### 5. Point Twilio to Your Webhooks

In [Twilio Console](https://console.twilio.com) → Phone Numbers → your number:

- **Voice webhook (missed call):**
```
https://YOUR-N8N-URL/webhook/missed-call
```

- **WhatsApp incoming message webhook:**
```
https://YOUR-N8N-URL/webhook/whatsapp-reply
```

### 6. Activate the Workflow
Toggle the workflow to **Active** in n8n — you're live! 🚀

---

## 🧪 Testing

**Test missed call detection:**
```bash
curl -X POST https://YOUR-N8N-URL/webhook/missed-call \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "CallStatus=no-answer&From=%2B15551234567&To=%2B14155238886"
```

**Test WhatsApp reply:**
```bash
curl -X POST https://YOUR-N8N-URL/webhook/whatsapp-reply \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "From=%2B15551234567&Body=Yes+I+need+help+with+my+order"
```

---

## 💡 Use Cases

- 💇 **Salons & spas** — never lose a booking inquiry
- 🏥 **Clinics & doctors** — follow up with patients instantly
- 🔧 **Repair shops** — capture every service lead
- 🏠 **Real estate agents** — respond to property inquiries 24/7
- 🎓 **Coaching institutes** — follow up with prospective students
- ⚡ **Electricians / plumbers** — recover leads from busy hours

---

## 💰 Monetization (for Freelancers)

This workflow is sellable as a service to local businesses:

| Package | Price |
|---|---|
| Setup fee | ₹6,000 – ₹12,000 |
| Monthly retainer | ₹1,500 – ₹2,500/month |
| ROI pitch | *"One recovered lead pays for 3 months of your fee"* |

---

## 🗺️ Roadmap

- [ ] AI-powered smart reply suggestions via Gemini
- [ ] Daily missed call summary report on Telegram
- [ ] CRM integration (HubSpot / Zoho)
- [ ] Multi-language WhatsApp messages
- [ ] Escalation if lead doesn't reply within 1 hour

---

## 📄 License

MIT — free to use, modify, and sell.

---

## 🙌 Contributing

Pull requests welcome! If you improve this workflow, share it back.

---

*Built with ❤️ using [n8n](https://n8n.io)*
=======
# Missed-Call-Auto-Followup
Missed Call Auto-Followup — Automatically sends a WhatsApp message to anyone who calls and gets no answer. Captures their reply and forwards it to the business owner via Telegram. Logs all missed calls and responses to Google Sheets. Built with n8n, Twilio, and Telegram. Never lose a lead again.
>>>>>>> 502e378810568f7a13c9d7fe1c2fbd631acb1556
