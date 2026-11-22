# 05 - Animation

**Type:** LLM Agent + Higgsfield API

## Role
Shloka ke theme ke hisaab se clips generate karna, voice ki duration ke hisaab se.

## Input
- `02_script.json` (visual_theme)
- `04_voice/timings.json`
- `docs/style-guide.md` (fixed style prompt)

## Output
- `05_clips/clip_plan.json` (scene list, har clip ka prompt aur duration)
- `05_clips/clip_01.mp4 ...`

## Rules
- Fixed style prompt hamesha same, sirf scene badalna.
- Clips 5-10 sec, slow camera movement, 9:16.
- Total clip duration >= voice duration (thoda extra trim ke liye).
- Higgsfield API **async** hai: job submit karo, status ~30 sec ke gap par poll karo jab tak `completed` ya `failed`.
- Resubmit tabhi karo jab job `failed` ho (stuck dikhne par naya job mat daalo).
- Cost log karo (`run_log.json`), daily cap check karo.
- Clips me **text/Devanagari generate mat karwao**. Subtitles edit stage par aate hain.
- Clips reuse/loop allowed hain cost bachane ke liye.

## Fail behaviour
Job failed -> max 2 retry (prompt thoda badal ke). Budget cap hit -> stop + alert.

## TODO
- [ ] Higgsfield model choose karna (cost vs quality)
- [ ] API key GitHub Secrets me
- [ ] Reuse/loop strategy (weekly batch?)
