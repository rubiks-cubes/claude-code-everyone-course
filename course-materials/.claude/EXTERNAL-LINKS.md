# External Links Registry

All external URLs used across the CC4E course. Update this file when a link changes or when verifying links.

**Format:** `URL | Purpose | Last Verified`

---

## Course & Community

| URL | Purpose | Last Verified |
|-----|---------|---------------|
| https://ccforeveryone.com | Main course site, newsletter, community | 2026-03-10 |
| https://ccforeveryone.com/fundamentals/course-intro | Lesson 1.1 reference page | 2026-03-10 |
| https://fullstackpm.com | Carl Vellotti's main site | 2026-03-10 |
| https://x.com/carlvellotti | Carl on X/Twitter | 2026-03-10 |
| https://www.linkedin.com/in/carlvellotti/ | Carl on LinkedIn | 2026-03-10 |

---

## Tools & Downloads

| URL | Purpose | Last Verified | Lesson |
|-----|---------|---------------|--------|
| https://nimbalyst.com/ | Nimbalyst download | 2026-03-10 | 1.2 |
| https://cursor.com | Cursor download | 2026-03-10 | 1.2 |
| https://cli.github.com | GitHub CLI download (manual) | 2026-03-10 | 2.4 |
| https://github.com | GitHub signup | 2026-03-10 | 2.4 |
| https://github.com/login/device | GitHub device auth page | 2026-03-10 | 2.4 |
| https://vercel.com | Vercel signup and dashboard | 2026-03-10 | 2.5 |
| https://nodejs.org | Node.js LTS download | 2026-03-10 | 2.3 |

---

## References & Demos

| URL | Purpose | Last Verified | Lesson |
|-----|---------|---------------|--------|
| https://x.com/bcherny/status/2007566454447906842 | Creator of Claude Code quote-tweet (browser use demo) | 2026-03-10 | 1.8 |

---

## MCP Server Packages (npm)

| Package | Purpose | Last Verified | Lesson |
|---------|---------|---------------|--------|
| @modelcontextprotocol/server-github | GitHub MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-notion | Notion MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-google-calendar | Google Calendar MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-slack | Slack MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-linear | Linear MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-jira | Jira MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-postgres | Postgres MCP server | 2026-03-10 | 3.2 |
| @modelcontextprotocol/server-filesystem | Filesystem MCP server | 2026-03-10 | 3.2 |

---

## How to Verify Links

```bash
# Quick check - returns HTTP status code
curl -o /dev/null -s -w "%{http_code}" [URL]
# 200 = ok, 301/302 = redirect (usually fine), 404 = broken
```

When a link breaks: fix it in the relevant lesson CLAUDE.md AND update the "Last Verified" date here.
