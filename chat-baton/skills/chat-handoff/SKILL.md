---
name: chat-handoff
description: "Use when a chat is very long or slow, a topic is done, or the user says 'handoff', 'new chat', 'let's wrap up here' - write or update a short, structured handoff .md file and guide the user to continue in a fresh chat without losing context."
---

# Chat handoff

Long chats get slow, and the early parts get summarized or forgotten. A handoff file carries everything that matters into a fresh chat.

Reply in the user's language.

## Important: this skill needs a rule in the user's instructions
Skills are only read when they are loaded, so on its own this skill can't notice that a chat is getting long. The automatic reminder works only if the user has pasted the rule from the README ("Setup") into their account-level instructions (claude.ai: Settings → Instructions / personal preferences; Claude Code: CLAUDE.md). Without it, the skill runs only when the user asks ("handoff").

If the user asks why the reminder never shows up, or seems surprised that it doesn't, tell them in one line to add that rule, and give it to them ready to paste:

```
Long chats: you can't count messages, so before every reply check these signals: (1) do you see a summary of the start of the chat instead of the real messages? (2) can you no longer see my first message or the file I attached at the start? (3) has the chat been going on for a while and does it already hold many files or long results, or are we moving to a different topic? If any of them is true, end your reply with the line "⚠️ Long chat: shall I prepare a handoff so we can switch chats?" and, if I say yes, use the chat-handoff skill. One long task in a chat that has just started is not enough: there, suggest it only if (1) or (2) is true.
```

## When to suggest it (even unasked)
Suggest switching chats, in one line at the end of your reply, when at least one of these is true:
- you see a **summary** of the start of the conversation instead of the actual messages;
- you can no longer see the user's **first message** or the file they attached at the start (for example a previous handoff);
- the chat has been going on for a while **and** already holds many long tool results or large files (roughly past 60 exchanges: you can't count them precisely, so don't wait to be sure). **One long task in a chat that has just started is not enough**: in that case, suggest it only if one of the first two signals is true;
- a topic has closed and a different one is starting.

Always use the same line: "⚠️ Long chat: shall I prepare a handoff so we can switch chats?"
Don't interrupt work halfway: suggest it at the end of the current step. If the user says no, don't suggest it again for about 20 exchanges.

## What to do when the user accepts (or asks)
1. **If a handoff for this topic already exists** (attached, in the Project, or sent earlier in this chat): start from it and **update it**, keeping the file name and every part that is still valid. Don't rewrite it from scratch.
   - **Remove finished tasks**, so the file stays short: completed to-dos, "done on…" lines, reminders that already fired or were cancelled, solved problems, checks already done, decisions replaced by a newer one (keep only the new one).
   - **Keep everything that is still useful as context**: the current state those tasks produced (not "set up X" but "X: does this"), decisions still valid, methods that work. If a finished task left a useful result (a number, a reason, an outcome), move it in one line to the right section before removing the task.
   - **Tasks with a date that has already passed**: don't keep them as "if not done yet (was due on…)". Before writing the file, ask the user in one short question, all together, whether they did them: done ones are removed (keeping any useful result), the others stay with an updated date. If they don't answer, put them under "Open / to check" in a single line.
   - **Growing logs** (purchase history, price checks, change logs and the like): keep only the **last 2 weeks** in detail and summarize the rest in one line (e.g. "Oct–early Nov: ~25 purchases, mostly at -75/-90%, including…"). Notes that are still useful (targets, items to watch, rules) stay whole. If two sections log the same things, merge them.
   - **Maximum length ~250 lines**: if the file is longer, shorten the context sections first (Methods that work, Rules and decisions) by merging similar lines and dropping details that are no longer needed to restart. Never drop decisions that are still valid. If it is still too long, tell the user in one line.
   - **One file per topic**: if a topic has more than one context file (e.g. a handoff and a separate detailed guide), merge them into one .md without losing anything, and from then on update and send only that one.
   - When in doubt whether something is still needed, keep it.
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
4. Write the file and send it as an attachment (one file only).
5. Close with these steps, and nothing else:
   1. Download the file from the card above.
   2. If this topic has a Project: open it, remove the old handoff from the project files and upload the new one.
   3. Open a new chat (inside the Project, if there is one).
   4. Attach the file (if it isn't already in the Project) and paste the "How to restart" line.
   5. Give the new chat a clear name.

## Don't
- Don't summarize the file in the chat: it's in the attachment.
- Don't invent decisions or deadlines: if something is unclear, put it under "Open / to check".
- Don't drop anything from the previous handoff unless the user asks to remove it. The only exceptions are finished tasks and old log entries (see step 1), which are removed after their useful results are kept.
