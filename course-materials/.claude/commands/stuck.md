The student is stuck or lost. Run the following diagnostic flow:

1. **Check where they are.** Read `CLAUDE.md` at the project root. Look for the `## Progress` section. If it exists, note the last completed lesson.

2. **Check for artifacts.** Run these checks to infer progress:
   - Does `organized/` have files? → Completed at least 1.3
   - Does `reviews/` have files? → Completed at least 1.6
   - Does `CLAUDE.md` have content beyond the scaffold? → Completed 1.7
   - Does a `quiz-project/` folder exist? → Started Module 2
   - Does `quiz-project/package.json` exist? → Completed at least 2.3
   - Does `quiz-project/.git` exist? → Completed at least 2.4
   - Does `analysis/gauntlet-report.md` exist? → Ran The Gauntlet

3. **Ask what went wrong.** Say: "Based on what I can see, it looks like you last completed [LESSON]. What's going wrong — are you getting an error, or are you just not sure what to do next?"

4. **Route them.** Based on their answer:
   - Error message → Help diagnose it directly
   - Not sure what to do → Tell them: "Type `/start-[LESSON]` to restart that lesson from the beginning. Your work is safe."
   - Everything seems broken → Run `ls` to check folder structure and reassure them

5. **If truly lost** — offer to start fresh from the beginning: "If you want to start completely fresh, you can type `/start-1-1` at any time. Your files won't be deleted."

Always end with: "You're not as lost as you think. Tell me what you're seeing."
