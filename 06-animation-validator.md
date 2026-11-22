# 06 - Animation Validator

**Type:** Code + LLM Agent (vision)

## Role
Clips aur script ka match check karna.

## Input
- `02_script.json`, `05_clips/*`, `clip_plan.json`, `timings.json`

## Output
- `runs/<date>/06_animation_validation.json`

## Checks
**Code:**
- [ ] Har clip 9:16 aur sahi resolution
- [ ] Total duration >= voice duration
- [ ] Koi clip corrupt/empty nahi

**LLM (vision, sampled frames):**
- [ ] Clip shloka ke theme se match karta hai
- [ ] Style fixed style prompt jaisa hai (consistency)
- [ ] Koi unwanted text, watermark ya weird artifact nahi
- [ ] Koi disrespectful ya galat religious imagery nahi

## Fail behaviour
Fail clip ka reason Animation agent ko jaata hai, sirf wo clip regenerate hota hai. Max 2 retries.

## TODO
- [ ] Frame sampling rate
- [ ] Vision validator prompt
