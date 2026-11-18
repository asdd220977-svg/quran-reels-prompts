# Quran Reel — Ash-Sharh 94:5-6 — copy-ready instructions for OpenCode

## Goal
Produce ONE video: Ash-Sharh (Surah 94), ayahs 5-6, reciter Maher Al-Muaiqly, in the same style as my existing reference videos (duha-93-5-v2.mp4 and ayat-al-kursi-v1.mp4, both 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- OpenMontage, Python 3.12, FFmpeg, git, Whisper (small model) and the Arabic fonts were already installed yesterday — check first, do NOT reinstall anything that already works. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Step 1 — Get the recitation audio (licensed)
- Ash-Sharh = Surah 94, ayahs 5 and 6.
- Reciter: Maher Al-Muaiqly.
- Fetch the MP3s from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/94:5/ar.mahermuaiqly`
  - `GET https://api.alquran.cloud/v1/ayah/94:6/ar.mahermuaiqly`
  The JSON responses contain the audio URLs. Download both and join them in order (ayah 5 then ayah 6) into one file `ash-sharh-94-5-6-muaiqly.mp3` in the project folder. If that fails, get the same reciter's audio for Surah 94 ayahs 5-6 from Quran.com / EveryAyah (`ar.mahermuaiqly`).
- Verify the audio: report its exact duration (expected roughly 15–20 seconds).

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4` and `ayat-al-kursi-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Produce the Ash-Sharh video
- Background: light rain / mountain road. Free stock footage only, no paid assets.
- Text: the two ayahs in Uthmani script, large white, centred above the middle:
  فَإِنَّ مَعَ الْعُسْرِ يُسْرًا ۝ إِنَّ مَعَ الْعُسْرِ يُسْرًا
- Show the ayahs in lines that appear progressively as recited. Each spoken word turns GOLD exactly when it is spoken — get word-level timestamps by transcribing the audio with local Whisper (small model, already installed) or from the Quran.com word-timing API (the method used for ayat-al-kursi-v1).
- English translation underneath in small white text (Sahih International): "For indeed, with hardship [will be] ease." — IMPORTANT: do NOT show one static translation line for the whole video (lesson from the Ayat al-Kursi v1 review). Show this translation line while ayah 5 is recited, then show it again while ayah 6 is recited.
- Top label: "سورة الشرح - 5-6" and "ASH-SHARH".
- Last second of the video: "تابع للمزيد" + "القارئ: ماهر المعيقلي".
- Pure recitation, no music.
- Render to `ash-sharh-94-5-6-v1.mp4`, 1080x1920, under 60 seconds.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 4 — Report back
- Tell me: the exact output file path, duration, file size, and total cost (must be $0).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
