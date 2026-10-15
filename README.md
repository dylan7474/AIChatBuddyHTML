# AIChatBuddyHTML

https://dylan7474.github.io/AIChatBuddyHTML

A voice chat with an animated robot, in a single HTML page. Press **Start conversation** and just
talk, as on a phone call: Gemini answers in its own voice straight away, you can talk over it, and the
robot's face moves with what it says and how it feels.

## Getting started

1. Get a Gemini API key from [Google AI Studio](https://aistudio.google.com/apikey).
2. Open the page and paste the key into the bar under the header, then press Save.
   The key is stored only in your browser. The key icon in the top bar shows the bar again.
3. Press **Start conversation**, allow the microphone, and talk. **End conversation** hangs up.
   You can also type in the box under the chat.

The sliders icon opens the settings: the **voice** (used from the next conversation) and **Let me
interrupt it**. Turn that off if the robot keeps cutting itself off: its own voice from loud speakers
is reaching the microphone. Headphones avoid that altogether.

**Watch me with the camera** (also in the settings, off until you turn it on): the robot turns to keep
looking at you, notices when you sit down, looks about for you when you leave (and dozes off if you're
gone a while), and smiles back when you smile. The picture is read in your browser by Google's MediaPipe
face tracker (in a background worker, so the page never stalls) and never sent anywhere, Gemini included;
only a picture the robot takes with *look* is sent. If it seems to look past you, sit as you usually
do, look at it, and press **Look at me**.

## How it works

- **Gemini Live** (`gemini-3.8-live`): one WebSocket for the whole conversation. The microphone is
  streamed as 16 kHz audio; the reply streams back as 24 kHz audio and starts playing as it arrives.
  Gemini hears when you start and stop talking, and stops when you talk over it. Transcripts of both
  sides fill the chat. A dropped connection, or the session's time limit, reconnects where it was.
- **Memory**: after each conversation Gemini updates a few notes about you (your name, what you're into,
  recent topics, things coming up to ask about), and the robot reads them at the start of the next one,
  so it can ask how things went. **What I remember** in the settings shows the notes: edit them, wipe them,
  or turn remembering off. They're kept only in your browser (the conversation itself goes to Gemini, as
  every conversation does).
- **Look**: ask "can you see this?" or "what do you think of my hat?" and the robot takes one picture
  with your camera (it opens it just for that if *Watch me* is off) and talks about it. The picture it
  sent appears in the chat, so you always see exactly what it saw.
- **The face**: Gemini sets its expression with a `set_expression` tool (happy, excited, laughing,
  surprised, curious, thinking, sad, concerned, embarrassed, annoyed); when it doesn't, the face takes
  a cue from its words. Eyelids, LED brows, blush, mouth corners and colour all change with it.
- **It starts the conversation**: a greeting picked from about 130 openers (for the time of day and the
  day of the week, questions, would-you-rathers, odd facts), never one of the last 40, and a welcome back
  that depends on how long it's been since you last talked. Gemini says it in its own words. Typing a
  message to start skips it.
- **Life**: natural blinks, eyes that look about (and follow the mouse), the head moving with the
  speech's emphasis, nods and glowing ears while you talk, a look up and away while it thinks.
- **Lip sync** from the voice itself: loudness opens the jaw, the sound's colour shapes the lips.

Tested in Chrome; it uses nothing Chrome-only, so Edge, Firefox and Safari should work too (it needs the microphone).

## Files

- `index.html`: the current version, on Gemini Live (`gemini-3.8-live`). In Gemini Canvas it uses
  the key Canvas provides.
- `basic.html`: an earlier, simpler version (press to talk; a reply, then its voice), opened at
  https://dylan7474.github.io/AIChatBuddyHTML/basic.html. It remembers the conversation
  and asks for the API key the same way.
