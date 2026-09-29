# Rebuttalist ideas

Working notes for a real-time response assistant built from the OBS Studio fork. This document records product ideas, not settled requirements.

## Core idea

Help someone respond during a live conversation. The app listens to an exchange, recognizes the question, objection, or argument, and suggests a useful next response quickly enough to use in the moment.

**Working tagline:** Your next response, right on time.

## Audiences and possible modes

- **Debate:** Identify a claim, surface a concise counterargument, and show supporting sources when available.
- **Sales:** Recognize objections, suggest a response and a follow-up question, and avoid unsupported claims.
- **Job interviews:** Help applicants answer questions using their own experience and the job description.

## Possible first version

1. Capture microphone and, where permitted, the other participant's audio.
2. Transcribe speech live and distinguish the user's speech from the other participant's.
3. Detect when a response is needed.
4. Show one short suggested reply, with optional alternatives or supporting detail.
5. Let the user pause listening, hide suggestions, and review or delete session data.

## Design questions to resolve

- Should Rebuttalist be an OBS plugin, a separate desktop app using OBS components, or a full OBS fork?
- Which audience should the first version serve?
- What latency makes suggestions genuinely useful?
- Should it display suggestions in a private window, an overlay, a browser dock, or on a second device?
- Which transcription and language-model services should it use, and should local processing be an option?
- What should be recorded or stored, and how will participants be informed where consent is required?
- Which features must work on both Windows and macOS at launch?
- How will source citations and uncertainty be shown for factual claims?

## Development notes

- Keep experimental product work separate from upstream OBS changes where practical.
- Test audio capture and display behavior on Windows and macOS independently.
- Use **Rebuttalist** as a working name. Domain and trademark clearance remain open before a public release.

## Ideas to add next

- Specific examples of conversations and the responses you want the app to suggest.
- A sketch of the on-screen experience.
- The single most important workflow for a prototype.
