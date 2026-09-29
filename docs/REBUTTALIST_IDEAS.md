# Rebuttalist ideas

Working notes for a real-time response assistant built from the OBS Studio fork. This document records product ideas, not settled requirements.

## Core idea

Help someone respond during a live conversation. The app listens to an exchange, recognizes the question, objection, or argument, and suggests a useful next response quickly enough to use in the moment.

**Working tagline:** Your next response, right on time.

## Audiences and possible modes

- **Debate:** Identify a claim, surface a concise counterargument, and show supporting sources when available.
- **Sales:** Recognize objections, suggest a response and a follow-up question, and avoid unsupported claims.
- **Job interviews:** Help applicants answer questions using their own experience and the job description.

## Multi-window workspace

Support separate, independently movable and resizable windows that users can place on different monitors. For example:

- **Transcript window:** Live speech-to-text with speaker labels.
- **Summary window:** A continuously updated summary of the conversation and key points.
- **Rebuttals window:** Suggested responses to the latest argument, objection, or question.

Allow users to show or hide each window and choose its screen. Keep the transcript, summary, and suggestions synchronized to the same conversation.

## Possible first version

1. Capture microphone and, where permitted, the other participant's audio.
2. Transcribe speech live and distinguish the user's speech from the other participant's.
3. Detect when a response is needed.
4. Show one short suggested reply, with optional alternatives or supporting detail.
5. Let the user pause listening, hide suggestions, and review or delete session data.

## Bring-your-own API keys

Let users connect their own accounts for services Rebuttalist uses. Examples include Amazon Web Services for transcription and OpenAI or Anthropic for response generation. Let users choose supported providers and enter the credentials required by each provider. Usage charges from those services would be separate from the Rebuttalist subscription.

Key handling requirements to design and test:

- Store credentials in the operating system's secure credential store where available, never in the repository, plaintext configuration files, logs, transcripts, or analytics.
- Mask credentials in the interface, avoid exposing them to windows or processes that do not need them, and provide a way to replace or remove them.
- Send each credential only to its intended provider over encrypted connections. Do not route user keys through a Rebuttalist server unless the architecture explicitly requires it and the user is informed.
- Support least-privilege credentials and provider-side spending limits where the provider permits them.
- Explain which provider receives audio, transcripts, and prompts before enabling a connection.

## Subscription idea

Charge **$5 per month** for Rebuttalist. This is an initial pricing idea to validate, not a finalized plan. Define what the subscription includes, how billing and cancellation work, and how to handle the separate charges on users' own API accounts.

## Design questions to resolve

- Should Rebuttalist be an OBS plugin, a separate desktop app using OBS components, or a full OBS fork?
- Which audience should the first version serve?
- What latency makes suggestions genuinely useful?
- How should the three windows behave when a user has only one screen?
- Which transcription and language-model services should it use, and should local processing be an option?
- What should be recorded or stored, and how will participants be informed where consent is required?
- Which features must work on both Windows and macOS at launch?
- How will source citations and uncertainty be shown for factual claims?
- What costs would Rebuttalist itself incur under a bring-your-own-key subscription?

## Development notes

- Keep experimental product work separate from upstream OBS changes where practical.
- Test audio capture and display behavior on Windows and macOS independently.
- Use **Rebuttalist** as a working name. Domain and trademark clearance remain open before a public release.

## Ideas to add next

- Specific examples of conversations and the responses you want the app to suggest.
- A sketch of the on-screen experience.
- The single most important workflow for a prototype.
