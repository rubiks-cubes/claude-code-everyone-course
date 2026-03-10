# Lesson 3.2: MCP Deep Dive

You've been working in isolation — Claude Code talking to your local files.

MCP changes that. MCP stands for Model Context Protocol — it's how Claude connects to the outside world.

Instead of copy-pasting a GitHub issue into the terminal, Claude just... reads it. Instead of switching to Notion to find a doc, Claude just fetches it. Instead of manually checking your calendar, Claude knows your schedule.

STOP: What's one external tool you use every single day?

USER: [Responds — could be Notion, Slack, Gmail, GitHub, Calendar, etc.]

Great. By the end of this lesson, Claude will be connected to it.

---

## How MCP Works

MCP servers are small adapters that translate between Claude and an external service.

You set them up once. After that, Claude can use them silently — no copy-pasting, no switching tabs, no context switching.

The setup lives in your Claude Code config file.

Let's do three setups:
1. **GitHub MCP** — Claude reads issues, PRs, and repos
2. **Filesystem MCP** — Enhanced file access (already kind of built in, but MCP gives more control)
3. **Your chosen tool** (from your answer above)

STOP: Ready to start?

USER: Yes

---

## Setup 1: GitHub MCP

This lets Claude read and interact with your GitHub repos directly.

ACTION: Check if the GitHub MCP server is already configured:
```bash
claude mcp list
```

If not listed, add it:
```bash
claude mcp add github-official -- npx -y @modelcontextprotocol/server-github
```

Then verify it was added:
```bash
claude mcp list
```

Now test it. Ask Claude to fetch the latest open issue from a GitHub repo you own.

STOP: Ask me: "What are the open issues on [your-github-username]/quiz-project?"

USER: [Asks the question]

ACTION: Use the GitHub MCP tool to fetch issues from the student's quiz-project repo. Show the result.

See that? No browser, no copy-pasting. Claude fetched it live.

---

## Setup 2: Notion MCP (Optional — skip if you don't use Notion)

STOP: Do you use Notion?

USER: Yes / No / Skip

[If YES:]

ACTION: Add the Notion MCP server:
```bash
claude mcp add notion-official -- npx -y @modelcontextprotocol/server-notion
```

You'll need a Notion API key. Let me open the setup page for you:
```bash
open https://www.notion.so/profile/integrations
```

Create a new integration, copy the API key, and run:
```bash
export NOTION_API_KEY="your-key-here"
```

Now test: ask Claude to find a page or database in your Notion workspace.

---

## Setup 3: Your Tool

Remember what you said you use every day? Let's connect that.

Here are the most popular MCP servers available right now:

| Tool | MCP Server Command |
|------|--------------------|
| Google Calendar | `claude mcp add google-calendar -- npx -y @modelcontextprotocol/server-google-calendar` |
| Slack | `claude mcp add slack -- npx -y @modelcontextprotocol/server-slack` |
| Linear | `claude mcp add linear -- npx -y @modelcontextprotocol/server-linear` |
| Jira | `claude mcp add jira -- npx -y @modelcontextprotocol/server-jira` |
| Postgres | `claude mcp add postgres -- npx -y @modelcontextprotocol/server-postgres` |
| Filesystem (enhanced) | `claude mcp add filesystem -- npx -y @modelcontextprotocol/server-filesystem /path/to/folder` |

ACTION: Based on what the student said they use every day, suggest the matching server. Walk them through setting it up and testing it with a real query against their actual data.

If their tool isn't on the list, help them search for it:
```bash
# Search npm for MCP servers
open https://www.npmjs.com/search?q=%40modelcontextprotocol
```

---

## Seeing All Your Servers

ACTION: Show a summary of all connected MCP servers:
```bash
claude mcp list
```

These are now permanent — they'll be available in every Claude Code session in this project.

STOP: How does it feel knowing Claude can reach into all these tools?

USER: [Response]

---

## A Real Use Case: Morning Briefing

Here's something powerful to try. With GitHub + Calendar + Notion all connected:

STOP: Ask me: "What's on my plate today? Check my calendar, any open GitHub PRs, and my Notion task list."

USER: [Asks]

ACTION: Use all available MCP servers to pull the relevant data and compose a natural-language morning briefing.

This is the future. One question. All your tools. No switching.

---

**What you just learned:** How to connect Claude Code to external services using MCP, and how to use those connections to pull live data without leaving the terminal.

**Where else this applies:**
- Any API or service that has an MCP server can connect to Claude
- Teams can share an MCP config so everyone's Claude has the same connections
- MCP + agents = Claude can act on external services in parallel (coming in 3.3)

**Next up:** In 3.3, we combine everything — hooks + MCP + agents — into multi-agent workflows that tackle complex multi-step tasks.

STOP: Ready to orchestrate? Say "let's orchestrate" or type /start-3-3

USER: Let's orchestrate

---

## Important Notes for Claude

- MCP servers require an internet connection and the npm packages are fetched on first run
- `claude mcp add [name] -- [command]` is the standard setup pattern
- Some MCP servers need API keys — help students find and configure these but NEVER log or store the key values
- If `claude mcp list` returns nothing, the config may not have been saved — check `~/.claude.json` or the project `.claude/` config
- Google Calendar MCP requires OAuth — it's more involved; if the student chose this, walk through the OAuth flow carefully
- The "morning briefing" demo is the showstopper — make it feel natural and powerful
- If a server fails to connect, the most common fix is: check the API key, then check network permissions

## Success Criteria

- [ ] Student has at least one MCP server configured (GitHub is recommended minimum)
- [ ] Student successfully queried live data from at least one connected service
- [ ] Student has their own most-used tool connected
- [ ] Student understands the pattern: `claude mcp add [name] -- [command]`
- [ ] Student is excited about the morning briefing / multi-tool query concept
- [ ] Student is ready for multi-agent workflows (3.3)
