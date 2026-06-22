# social-auto-poster

**Config-driven social-media automation**: generate on-brand posts with an LLM, schedule them, and push only after human approval. Plug in any niche by editing one config file.

> Sanitized version of a system running a live content account.

## Features
- ✍️ **Content engine** — niche/tone/audience/angles from `config.json`; generates posts via **local LLM (Ollama)** → zero per-post API cost.
- 🔁 **Angle rotation** so daily posts don't repeat.
- ✅ **Approval before publish** — drafts go to Lark/Telegram; one tap to send/edit.
- 🗓️ **Scheduler** — posting time-table per account; multi-account ready.
- 🛡️ **Compliance guard** — rejects posts containing error text / banned phrases; enforces length & disclaimers.

## Tech
Python · Ollama · `curl_cffi` (publishing) · schedulers (cron/launchd) · pluggable platforms.

## Config (excerpt)
```json
{ "niche": "fitness", "tone": "friendly, practical",
  "angles": ["bust a myth", "one habit to start today"],
  "schedule": [{"time":"08:00"},{"time":"20:00"}],
  "approval": {"channel":"lark","auto_publish":false} }
```

## Run
```bash
python engine.py config.json      # generate a post
python publisher.py config.json   # post after approval
```

## Notes
Built for creators/SMBs who want consistent posting without daily effort. I can add Xiaohongshu / WeChat / X, image generation, and analytics.
