# 00 - Orchestrator

**Type:** Code (script, GitHub Actions se trigger)

## Role
Daily cron par chalta hai, agents ko order me call karta hai, retries aur failures handle karta hai.

## Input
- `data/shlokas.csv`
- Config (budget cap, max retries)

## Output
- `runs/<date>/run_log.json` (status, retries, cost)
- Failure par alert

## Rules
- Order: 01 -> 02 -> 03 -> 04 -> 05 -> 06 -> 07 -> 08 -> 09
- Voice (04) animation (05) se pehle chalti hai.
- Har step ka output `runs/<date>/` me save hota hai. Resume wahin se hota hai.
- Validator fail hone par generator agent ko fail reason ke saath dobara call karta hai.
- Max retries per step: 3. Uske baad pipeline stop + alert.
- Daily Higgsfield spend cap cross hone par stop.
- Ek din me ek hi run (duplicate run se bachne ke liye run folder check karna).

## Trigger
GitHub Actions: daily cron + manual `workflow_dispatch` (testing ke liye).

## TODO
- [ ] Cron time decide karna
- [ ] Budget cap value
- [ ] Alert channel
