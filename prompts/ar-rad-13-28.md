# Ar-Ra'd 13:28 — copy-ready instructions for OpenCode (OpenMontage, already installed)

## Goal
Produce ONE video: Ar-Ra'd (Surah 13), ayah 28, reciter Abdulrahman Al-Sudais, in the same style as my existing reference videos (duha-93-5-v2.mp4 and ayat-al-kursi-v1.mp4, both 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- OpenMontage, Python 3.12, FFmpeg, git, Whisper (small model) and the Arabic fonts were already installed — check first, do NOT reinstall anything that already works. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Step 1 — Get the recitation audio (licensed)
- Ar-Ra'd = Surah 13, ayah 28.
- Reciter: Abdulrahman Al-Sudais.
- Fetch the MP3 from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/13:28/ar.abdurrahmaansudais`
  The JSON response contains the audio URL. Download it into the project folder as `ar-rad-13-28-sudais.mp3`. If that fails, get the same reciter's audio for Surah 13 ayah 28 from Quran.com / EveryAyah (`ar.abdurrahmaansudais`).
- Verify the audio: report its exact duration (expected roughly 20 seconds).

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4` and `ayat-al-kursi-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Produce the Ar-Ra'd video
- Background: sunrise over the Haram (morning video). Free stock footage only, no paid assets.
- Text: the ayah in Uthmani script, large white, centred above the middle:
  الَّذِينَ آمَنُوا وَتَطْمَئِنُّ قُلُوبُهُم بِذِكْرِ اللَّهِ ۗ أَلَا بِذِكْرِ اللَّهِ تَطْمَئِنُّ الْقُلُوبُ
- Show the ayah in lines that appear progressively as recited. Each spoken word turns GOLD exactly when it is spoken — get word-level timestamps by transcribing the audio with local Whisper (small model, already installed) or from the Quran.com word-timing API (the method used for ayat-al-kursi-v1).
- Start the text and the gold highlight immediately — the first words must be visible in the first 2 seconds (no slow fade-in).
- English translation underneath in small white text (Sahih International): "Those who have believed and whose hearts find rest in the remembrance of Allah. Unquestionably, by the remembrance of Allah hearts are assured."
- Top label: "سورة الرعد - 28" and "AR-RA'D 13:28".
- Last second of the video: "تابع للمزيد" + "القارئ: عبد الرحمن السديس".
- Pure recitation, no music.
- Render to `ar-rad-13-28-v1.mp4`, 1080x1920, under 60 seconds.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 4 — Report back
- Tell me: the exact output file path, duration, file size, and total cost (must be $0).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
