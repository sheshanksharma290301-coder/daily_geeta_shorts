# 09 - GitHub Publisher

**Type:** Code

## Role
Validated video ko GitHub par push karna taaki aap review karke manual upload kar sako.

## Input
- `07_final.mp4`, `02_script.json`, validation reports

## Output
- Branch `video/<id>-ch<chapter>-v<verse>`
- Pull Request

## PR Content
- Title: `Gita Ch <chapter>.<verse> (id <id>)`
- Body: script (Sanskrit + Hindi), caption + hashtags, validation summary, cost
- Files: final video, script.json, validation reports

## Rules
- Videos bade hote hain: **Git LFS ya GitHub Releases** use karo, warna repo bhar jayega.
- Direct `main` me push nahi, hamesha PR.
- PR merge = "approved" signal. Merge par DB status -> `uploaded` (ya aap manually set karo upload ke baad).
- Status push ke waqt `pr_open`.

## Aapka manual step
1. PR kholo, video dekho, Sanskrit uchcharan aur text check karo.
2. Theek ho to download karke YouTube Shorts par upload karo (caption PR me hai).
3. PR merge karo.

## TODO
- [ ] LFS vs Releases decide karna
- [ ] Merge par status auto-update workflow
