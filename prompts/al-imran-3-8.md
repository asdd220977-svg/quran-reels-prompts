# Al-Imran 3:8 — copy-ready instructions for OpenCode (OpenMontage, already installed)

## Goal
Produce ONE video: Al-Imran (Surah 3), ayah 8, reciter Ahmed bin Ali Al-Ajmi, in the same style as my existing reference videos (`duha-93-5-v2.mp4`, `ayat-al-kursi-v1.mp4` and `al-qamar-54-10-v1.mp4`, all 1080x1920) — using the OpenMontage setup already installed in `C:\Users\USER\OpenMontage`.

The ayah text below is ALREADY APPROVED. Do not stop to ask for text approval; build the video.

## Rules
- Work ONLY inside `C:\Users\USER\OpenMontage`. Do not touch any other folder or project.
- FREE path only: zero API keys, no paid providers, no paid models. Do not spend any money.
- Already installed — do NOT reinstall: OpenMontage + `.venv` (Python 3.12), FFmpeg 9, Node/Remotion (`remotion-composer/node_modules` present), faster-whisper 1.2.1 with the `small` model cached, and the fonts `Shah-Bold.ttf` / `Shah-Regular.ttf` / `Inter.ttf` in `remotion-composer/public/ayat`. Ask me before installing anything new or big.
- Do NOT publish the video anywhere. I review it first.

## Known-good pipeline (reuse it, do not reinvent)
- Previous video: `al-qamar-54-10-v1.mp4` + `README-al-qamar-54-10.md` at the root.
- Template composition: `remotion-composer/src/AlQamar.tsx` (copy to `AlImran.tsx`, register as **`AlImran`** in `Root.tsx`).
- Template props: `remotion-composer/public/qamar/props.json` (copy to `public/imran/props.json`).
- Word timings: `scripts/alqamar_whisper.py` (adapt paths and `initial_prompt`).

## Step 1 — Get the recitation audio (licensed)
- Al-Imran = Surah 3, ayah 8.
- Reciter: Ahmed bin Ali Al-Ajmi.
- Fetch the MP3 from the AlQuran Cloud API:
  - `GET https://api.alquran.cloud/v1/ayah/3:8/ar.ahmedajamy`
  The JSON response contains the audio URL. Download it as `al-imran-3-8-ajamy.mp3` in `assets/audio/` and copy it to `remotion-composer/public/imran/`. If that fails, get the same reciter's audio for 3:8 from Quran.com / EveryAyah (`ar.ahmedajamy`, global ayah 301).
- Verify the audio: report its exact duration (expected roughly 15–18 seconds).

## Step 2 — Reference style
- My reference videos are `duha-93-5-v2.mp4`, `ayat-al-kursi-v1.mp4` and `al-qamar-54-10-v1.mp4` in the same folder. Analyse them first: layout, fonts, colours, pacing, caption style.
- Target video must match this style: 9:16, 1080x1920, MP4, under 60 seconds.

## Step 3 — Word-level timings
- Quran.com's QDC segment API has no Al-Ajmi reciter. Use local faster-whisper `small` (int8, CPU), `language="ar"`, `word_timestamps=True`, `vad_filter=False`, `initial_prompt` = the ayah text below.
- Save to `analysis/imran/whisper.json` and report every word boundary.
- Whisper may split or merge words; map its boundaries onto the display lines below. Keep word 1 at 0 ms and the last word ending at its real end.

## Step 4 — Produce the Al-Imran 3:8 video
Ayah text (Uthmani, exactly as written):
رَبَّنَا لَا تُزِغْ قُلُوبَنَا بَعْدَ إِذْ هَدَيْتَنَا وَهَبْ لَنَا مِن لَّدُنكَ رَحْمَةً ۚ إِنَّكَ أَنتَ الْوَهَّابُ

- Show the ayah in 3 lines that appear progressively as recited:
  1. رَبَّنَا لَا تُزِغْ قُلُوبَنَا
  2. بَعْدَ إِذْ هَدَيْتَنَا وَهَبْ لَنَا مِن لَّدُنكَ رَحْمَةً
  3. إِنَّكَ أَنتَ الْوَهَّابُ
  If line 2 overflows, split it after "هَدَيْتَنَا" (4 lines total) and say so.
- Each spoken word turns GOLD exactly when it is spoken. Start the text and the gold highlight immediately — the first words must be visible in the first 2 seconds (no slow fade-in).
- Measure each line with uharfbuzz/Shah-Bold and choose the largest font size (≤ 112 px) that leaves at least ~120 px side margins. Keep ~160 px leading.
- Background: warm light through trees or a mosque window (guidance/light mood). Free stock only, vertical 9:16, no paid assets and no API key. Pexels search pages can be read with webfetch (HTML) and the direct `videos.pexels.com` contentUrl downloaded without a key; a high-res still plate with a slow push-in is acceptable if no free clip fits. Report the exact source, author and licence.
- English translation underneath in small white text (Sahih International): "[Who say], 'Our Lord, let not our hearts deviate after You have guided us and grant us from Yourself mercy. Indeed, You are the Bestower.'"
- Top label: "سورة آل عمران - 8" and "AL-IMRAN 3:8".
- Last second of the video: "تابع للمزيد" + "القارئ: أحمد بن علي العجمي".
- Pure recitation, no music.
- Render to `al-imran-3-8-v1.mp4` (also in `projects\al-imran-3-8\renders\`), 1080x1920, 30 fps, under 60 seconds.
- Check the audio peak with `volumedetect`; if it hits 0 dB, trim ~3.5 dB and re-mux (copy video, re-encode audio) as done for `al-qamar-54-10-v1`.
- If OpenMontage cannot do the word-by-word gold highlight properly, say so clearly and fall back to the FFmpeg method used for the Duha v2 (render the Arabic text as PNGs with PIL + raqm, overlay with FFmpeg timed to the Whisper word timings) — and report that you did.

## Step 5 — Report back
- Tell me: the exact output file path, duration, file size, audio mean/peak, and total cost (must be $0).
- Say clearly that word timings come from Whisper (QDC has no Al-Ajmi).
- List anything that did not match the reference style and why.
- Do not publish anything. I review the video first.
