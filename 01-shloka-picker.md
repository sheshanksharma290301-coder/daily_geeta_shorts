# 01 - Shloka Picker

**Type:** Code (LLM nahi chahiye, deterministic logic)

## Role
Aaj ka shloka nikalna aur sequence validate karna.

## Input
- `data/shlokas.csv`

## Output
- `runs/<date>/01_pick.json` (id, chapter, verse, sanskrit, theme)

## Rules
- Last `uploaded` id dhundho. Next id = last + 1.
- Sequence validation:
  - Agar koi id skip hui hai (gap), ya `uploaded` me duplicate hai, to **stop + alert**.
  - Agar pichla shloka abhi `pr_open` hai (merge nahi hua), to alert: "pichla video abhi upload nahi hua". Aage badhna hai ya rukna hai, ye config se.
- Sanskrit text DB se as-is copy hota hai.
- Pick karne ke baad status `pending` hi rehta hai, `script_ready` tab hota hai jab script validate ho jaye.

## Fail behaviour
Sequence galat ho to run ruk jaata hai, koi agent aage nahi chalta.

## TODO
- [ ] "pichla PR pending hai" case ka final behaviour (wait ya aage badho)
