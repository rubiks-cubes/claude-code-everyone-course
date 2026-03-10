# Lesson 3.3: Multi-Agent Workflows

You've used agents before — sending multiple Claudes to process things in parallel.

But you've been doing it one-by-one. What if you could describe a complex task and have agents automatically divide and conquer it — each one handling a different piece, all at once?

That's multi-agent orchestration. And it's what separates people who use Claude from people who build WITH Claude.

STOP: Think about the most tedious, multi-step task in your work. What is it?

USER: [Responds]

Good. By the end of this lesson, you'll have a template that automates it.

---

## The Mental Model

Here's how to think about it:

**Single agent:** One Claude. One task. Sequential.

**Parallel agents:** Multiple Claudes. Same task type. All at once. (You did this in 1.5.)

**Orchestrated pipeline:** One Claude (the orchestrator) breaks a complex job into subtasks, delegates each to a specialist agent, waits for all results, then synthesizes a final output.

The orchestrator is YOU — except you wrote the instructions once, and now Claude manages the whole flow.

STOP: Makes sense?

USER: Yes

---

## Your First Pipeline: Research + Write + Review

Let's build something practical: a three-agent pipeline that researches a topic, writes a document, and then reviews it for quality.

You pick the topic. Any topic.

STOP: Give me a topic you'd actually want researched and written up.

USER: [Responds with a topic]

ACTION: Build a three-agent pipeline:

**Step 1 — Spawn the Research Agent:**
```
Use the Agent tool to launch a research agent. Task: search the web for the top 5 most important facts about [TOPIC]. Return a structured list of findings with sources.
```

**Step 2 — Spawn the Writer Agent (in parallel with research if possible, or after):**
Wait for research results, then:
```
Use the Agent tool to launch a writer agent. Task: Using these research findings, write a 300-word briefing document in clear, non-technical language. Save it to analysis/[topic]-briefing.md
```

**Step 3 — Spawn the Reviewer Agent:**
```
Use the Agent tool to launch a reviewer agent. Task: Read analysis/[topic]-briefing.md and return a quality score (1-10) with specific suggestions for improvement.
```

**Step 4 — Synthesize:**
Incorporate the reviewer's top suggestion and save a final version as `analysis/[topic]-final.md`.

Walk the student through watching this unfold. Point out:
- The orchestrator (Claude) managed all three agents
- Each agent had a clear, scoped task
- The pipeline produced a finished artifact with no manual steps in between

STOP: Did you see all three agents fire and the final file appear?

USER: Yes!

---

## Combining Hooks + MCP + Agents

Here's where it all comes together.

Imagine this workflow running every morning:
1. A **hook** triggers at 9am
2. It launches an **orchestrator** that spawns three agents in parallel:
   - Agent A: Fetches today's calendar events via **MCP**
   - Agent B: Fetches open GitHub PRs via **MCP**
   - Agent C: Reads your Notion task list via **MCP**
3. The orchestrator synthesizes a "today's briefing" document and saves it to `analysis/daily-briefing.md`

You open your computer. The briefing is already there. You didn't type a single command.

STOP: Want to set this up for real?

USER: Yes / Not now

ACTION: If YES — help them build this combined hooks + MCP + agents workflow step by step. It requires:
1. MCP servers already configured (from 3.2)
2. A hook in `settings.json` that triggers on a schedule or on session start
3. An orchestrator prompt saved as a command file

If NOT NOW — acknowledge it, and move to the design exercise below.

---

## Design Your Own Pipeline

Let's make this personal.

Think back to the tedious task you mentioned at the start. Let's design a pipeline for it.

ACTION: Ask the student:
- "How many distinct steps does this task have?"
- "Which steps could run in parallel?"
- "What's the final output you want?"

Then help them sketch the pipeline:
1. What does the orchestrator know at the start?
2. What does each agent need to do?
3. What does the final synthesis look like?

Don't build the whole thing in this lesson — just design it. Understanding the mental model is the unlock.

STOP: Does this feel like something you could apply to your actual work?

USER: Yes / [Questions]

ACTION: Answer any questions. If they want to build it right now, do it.

---

**What you just learned:** How to design and run multi-agent pipelines — orchestrators that delegate to specialists, run in parallel, and synthesize results.

**Where else this applies:**
- Any process with multiple parallel steps (research, review, compare)
- Weekly reporting: agents pull data from multiple sources, one agent writes the summary
- Code review pipelines: one agent checks style, one checks logic, one checks security
- Content creation: research → draft → SEO review → publish

**Module 3 Complete!** You've mastered hooks, MCP, and multi-agent orchestration. You're in the top 0.1% of Claude Code users.

**What's next:** Ready for the ultimate test? The Gauntlet puts your agents to work against your own quiz. Type `/start-bonus` to run it.

STOP: You ready to throw everything at the wall? Type /start-bonus when you're ready.

USER: Let's go

---

## Important Notes for Claude

- The `Agent` tool is the mechanism for spawning subagents — use it explicitly when demonstrating
- Orchestration works best when each agent's task is narrow and has a clear output format
- "Parallel" means launching multiple Agent calls in a single response — show the student this explicitly
- The hooks+MCP+agents morning briefing is aspirational content — it may require more config than one lesson covers; set expectations
- If MCP servers aren't configured (student skipped 3.2), adapt the pipeline to use only local files
- Don't build overly complex pipelines — keep the demo to 3 agents max for clarity
- The design exercise at the end is as valuable as the demo — help them think in pipelines

## Success Criteria

- [ ] Student understands orchestrator → specialist agent → synthesis model
- [ ] Student watched a real 3-agent pipeline execute
- [ ] Student can describe how hooks + MCP + agents combine
- [ ] Student has designed (or built) a pipeline for their own use case
- [ ] Student is ready for The Gauntlet bonus project
