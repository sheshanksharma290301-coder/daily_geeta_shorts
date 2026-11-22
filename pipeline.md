# Pipeline

## Daily Flow
1. **Pick**: next shloka + sequence check (code)
2. **Script**: anuvaad, bhavarth, caption draft (agent)
3. **Validate script**: exact Sanskrit match + Hindi quality check
4. **Voice**: Sanskrit + Hindi audio, segment-wise durations
5. **Animation**: voice duration ke hisaab se Higgsfield clips
6. **Validate animation**: clips theme aur script se match karte hain?
7. **Edit**: clips + voice + Devanagari subtitles + music (ffmpeg/Remotion)
8. **Validate final video**: duration, resolution, audio, subtitle safe area
9. **Publish**: branch + Pull Request
10. **Manual**: aap PR review karo, merge karo, YouTube par upload karo

## Video Structure (30-60 sec)
| Time | Part | Content |
|---|---|---|
| 0-3s | Hook | Chapter/Shloka number + ek line ka title (e.g. "Gita Adhyay 2, Shloka 47") |
| 3-20s | Sanskrit paath | Shloka dhire aur shuddh uchcharan me, Devanagari text screen par |
| 20-45s | Hindi anuvaad | Saral Hindi me arth + 1-2 line ka bhavarth |
| 45-55s | Closing | Ek line ki seekh + "Roz ek shloka, follow karein" |

## Run Folder Contract
Har agent **input files padhta hai aur output files likhta hai**. Agents ek dusre se seedha baat nahi karte, sirf files ke through. Isse debugging aur resume aasaan hota hai.

```
runs/2026-11-23/
├── 01_pick.json              <- picker output
├── 02_script.json            <- script writer output
├── 03_script_validation.json
├── 04_voice/
│   ├── voice_sanskrit.mp3
│   ├── voice_hindi.mp3
│   ├── voice_full.mp3
│   └── timings.json          <- har segment ki duration
├── 05_clips/
│   ├── clip_01.mp4 ...
│   └── clip_plan.json
├── 06_animation_validation.json
├── 07_final.mp4
├── 08_final_validation.json
└── run_log.json              <- status, retries, cost
```

## script.json Schema
```json
{
  "id": 47,
  "chapter": 2,
  "verse": 47,
  "sanskrit": "<DB se exact copy>",
  "transliteration": "",
  "hindi_anuvaad": "",
  "bhavarth": "",
  "closing_line": "",
  "visual_theme": "",
  "caption": "",
  "hashtags": []
}
```

## Status Flow (shlokas.csv)
`pending -> script_ready -> voice_ready -> clips_ready -> video_ready -> pr_open -> uploaded`

`uploaded` tab set hota hai jab aap PR merge karte ho (ya manually update karte ho).

## Failure Policy
- Har validator: `pass/fail + reason`.
- Fail par generator agent ko reason ke saath retry, **max 2-3 baar**.
- Retries khatam hone par pipeline ruk jaati hai aur aapko alert jaata hai (GitHub issue / email). Koi infinite loop nahi, taaki API cost na jale.
- Har step ka output save hota hai, isliye fail hone par wahin se resume ho sakta hai.
