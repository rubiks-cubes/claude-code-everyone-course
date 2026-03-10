# Bonus: The Gauntlet 🏆

You've built agents. You've built a quiz. You've shipped something real.

Now we put them together.

The Gauntlet is one lesson. One prompt. Three agents you created in Lesson 1.6 — unleashed simultaneously on your own work.

No setup required. No new tools. Just you, your agents, and the quiz you built.

Let me tell you what's about to happen.

---

## What's About to Happen

You're going to type a single prompt.

The moment you hit Enter, three agents launch in parallel:

🟤 **The Barista Lead** — street-level instincts. She's heard 10,000 customers order coffee. She knows what real people say, what they don't say, and what makes them come back. If something feels wrong, she'll tell you exactly why in plain English.

📊 **The Exec** — has one question: "What does this do for the business?" No hand-waving. Wants numbers, projections, and a hypothesis she can test.

🎨 **The Product Designer** — the soul police. She asks: does this feel like anything? Is there a moment of delight? Is there a reason to share it? If the quiz is hollow, she will say so out loud.

Each agent gives their honest, in-character assessment. Then Claude synthesizes all three into a Final Verdict — saved as a real file you can read, keep, and act on.

STOP: Ready to run it?

USER: Yes / Let's do it

---

## The Prompt

Copy this exactly. Every word matters.

STOP: Type the following prompt:

```
Use the Barista Lead, Exec, and Product Designer agents simultaneously to review
the Coffee Personality Quiz at @quiz-project. I want each agent to give their
honest assessment — what works, what doesn't, and one thing they'd change.
Then synthesize all three reviews into a final verdict and save it to
analysis/gauntlet-report.md
```

Press Enter and watch what happens.

---

ACTION: When the student sends the prompt, execute the following:

1. **Launch three agents in parallel** using the Agent tool:

   **Agent 1 — Barista Lead (`(•‿•)`):**
   Task: Read the Coffee Personality Quiz at quiz-project. As the Barista Lead — someone who hears customers talk about coffee every day — give your honest assessment. What works? What rings false? What would a real customer say when they get their result? What's one thing you'd change? Be direct. Be a little feisty if needed.

   **Agent 2 — Exec (`(ಠ_ಠ)`):**
   Task: Read the Coffee Personality Quiz at quiz-project. As the Exec — focused on business outcomes — assess the quiz. Does it have a clear call to action? What's the projected impact on loyalty sign-ups or repeat visits? Is there a metric you'd track? What's one thing you'd change to improve business performance? Give me numbers or at least hypotheses.

   **Agent 3 — Product Designer (`(◠‿◠)`):**
   Task: Read the Coffee Personality Quiz at quiz-project. As the Product Designer — focused on the emotional experience — assess the quiz. Is there a delight moment? Does it feel like a brand? Would someone want to share their result? What's missing emotionally? What's one thing you'd change to make it memorable?

2. **Wait for all three to return.**

3. **Synthesize** all three reviews into a Final Verdict with this structure:
   ```markdown
   # Gauntlet Report — Coffee Personality Quiz

   ## The Panel
   - Barista Lead (•‿•): [1-2 sentence summary of her take]
   - Exec (ಠ_ಠ): [1-2 sentence summary of his take]
   - Product Designer (◠‿◠): [1-2 sentence summary of her take]

   ## What's Working
   [Points all three agree on, or strong positives]

   ## What Needs Work
   [Points of concern, ranked by severity]

   ## The One Fix That Matters Most
   [The highest-impact change, agreed upon or argued for by 2+ agents]

   ## Final Verdict
   [2-3 sentences. Honest, direct, actionable.]
   ```

4. **Save** the report to `analysis/gauntlet-report.md`

5. **Tell the student:** "The Gauntlet is complete. Open `analysis/gauntlet-report.md` to see the verdict."

---

## Read the Verdict

ACTION: Open `analysis/gauntlet-report.md` in the editor.

STOP: Read it. All of it. Take your time.

USER: [Reads and reacts]

---

## Pick One Thing

Now here's the rule: you only have to fix ONE thing.

Not everything. Not the whole quiz. One thing.

STOP: What's the one change from the report that feels most important to you?

USER: [Picks something]

ACTION: Make that change. Don't ask for clarification on small details — just build it. Then push to GitHub.

Done! Your quiz is better than it was an hour ago.

That's the loop. That's what real product development looks like — get feedback, pick the most important thing, ship it.

---

## What Just Happened

You just ran a parallel multi-agent review process.

Three independent perspectives. One synthesized output. One concrete action.

No meeting. No email thread. No waiting for feedback. You did it alone, in minutes.

This scales. Imagine running The Gauntlet on:
- A landing page you're about to launch
- A business proposal you're about to send
- A job description you're about to post
- A process doc that nobody reads

Same pattern. Different agents. Different context.

STOP: How does it feel knowing you can do this on anything?

USER: [Response]

---

**Gauntlet Complete!** 🏆

You've finished Module 1, Module 2, and if you got here through Module 3, you're officially a Claude Code power user.

More modules, in-depth guides, and a community of people like you at **ccforeveryone.com**.

This course was created by Carl Vellotti. If you have feedback — and especially if The Gauntlet surprised you — he'd love to hear it: [X](https://x.com/carlvellotti) / [LinkedIn](https://www.linkedin.com/in/carlvellotti/)

Now go build something.

---

## Important Notes for Claude

- The Gauntlet works even if the student HASN'T done Module 3 — it only requires the agents from 1.6 and the quiz from 2.x
- All three agents must launch in the same response (parallel, not sequential) — this is the visual magic of the lesson
- Use the actual agent personas defined in lesson 1.6. If the student's custom agents have different names or personalities, adapt
- If `quiz-project` can't be found with `@quiz-project`, ask the student for the path and use it directly
- The `analysis/` folder should already exist from Module 1 — create it if not
- The "pick one thing" instruction is deliberate: overwhelm is the enemy of shipping. Keep it to one fix.
- After the fix is made, push to GitHub immediately — ending on a deployed change feels incredible
- The closing reflection should feel earned, not rushed

## Success Criteria

- [ ] All three agents fired in parallel from a single prompt
- [ ] `analysis/gauntlet-report.md` exists and contains a structured verdict
- [ ] Student read the full report
- [ ] Student picked and implemented one change
- [ ] Change was pushed to GitHub and is live on Vercel
- [ ] Student feels the power of what they just did
