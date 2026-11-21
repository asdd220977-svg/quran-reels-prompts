# Al-Mu'minun 23:118 — copy-ready instructions for OpenCode (OpenMontage, already installed)

## Goal
Produce ONE video: Al-Mu'minun (Surah 23), ayah 118, reciter Ahmed bin Ali Al-Ajmi, in the same style as my existing reference videos (`duha-93-5-v2.mp4`, `ayat-al-kursi-v1.mp4` and `al-qamar-54-10-v1.mp4`, all 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

The ayah text below is ALREADY APPROVED. Do not stop to ask for text approval; build the video.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- Already installed — do NOT reinstall: OpenMontage + `.venv` (Python 3.12), FFmpeg 9, Node/Remotion (`remotion-composer/node_modules` present), faster-whisper 1.2.1 with the `small` model cached, and the fonts `Shah-Bold.ttf` / `Shah-Regular.ttf` / `Inter.ttf` in `remotion-composer/public/ayat`. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Known-good pipeline (reuse it, do not reinvent)
- Previous video: `al-qamar-54-10-v1.mp4` + `README-al-qamar-54-10.md` at the root.
- Template composition: `remotion-composer/src/AlQamar.tsx` (copy to `AlMuminun.tsx`, register as **`AlMuminun`** in `Root.tsx`).
- Template props: `remotion-composer/public/qamar/props.json` (copy to `public/muminun/props.json`).
- Word timings: `scripts/alqamar_whisper.py` (adapt paths and `initial_prompt`).

## Step 1 — Get the recitation audio (licensed)
- Al-Mu'minun = Surah 23, ayah 118.
- Reciter: Ahmed bin Ali Al-Ajmi.
- Fetch the MP3 from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/23:118/ar.ahmedajamy`
  The JSON response contains the audio URL. Download it as `al-muminun-23-118-ajamy.mp3` in `assets/audio/` and copy it to `remotion-composer/public/muminun/`. If that fails, get the same reciter's audio for 23:118 from Quran.com / EveryAyah (`ar.ahmedajamy`, global ayah 2791).
- Verify the audio: report its exact duration (expected roughly 5–7 seconds).

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4`, `ayat-al-kursi-v1.mp4` and `al-qamar-54-10-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Word-level timings
- Quran.com's QDC segment API has no Al-Ajmi reciter. Use local faster-whisper `small` (int8, CPU), `language="ar"`, `word_timestamps=True`, `vad_filter=False`, `initial_prompt` = the ayah text below.
- Save to `analysis/muminun/whisper.json` and report every word boundary.
- Keep word 1 at 0 ms and the last word ending at its real end. If Whisper merges two short words, split the span proportionally and say so.

## Step 4 — Produce the Al-Mu'minun 23:118 video
Ayah text (Uthmani, exactly as written):
وَقُل رَّبِّ اغْفِرْ وَارْحَمْ وَأَنتَ خَيْرُ الرَّاحِمِينَ

- Show the ayah in 2 lines that appear progressively as recited:
  1. وَقُل رَّبِّ اغْفِرْ وَارْحَمْ
  2. وَأَنتَ خَيْرُ الرَّاحِمِينَ
- Each spoken word turns GOLD exactly when it is spoken. Start the text and the gold highlight immediately — the first words must be visible in the first 2 seconds (no slow fade-in).
- Because the ayah is short, use large type: measure with uharfbuzz/Shah-Bold and choose the largest size (≤ 120 px) that leaves at least ~120 px side margins. Keep ~160 px leading.
- Background: night sky / soft clouds with faint stars (calm, quiet mood). Free stock only, vertical 9:16, no paid assets and no API key. Pexels search pages can be read with webfetch (HTML) and the direct `videos.pexels.com` contentUrl downloaded without a key. Report the exact clip, author and licence.
- English translation underneath in small white text (Sahih International): "And, [O Muhammad], say, 'My Lord, forgive and have mercy, and You are the best of the merciful.'"
- Top label: "سورة المؤمنون - 118" and "AL-MU'MINUN 23:118".
- Last second of the video: "تابع للمزيد" + "القارئ: أحمد بن علي العجمي".
- Pure recitation, no music.
- Render to `al-muminun-23-118-v1.mp4` (also in `projects\al-muminun-23-118\renders\`), 1080x1920, 30 fps, under 60 seconds. Since the recitation is ~6 s, keep a ~1.2 s outro tail like `al-qamar-54-10-v1`.
- Check the audio peak with `volumedetect`; if it hits 0 dB, trim ~3.5 dB and re-mux (copy video, re-encode audio) as done for `al-qamar-54-10-v1`.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 5 — Report back
- Tell me: the exact output file path, duration, file size, audio mean/peak, and total cost (must be $0).
- Say clearly that word timings come from Whisper (QDC has no Al-Ajmi).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
