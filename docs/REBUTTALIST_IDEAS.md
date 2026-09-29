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

## Response display settings

Let users configure how live suggestions appear, with settings saved per mode or knowledge base:

- Choose a format such as a fixed number of concise bullets, a short paragraph, a fuller explanation, or questions to ask.
- Set the number of bullets (for example, exactly five), maximum length per bullet or response, and preferred level of detail.
- Provide an **Answer** button and a keyboard shortcut. When pressed during a debate, use the latest relevant conversation context and the selected knowledge base to generate a fresh response in the saved format. For example, a five-bullet preset should display five quick bullets every time.
- Keep the first result fast and readable at a glance. Offer a way to expand it for evidence, citations, and detail without changing the configured short view.
- Make the current format and knowledge base visible so the user knows what the Answer button will produce.

## Steelman and question mode

Add a **Steelman** option that briefly presents the strongest fair version of the other person's position. From that understanding, suggest useful clarifying or probing questions the user can ask when they need a moment to think or want to test the argument. Let the user request questions directly with a button or shortcut, with the same format and maximum-length controls. Distinguish questions from factual rebuttals, and avoid inventing what the other person believes.

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

## Literature and knowledge bases

Let users build multiple named knowledge bases for separate debates, projects, clients, or topics. Users can add literature and other source material to each base, such as papers, books or excerpts they have rights to use, documents, links, notes, and prior arguments. Show what was imported, its processing status, and the source behind each suggested response.

- Allow a user to choose the active knowledge base before a debate and switch bases during a session. Suggestions should draw from the selected base, with an option to combine explicitly selected bases.
- Let users assign a priority or weight to each source, and optionally mark a source as authoritative, background, or disputed. Ranking should influence retrieval and presentation without treating a highly weighted source as automatically true.
- Organize sources within each base by topic, stance, tags, and project. Let users edit, replace, remove, and reprocess individual items.
- When supported by the chosen AI provider, upload or index items in that provider's API storage and associate them with the corresponding Rebuttalist knowledge base. Keep a mapping of local items to remote file or index IDs so the app can avoid duplicate uploads and delete or update the right remote items.
- Explain where source content is stored, which provider can access it, any provider storage or retrieval charges, and how deletion works. Keep bases separate to avoid accidentally pulling material from another debate or client.
- Show citations to the specific source and passage used in a rebuttal when the provider supports it. Make it clear when a suggestion is general model output rather than grounded in the selected base.

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
- Which provider APIs support persistent file storage and retrieval, and should knowledge bases also work with local indexing?
- What costs would Rebuttalist itself incur under a bring-your-own-key subscription?

## Development notes

- Keep experimental product work separate from upstream OBS changes where practical.
- Test audio capture and display behavior on Windows and macOS independently.
- Use **Rebuttalist** as a working name. Domain and trademark clearance remain open before a public release.

## Ideas to add next

- Specific examples of conversations and the responses you want the app to suggest.
- A sketch of the on-screen experience.
- The single most important workflow for a prototype.
