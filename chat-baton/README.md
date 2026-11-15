# Chat Baton

Long chats get slow, and the early parts get summarized or forgotten. Chat Baton passes the baton to a fresh chat: it writes (or updates) a structured handoff Markdown file with everything that matters, so you can continue in a new conversation without explaining it all again.

## What it does
- Suggests switching chats when a conversation is very long, holds many large files, or a topic has closed.
- Writes or updates `handoff-[topic].md` with: context, current status, decisions, to-do list with deadlines, open questions, methods that work, and a line to restart.
- Never invents decisions or deadlines, and never drops information from a previous handoff.
- Asks before including sensitive data such as passwords or keys.
- Ends with simple steps to continue in a new chat or Project.

## Tip
Add one line to your account instructions, for example "When a chat gets too long, tell me and use the chat-handoff skill", so the reminder is always active. You can also just type "handoff".

## Privacy
This plugin contains one skill (plain instructions). It runs no code and sends no data anywhere. The handoff file is created in your chat and stays with you.

## License
MIT
