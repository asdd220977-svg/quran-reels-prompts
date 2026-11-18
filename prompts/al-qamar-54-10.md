# Al-Qamar 54:10 — copy-ready instructions for Codex (OpenMontage, already installed)

## Goal
Produce ONE video: Al-Qamar (Surah 54), ayah 10, reciter Ahmed bin Ali Al-Ajmi, in the same style as my existing reference videos (duha-93-5-v2.mp4 and ayat-al-kursi-v1.mp4, both 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- OpenMontage, Python 3.12, FFmpeg, git, Whisper (small model) and the Arabic fonts were already installed — check first, do NOT reinstall anything that already works. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Step 1 — Get the recitation audio (licensed)
- Al-Qamar = Surah 54, ayah 10.
- Reciter: Ahmed bin Ali Al-Ajmi.
- Fetch the MP3 from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/54:10/ar.ahmedajamy`
  The JSON response contains the audio URL. Download it into the project folder as `al-qamar-54-10-ajamy.mp3`. If that fails, get the same reciter's audio for Surah 54 ayah 10 from Quran.com / EveryAyah (`ar.ahmedajamy`).
- Verify the audio: report its exact duration (expected roughly 12 seconds).

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4` and `ayat-al-kursi-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Produce the Al-Qamar video
- Background: tunnel / heavy rain / rough sea. Free stock footage only, no paid assets.
- Text: the ayah in Uthmani script, large white, centred above the middle:
  فَدَعَا رَبَّهُ أَنِّي مَغْلُوبٌ فَانتَصِرْ
- Show the ayah in lines that appear progressively as recited. Each spoken word turns GOLD exactly when it is spoken — get word-level timestamps by transcribing the audio with local Whisper (small model, already installed) or from the Quran.com word-timing API (the method used for ayat-al-kursi-v1).
- English translation underneath in small white text (Sahih International): "So he invoked his Lord, 'Indeed, I am overpowered, so help.'"
- Top label: "سورة القمر - 10" and "AL-QAMAR 54:10".
- Last second of the video: "تابع للمزيد" + "القارئ: أحمد بن علي العجمي".
- Pure recitation, no music.
- Render to `al-qamar-54-10-v1.mp4`, 1080x1920, under 60 seconds.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 4 — Report back
- Tell me: the exact output file path, duration, file size, and total cost (must be $0).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
