# 04 - Voice

**Type:** Agent / API call (ElevenLabs ya final tool)

## Role
Validated script ka voice over banana aur timings dena.

## Input
- `02_script.json`
- `docs/style-guide.md`

## Output
- `04_voice/voice_sanskrit.mp3`, `voice_hindi.mp3`, `voice_full.mp3`
- `04_voice/timings.json` (har segment ki start/end/duration)

## Rules
- Same voice roz (voice ID config me fixed).
- Sanskrit text Devanagari me hi TTS ko dena.
- Slow, shaant pace.
- Sanskrit aur Hindi ke beech 0.5-1 sec pause.
- **Self-check:** final audio ko speech-to-text (Whisper) se transcribe karke script se compare karo. Badi mismatch ho to retry ya flag.
- Total duration 30-60 sec. Bahar ho to script wapas Script Writer ko (length issue).

## Fail behaviour
STT mismatch / duration out of range -> retry (settings badal ke), phir alert.

## TODO
- [ ] Pehle 5-10 shlokas par pronunciation test
- [ ] Voice tool + voice ID final
- [ ] STT mismatch threshold
