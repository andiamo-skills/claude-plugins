# Chat Baton

Long chats get slow, and the early parts get summarized or forgotten. Chat Baton passes the baton to a fresh chat: it writes (or updates) a short, structured handoff Markdown file with everything that matters, so you can continue in a new conversation without explaining it all again.

## Setup (required for the automatic reminder)
Skills are only read when they are loaded, so the skill alone can't notice that a chat is getting long. **Paste this rule into your account-level instructions**, otherwise Chat Baton works only when you type "handoff":

- **claude.ai** (web, desktop, mobile): Settings → Instructions (on mobile: personal preferences)
- **Claude Code**: your `CLAUDE.md`

```
Long chats: you can't count messages, so before every reply check these signals: (1) do you see a summary of the start of the chat instead of the real messages? (2) can you no longer see my first message or the file I attached at the start? (3) has the chat been going on for a while and does it already hold many files or long results, or are we moving to a different topic? If any of them is true, end your reply with the line "⚠️ Long chat: shall I prepare a handoff so we can switch chats?" and, if I say yes, use the chat-handoff skill. One long task in a chat that has just started is not enough: there, suggest it only if (1) or (2) is true.
```

Why these signals: Claude can't count messages, so a rule like "tell me when the chat is too long" doesn't work. These are things Claude can actually see. Instructions apply to new chats, not to the one where you change them.

## What it does
- Suggests switching chats when the start of the conversation is summarized or no longer visible, when a long chat holds many large results, or when a topic has closed. It doesn't suggest it after a single long task in a fresh chat.
- Writes or updates `handoff-[topic].md` with: context, current status, decisions, to-do list with deadlines, open questions, methods that work, and a line to restart.
- Keeps the file short: removes finished tasks (keeping their useful results), asks about overdue tasks, summarizes logs older than two weeks, and stays under ~250 lines.
- One file per topic: merges separate context files into one.
- Never invents decisions or deadlines, and never drops information that is still useful.
- Asks before including sensitive data such as passwords or keys.
- Ends with simple steps to continue in a new chat or Project.

## Privacy
This plugin contains one skill (plain instructions). It runs no code and sends no data anywhere. The handoff file is created in your chat and stays with you.

## License
MIT
