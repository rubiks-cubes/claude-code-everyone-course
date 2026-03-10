# Claude Code for Everyone - Documentation Website

This is the Nextra-based documentation website for the **Claude Code for Everyone** (CC4E) course.

The actual course materials (lesson scripts, commands, scenario files) live in `course-materials/`.

## Development

```bash
# Install dependencies
npm install

# Run development server
npm run dev

# Open http://localhost:3000
```

## Building

```bash
# Build static site
npm run build

# The build output will be in the `out/` directory
# Pagefind will automatically index the content after build
```

## Deployment to Vercel

### Option 1: Connect via Vercel Dashboard

1. Go to [vercel.com](https://vercel.com) and sign in
2. Click "Add New Project"
3. Import this GitHub repository
4. Framework Preset: Next.js
5. Build Command: `npm run build`
6. Output Directory: `out`
7. Deploy!

### Option 2: Deploy via Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy from the root directory
vercel

# For production
vercel --prod
```

## Project Structure

```
course-materials/        # Course lesson scripts and scenario files
├── lesson-modules/      # CLAUDE.md lesson files (1.1–3.3 + bonus)
├── .claude/
│   ├── commands/        # Slash commands (/start-1-1, /help, /stuck, etc.)
│   └── EXTERNAL-LINKS.md
├── company-context/     # Basecamp Coffee scenario background
├── inherited-chaos/     # Messy files students analyze in Module 1
└── course-structure.json

pages/                   # Nextra documentation pages (MDX)
public/                  # Images and static assets
```

## Content Updates

Course content lives in `course-materials/lesson-modules/`. To update the website:

1. Edit the relevant `CLAUDE.md` files in `course-materials/lesson-modules/`
2. Run the conversion script: `./convert-content.sh`
3. Build and deploy

## Tech Stack

- **Next.js** - Static site generation
- **Nextra** - Documentation theme
- **Pagefind** - Client-side search
- **MDX** - Markdown with JSX components

## Course Overview

| Module | Title | Lessons |
|--------|-------|---------|
| 1 | Claude Code Fundamentals | 1.1 – 1.8 |
| 2 | Vibe Coding | 2.1 – 2.5 |
| 3 | Power User Track | 3.1 – 3.3 |
| Bonus | The Gauntlet | `/start-bonus` |

## Links

- **Original Course:** https://github.com/carlvellotti/claude-code-everyone-course
- **Course Site:** https://ccforeveryone.com
- **Nextra Docs:** https://nextra.site
- **Pagefind Docs:** https://pagefind.app
