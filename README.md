# Daily Bhagavad Gita Shorts

_Last updated: 22 Nov 2026 (v0.2)_

Roz ek Bhagavad Gita shloka ka vertical Short: pehle Sanskrit paath, phir Hindi anuvaad. Poori pipeline AI agents + code se chalti hai, GitHub Actions par. Final upload manual hota hai.

## Confirmed Decisions
| Item | Decision |
|---|---|
| Format | Vertical Shorts/Reels (9:16, 1080x1920) |
| Length | 30-60 seconds |
| Voice | Male, calm, shaant, gambhir |
| Animation tool | Higgsfield **API** (website plan se alag; USD prepaid balance) |
| Voice tool | ElevenLabs (final decision pending, Sanskrit test ke baad) |
| Orchestration | GitHub Actions daily cron + orchestrator script |
| Output delivery | GitHub Pull Request (PR = review gate) |
| Upload | Manual YouTube Shorts (merge ke baad) |
| Frequency | Daily, 1 shloka per video |

## Architecture (ek line me)
`Picker (code) -> Script Writer -> Script Validator -> Voice -> Animation -> Animation Validator -> Edit (code) -> Final Validator -> GitHub PR -> (aap) manual upload`

> Note: Voice animation se **pehle** aati hai, kyunki voice ki duration se pata chalta hai ki kitne seconds ke clips chahiye.

## Folder Structure
```
gita-shorts/
├── README.md                  <- ye file (index)
├── CHANGELOG.md
├── docs/
│   ├── pipeline.md            <- flow, video structure, run folder contract
│   ├── shloka-database.md     <- CSV schema, status values, sourcing
│   ├── style-guide.md         <- voice, visual, subtitle guidelines
│   └── open-questions.md
├── agents/
│   ├── 00-orchestrator.md
│   ├── 01-shloka-picker.md
│   ├── 02-script-writer.md
│   ├── 03-script-validator.md
│   ├── 04-voice.md
│   ├── 05-animation.md
│   ├── 06-animation-validator.md
│   ├── 07-edit-assembly.md
│   ├── 08-final-validator.md
│   └── 09-github-publisher.md
├── data/shlokas.csv
└── runs/YYYY-MM-DD/           <- har din ka output (auto-generated)
```

## Agent Index
| # | File | Type | Kaam |
|---|---|---|---|
| 00 | [orchestrator](agents/00-orchestrator.md) | Code | Sab agents ko order me chalata hai, retries aur alerts handle karta hai |
| 01 | [shloka-picker](agents/01-shloka-picker.md) | Code | Next shloka + sequence validation |
| 02 | [script-writer](agents/02-script-writer.md) | Agent | Anuvaad, bhavarth, caption draft |
| 03 | [script-validator](agents/03-script-validator.md) | Code + Agent | Script check |
| 04 | [voice](agents/04-voice.md) | Agent/API | Voice over + timings |
| 05 | [animation](agents/05-animation.md) | Agent | Higgsfield clips |
| 06 | [animation-validator](agents/06-animation-validator.md) | Code + Agent | Clips + script match check |
| 07 | [edit-assembly](agents/07-edit-assembly.md) | Code | ffmpeg/Remotion se final video |
| 08 | [final-validator](agents/08-final-validator.md) | Code + Agent | Final video QA |
| 09 | [github-publisher](agents/09-github-publisher.md) | Code | Branch + PR |

## Rule: Har agent file me kya hona chahiye
Har agent file ka same structure: **Role, Type, Input, Output, Rules, Validation / Fail behaviour, Prompt, TODO**. Naye instructions sirf us agent ki file me jaate hain, taaki ek file lambi na ho.
