# Quran Reels — Shared Prompts

One repo, one prompt per video, one instruction file per agent.

## How it works
1. Muse writes each day's video prompt into `prompts/` (one file per video).
2. `LATEST.md` always points to the current video's prompt file.
3. Each agent (OpenCode, Claude Code, Hermes) has its own standing instruction file in `agents/`. It tells that agent where to find the latest prompt and the fixed rules of the project.
4. The user only has to say to the agent: "نفّذ فيديو اليوم من الملف المشترك" — the agent pulls the repo, reads `LATEST.md`, follows the prompt file, and reports back.

## Repo layout
- `LATEST.md` — pointer to the current video prompt.
- `prompts/` — one prompt file per video (e.g. `ash-sharh-94-5-6.md`).
- `agents/opencode.md` — standing instructions for OpenCode.
- `agents/claude-code.md` — standing instructions for Claude Code.
- `agents/hermes.md` — standing instructions for Hermes.

## Fixed project rules (apply to every video)
- 9:16, 1080x1920, MP4, under 60 seconds.
- Uthmani script, large white text, spoken word turns GOLD exactly when spoken.
- English translation underneath (Sahih International, short).
- Top label: surah name + ayah numbers. Last second: "تابع للمزيد" + reciter name.
- Pure recitation, no music. Licensed recitation audio only (AlQuran Cloud / Quran.com).
- FREE path only, $0. Never publish — Mohamed reviews first.
