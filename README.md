# lark-ai-bot

A **Lark/Feishu chatbot** that turns a chat group into an ops console: ask it questions, get scheduled reports, and approve outgoing actions with one tap.

> Demo / sanitized version. Built originally for a daily data-ops workflow; secrets and proprietary logic removed.

## Features
- 💬 **Q&A in chat** — send a query, get a structured answer (pluggable backend: API / LLM / RAG).
- 🗓️ **Scheduled push** — daily/▾ reports delivered to a group or DM.
- ✅ **Approval flow** — drafts are pushed for review; reply `发3 / 改3 新内容 / 转3` to publish, edit, or forward.
- 🔌 **WebSocket long-connection** — runs from a laptop/VPS, no public IP or tunneling needed.

## Tech
Python · `lark-oapi` (Feishu open platform) · threading · pluggable LLM backend.

## How it works
```
Feishu message → WebSocket event → command router
  ├─ query        → backend (API/LLM/RAG) → reply
  ├─ approval(发/改/转) → publish pipeline
  └─ scheduled    → push report to chat
```

## Run
```bash
pip install lark-oapi
export FEISHU_APP_ID=...   FEISHU_APP_SECRET=...
python feishu_bot.py
```

## Notes
Production-grade error handling, run-once flags, and GBK/UTF-8 cross-platform handling included. Ask me to adapt it to Slack / Telegram / WeChat Work.
