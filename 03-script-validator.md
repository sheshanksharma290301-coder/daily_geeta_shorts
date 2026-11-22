# 03 - Script Validator

**Type:** Code + LLM Agent

## Role
Script ko voice/animation me jaane se pehle check karna.

## Input
- `01_pick.json`, `02_script.json`

## Output
- `runs/<date>/03_script_validation.json` (`pass/fail`, reasons)

## Checks
**Code (deterministic):**
- [ ] `sanskrit` DB wale text se **exact match** (character-level)
- [ ] Sanskrit Devanagari me hai (koi Roman nahi)
- [ ] Saare fields bhare hain
- [ ] Estimated length 30-60 sec ke andar

**LLM:**
- [ ] Hindi anuvaad shloka ke arth se match karta hai
- [ ] Hindi saral aur natural hai
- [ ] Bhavarth overreach nahi kar raha (shloka se zyada claim nahi)
- [ ] Caption/hashtags theek hain

## Fail behaviour
Fail reason Script Writer ko jaata hai. Max 3 retries, phir stop + alert.
Pass par DB status -> `script_ready`.

## TODO
- [ ] LLM validator ke liye checklist prompt
