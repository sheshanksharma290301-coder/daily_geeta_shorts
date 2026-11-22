# Shloka Database

- File: `data/shlokas.csv`
- Columns: `id, chapter, verse, sanskrit, transliteration, hindi_meaning, theme, status, upload_date`
- `id` sequence number hai (Ch 1.1 = id 1, aage badhta hai).

## Status Values
`pending`, `script_ready`, `voice_ready`, `clips_ready`, `video_ready`, `pr_open`, `uploaded`

## Sourcing Rules
- Sanskrit text **Gita Press Gorakhpur** ya kisi trusted edition / verified open dataset se aayega.
- AI se generate kiya gaya Sanskrit **kabhi** DB me nahi jaayega.
- Sanskrit hamesha Devanagari me.
- DB ek baar bhar ke verify karni hai. Uske baad agents ise **read-only** treat karte hain (sirf `status` aur `upload_date` update hote hain).

## TODO
- [ ] Source finalize karna (dataset ya manual entry)
- [ ] Pehle 10 shlokas manually verify karna
- [ ] `theme` column ka vocabulary decide karna
