# 07 - Edit & Assembly

**Type:** Code (ffmpeg / Remotion)

## Role
Clips + voice + subtitles + music ko jod ke final video banana.

## Input
- `05_clips/*`, `04_voice/*`, `02_script.json`

## Output
- `runs/<date>/07_final.mp4`

## Rules
- 1080x1920, 30fps (ya jo final ho).
- Hook (0-3s): "Gita Adhyay X, Shloka Y" + title.
- Devanagari subtitles Noto Sans Devanagari me, voice timings ke saath sync.
- Subtitles bottom ke safe area se bahar.
- Background music halka, voice ke neeche (ducking).
- Audio loudness normalize.
- Total 30-60 sec.

## TODO
- [ ] ffmpeg vs Remotion final karna
- [ ] Hook design / branding (logo, intro/outro)
- [ ] Music source
- [ ] Subtitles Sanskrit + Hindi dono ya sirf ek
