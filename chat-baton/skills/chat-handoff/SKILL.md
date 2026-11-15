---
name: chat-handoff
description: Use when a chat is very long or slow, a topic is done, or the user says 'handoff', 'new chat', 'let's wrap up here': write or update a structured handoff .md file and guide the user to continue in a fresh chat without losing context.
---

# Chat handoff

Long chats get slow, and the early parts get summarized or forgotten. A handoff file carries everything that matters into a fresh chat.

Reply in the user's language.

## When to suggest it (even unasked)
Suggest switching chats, in one line at the end of your reply, when at least one of these is true:
- the conversation is past roughly **60 exchanges**, or holds many long tool results or large files;
- you can no longer see the start of the conversation, or you need to re-read things said much earlier;
- a topic has closed and a different one is starting.

Don't interrupt work halfway: suggest it at the end of the current step. If the user says no, don't suggest it again for about 20 exchanges.

Tip for the user: since skills are only read when they are loaded, add one line to your account-level instructions (e.g. "When a chat gets too long, tell me and use the chat-handoff skill") so the reminder is always active. You can also just type "handoff" at any time.

## What to do when the user accepts (or asks)
1. **If a handoff for this topic already exists** (attached, in the Project, or sent earlier in this chat): start from it and **update it**, keeping the file name and every part that is still valid. Don't rewrite it from scratch.
2. **If none exists**, create it as `handoff-[topic].md` (e.g. `handoff-thesis.md`).
3. File structure:
   - **Title and date** of the update (user's time zone).
   - **Context**: what this topic is for, in 2-3 lines.
   - **Current status**: where things stand.
   - **Rules and decisions**: everything the user decided, with the date when useful. Only the user's decisions, not suggestions they didn't accept.
   - **To do**: list with deadlines, most urgent first.
   - **Open / to check**.
   - **Methods that work**: commands, paths, steps already tested.
   - **Sensitive data**: if the chat contains passwords, keys, codes or personal data, don't copy them by default. Ask the user once whether to include them; if yes, put them together in this section at the end of the file so they are easy to remove before sharing.
   - **How to restart**: one line to paste into the new chat.
4. Write the file and send it as an attachment.
5. Close with these steps, and nothing else:
   1. Download the file from the card above.
   2. If this topic has a Project: open it, remove the old handoff from the project files and upload the new one.
   3. Open a new chat (inside the Project, if there is one).
   4. Attach the file (if it isn't already in the Project) and paste the "How to restart" line.
   5. Give the new chat a clear name.

## Don't
- Don't summarize the file in the chat: it's in the attachment.
- Don't invent decisions or deadlines: if something is unclear, put it under "Open / to check".
- Don't drop anything from the previous handoff unless the user asks to remove it.
