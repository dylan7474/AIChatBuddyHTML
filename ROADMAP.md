# Roadmap

What's built is described in the [README](README.md); this is what could come next, roughly in the
order it's worth doing.

## Next: small, and worth a lot

1. **Live facts.** The time and date, the weather where you are (Open-Meteo: free, no key), and Google
   Search for anything current, as tools the robot calls mid-conversation. At the moment it only knows
   what the model knew when it was trained.
2. **Timers and reminders.** "Remind me in 20 minutes to check the oven": it speaks up when the time
   comes, with a pay-attention face.
3. **A usage meter.** The Live API reports what each conversation uses; a small figure in the settings
   would show how close you are to the free tier's limits (on a paid key, roughly what it cost).
4. **More mirroring.** It already smiles back; it could look concerned when you frown and share your
   surprise when your eyebrows go up, from the same face tracker.

## Personality

5. **Characters.** Name, voice, accent and personality saved as presets ("Teesside mate", "posh
   butler", "grumpy robot") and switched with one click, each with its own LED colours. A neutral,
   BBC-style British accent belongs here too (the British one now comes out cockney: fun, but not
   always wanted).
6. **Games and activities.** A quiz, 20 Questions, rounds of would-you-rather, and stories told with
   the face acting them out. Mostly instructions and a few expressions.

## Your documents

7. **Ask it about your documents.** A *Documents* panel: drop in PDFs, Word or text files; the text is
   taken out in the browser and kept there, and goes into the robot's instructions at the start of each
   conversation (the Live model holds about 128,000 tokens, so up to roughly 100 pages, leaving room for
   the chat; in the instructions it can't be trimmed away in a long conversation). Then just ask: "what
   does the manual say about resetting it?". The passage it used could show in the chat while it says
   the gist.
8. **A search tool, for big collections.** When there's more than fits, a `search_documents` tool (like
   *look*): the page finds the most relevant passages (keywords, or Gemini embeddings for meaning) and
   the robot answers from those. Scanned PDFs would need text recognition first. On the free tier the
   text sent is used by Google, so keep private papers out.

## Hands-free, and on the desk

9. **A greeting when you sit down.** The camera already sees you arrive; the robot could start the
   conversation itself. Its own switch, with a cooldown, since it opens a connection by itself and,
   on the free tier, counts against the limits.
10. **A desk companion.** An installable, full-screen version for a spare tablet, or a Pi with a small
   screen, microphone and camera: a little robot that lives on the desk, with a quiet sleeping screen
   (a clock on the visor, say) between chats.
11. **The Sleep Radio.** "Play Radio Tees on Nightingale", "what's on 20 metres?": tools that call the
   radio's own API. The catch: this page is served over https, and browsers stop it from calling the
   radio's plain-http address, so it would have to be run locally, served by the radio itself, or reach
   the radio through Cloudflare.

## Housekeeping

12. **Other browsers.** Firefox, Safari and phones: so far everything has been tried in Chrome only.
13. **Memory backup.** Export and import the notes, so a new browser or computer doesn't start afresh.
14. **The key.** A small server (a Cloudflare Worker, say) handing out short-lived keys, so the API key
    needn't sit in the browser if the page is ever shared.

## Later, maybe

- **A 3D body**, with arms and gestures. Only if the 2D robot starts to feel limiting.

## Worth knowing

On the free tier both models this page uses (`gemini-3.8-live` and `gemini-3.8-flash`) are free of
charge: going over a limit gives an error, not a bill, and nothing is charged unless billing is set up
in AI Studio. But Google uses free-tier content to improve its products, so the conversations (your
voice, the transcripts, and any picture the robot takes with *look*) may be used by Google. The face
tracking and the memory notes themselves stay in the browser.
