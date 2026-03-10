# Lesson 3.1: Hooks & Automation

You've been doing everything manually — asking Claude to format, to check, to remind.

What if Claude just... did that automatically? Every time? Without you asking?

That's hooks.

STOP: Have you ever wished something would just happen automatically — without you having to remember to do it?

USER: Yes, definitely

---

## What Are Hooks?

Hooks are rules you set up once, and then Claude follows them silently on every action.

Think of them like standing orders. Instead of saying "please format this file" every time — you set a hook that says "after you edit any TypeScript file, always run the formatter." Done. Forever.

There are two main types:

- **Pre-tool hooks** — Run BEFORE Claude takes an action (great for checks and confirmations)
- **Post-tool hooks** — Run AFTER Claude takes an action (great for formatting, logging, notifications)

STOP: Makes sense?

USER: Yes

---

## Your First Hook: Auto-Format on Save

The most useful hook for vibecoding: auto-format every time Claude edits a file.

No more "oops, the formatting is a mess" — it just stays clean.

Let's set it up.

ACTION: Open (or create) `.claude/settings.json` in the current project folder. Add the following hooks configuration:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "npx prettier --write \"$CLAUDE_TOOL_RESULT_FILE_PATH\" 2>/dev/null || true"
          }
        ]
      }
    ]
  }
}
```

Walk the student through what each part means:
- `PostToolUse` = runs after a tool is used
- `matcher: "Write|Edit"` = triggers when Claude writes or edits a file
- The command runs Prettier (auto-formatter) on that file
- `|| true` means "don't crash if Prettier isn't installed"

STOP: Want to see it in action? Ask me to make a small edit to your quiz and watch what happens.

USER: Sure, make a small edit

ACTION: Make a trivial edit (like adding a comment) to one of the quiz files. The hook should trigger automatically and run Prettier.

See that? No input from you. The file just got formatted.

---

## Hook #2: Pre-Commit Check

Now let's add a safety net: before any git commit, Claude will run a quick build check to make sure nothing is broken.

ACTION: Add a second hook to `.claude/settings.json`:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "npx prettier --write \"$CLAUDE_TOOL_RESULT_FILE_PATH\" 2>/dev/null || true"
          }
        ]
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "echo '[Hook] About to run: $CLAUDE_TOOL_INPUT_COMMAND'"
          }
        ]
      }
    ]
  }
}
```

This pre-hook logs every bash command before it runs — giving you a visible audit trail.

STOP: Can you think of a hook that would be useful in YOUR workflow?

USER: [Responds with ideas]

ACTION: Help them think through their hook idea. If it's implementable with a simple shell command, walk them through adding it.

---

## Real-World Hook Ideas

Here are hooks that power users actually use:

- **Auto-backup** — After every file edit, copy the file to a `/.backups` folder
- **Screenshot on deploy** — After a deploy command, take a screenshot of the live URL
- **Notify on finish** — After a long task completes, send a desktop notification: `osascript -e 'display notification "Claude is done!" with title "Claude Code"'`
- **Lint before push** — Before any `git push`, run `npm run lint` and block if it fails
- **Log everything** — Append every tool use to a `claude-activity.log` for auditing

STOP: Which of these sounds most useful to you right now?

USER: [Responds]

ACTION: Help them set up whichever hook they're most excited about.

---

**What you just learned:** How to set up pre- and post-tool hooks that run automatically on Claude actions.

**Where else this applies:**
- Any repetitive "please also do X" instruction can become a hook
- Teams can share a `settings.json` so everyone has the same automations
- Hooks + agents = incredibly powerful automation pipelines (we'll use this in 3.3)

**Next up:** In 3.2, we connect Claude to external services — GitHub, Notion, Google Calendar, and more. Your Claude Code is about to have superpowers.

STOP: Ready to connect Claude to the world? Say "let's connect" or type /start-3-2

USER: Let's connect

---

## Important Notes for Claude

- `settings.json` lives at `.claude/settings.json` relative to the project root
- The `$CLAUDE_TOOL_RESULT_FILE_PATH` variable is injected by Claude Code for file-related tools
- The `$CLAUDE_TOOL_INPUT_COMMAND` variable contains the bash command text for PreToolUse on Bash
- `|| true` at the end of hook commands prevents the hook from blocking Claude if the command fails
- If the student's project doesn't have Prettier installed, the first hook will silently no-op (that's fine)
- Don't overwhelm with hooks — 1-2 practical ones is better than a complex configuration
- If hooks aren't triggering, check that `settings.json` is valid JSON (no trailing commas)

## Success Criteria

- [ ] Student understands what pre- and post-tool hooks are
- [ ] `.claude/settings.json` exists with at least one working hook
- [ ] Student saw the auto-format hook trigger in real time
- [ ] Student can articulate a hook they'd use in their own workflow
- [ ] Student is ready for MCP (3.2)
