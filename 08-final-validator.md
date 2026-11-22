# 08 - Final Validator

**Type:** Code + LLM Agent

## Role
Final video ko GitHub me jaane se pehle QA karna.

## Input
- `07_final.mp4`, `02_script.json`, `timings.json`

## Output
- `runs/<date>/08_final_validation.json`

## Checks
**Code:**
- [ ] Duration 30-60 sec
- [ ] Resolution 1080x1920
- [ ] Audio loudness target range me
- [ ] Audio track present, silence gaps nahi
- [ ] File size reasonable

**Speech check:**
- [ ] Final audio STT se transcribe karke script se compare

**LLM (vision, sampled frames):**
- [ ] Subtitles safe area me, kate hue nahi
- [ ] Subtitle text script se match
- [ ] Koi visual glitch nahi

## Fail behaviour
Issue ke type ke hisaab se sahi step par wapas bhejna (subtitle issue -> 07, voice issue -> 04, visual issue -> 05). Max retries ke baad stop + alert.
Pass par DB status -> `video_ready`.

## TODO
- [ ] Loudness target (LUFS)
- [ ] Frame sampling + vision prompt
