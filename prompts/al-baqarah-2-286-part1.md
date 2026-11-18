# Al-Baqarah 2:286 (first part only) — copy-ready instructions for Claude Code (OpenMontage, already installed)

## Goal
Produce ONE video: Al-Baqarah (Surah 2), ayah 286 — FIRST PART ONLY, reciter Abdul Basit Abdul Samad, in the same style as my existing reference videos (duha-93-5-v2.mp4 and ayat-al-kursi-v1.mp4, both 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- OpenMontage, Python 3.12, FFmpeg, git, Whisper (small model) and the Arabic fonts were already installed — check first, do NOT reinstall anything that already works. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Step 1 — Get the recitation audio (licensed)
- Al-Baqarah = Surah 2, ayah 286 — FIRST PART ONLY.
- Reciter: Abdul Basit Abdul Samad (murattal).
- Fetch the MP3 from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/2:286/ar.abdulbasitmurattal`
  The JSON response contains the audio URL. Download it into the project folder as `al-baqarah-2-286-abdulbasit.mp3`. If that fails, get the same reciter's audio for Surah 2 ayah 286 from Quran.com / EveryAyah (`ar.abdulbasitmurattal`, ayah 293).
- IMPORTANT: the API returns the FULL ayah 286, but this video uses ONLY its first part (text below). Transcribe the audio with local Whisper (small model, already installed), find the exact end of the words "وَعَلَيْهَا مَا اكْتَسَبَتْ", and TRIM the audio there (expected roughly 20 seconds). Use only the trimmed audio in the video — nothing after that point.
- Verify the audio: report the exact duration of the trimmed audio.

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4` and `ayat-al-kursi-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Produce the Al-Baqarah video
- Background: a person alone at sunset. Free stock footage only, no paid assets.
- Text: ONLY the first part of the ayah in Uthmani script, large white, centred above the middle:
  لَا يُكَلِّفُ اللَّهُ نَفْسًا إِلَّا وُسْعَهَا ۚ لَهَا مَا كَسَبَتْ وَعَلَيْهَا مَا اكْتَسَبَتْ
- Show the text in lines that appear progressively as recited. Each spoken word turns GOLD exactly when it is spoken — get word-level timestamps by transcribing the audio with local Whisper (small model, already installed) or from the Quran.com word-timing API (the method used for ayat-al-kursi-v1).
- English translation underneath in small white text (Sahih International): "Allah does not charge a soul except [with that within] its capacity. It will have [the consequence of] what [good] it has gained, and it will bear [the consequence of] what [evil] it has earned." — IMPORTANT: do NOT show one static translation line for the whole video (lesson from the Ayat al-Kursi v1 review). Show the translation in parts, changing as the recitation moves through the text.
- Top label: "سورة البقرة - 286" and "AL-BAQARAH 2:286".
- Last second of the video: "تابع للمزيد" + "القارئ: عبد الباسط عبد الصمد".
- Pure recitation, no music.
- Render to `al-baqarah-2-286-part1-v1.mp4`, 1080x1920, under 60 seconds.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 4 — Report back
- Tell me: the exact output file path, duration, file size, and total cost (must be $0).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
