# AIChatBuddyHTML

https://dylan7474.github.io/AIChatBuddyHTML

A voice chat with an animated robot avatar, in a single HTML page. Click the
button and speak. Gemini answers, reads its reply aloud, and the avatar's
mouth moves with the voice.

## Getting started

1. Get a Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Open the page and paste the key into the bar under the header, then press Save.
   The key is stored only in your browser. The key icon in the top bar shows the bar again.
3. Click **Click to Speak** and talk.

Speech recognition needs Chrome or Edge, and the page has to be allowed to use the microphone.

## Files

- `index.html`: the current version. It uses `gemini-3-flash-preview` for replies and
  `gemini-2.5-flash-preview-tts` for the voice. In Gemini Canvas it uses the
  key Canvas provides.
- `basic.html`: an earlier version, opened at
  https://dylan7474.github.io/AIChatBuddyHTML/basic.html. It remembers the conversation
  and asks for the API key the same way.
