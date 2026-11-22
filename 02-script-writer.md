# 02 - Script Writer

**Type:** LLM Agent

## Role
Shloka ke liye Hindi anuvaad, bhavarth, closing line, visual theme aur caption/hashtags ka draft banana.

## Input
- `01_pick.json`
- `docs/style-guide.md`
- (Retry par) validator ka fail reason

## Output
- `runs/<date>/02_script.json` (schema: `docs/pipeline.md`)

## Rules
- **Sanskrit text agent likhta nahi hai.** Wo DB se copy hota hai. Agent use sirf padh sakta hai.
- Hindi saral ho, 1 anuvaad + 1-2 line bhavarth.
- Anuvaad ka style: (pending, `open-questions.md`).
- Closing line ek line ki seekh + "Roz ek shloka, follow karein".
- Length aisi ho ki voice 30-60 sec me aaye. Rough guide: Sanskrit 15-20 sec, Hindi 20-25 sec.
- Visual theme ek short phrase (e.g. "Kurukshetra, sunrise, divine light").
- Caption + 5-8 hashtags.
- Koi aisa claim nahi jo shloka me na ho.

## Prompt
_(TODO: final system prompt yahan likhna)_

## TODO
- [ ] Anuvaad style finalize
- [ ] 3-5 example scripts (few-shot) add karna
