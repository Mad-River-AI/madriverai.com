# Mad River AI — madriverai.com

## 📖 Read the roadmap
The full strategic roadmap lives in the private repo `Mad-River-AI/down-stream` at `CLAUDE.md`.
Current phase and next task are in the **AGENT CONTINUATION PROTOCOL** block at the top of that file.

When starting a session here, check `Mad-River-AI/down-stream` `CLAUDE.md` for `CURRENT_TASK` before doing anything else.

## 🎯 This repo's role
Public website for Mad River AI. Stack: Astro 6 + Tailwind CSS v4 + Three.js.
Deployed to GitHub Pages via `.github/workflows/deploy.yml` on push to `main`.

### Dev commands
```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # production build to ./dist
npm run preview  # preview the build
```

## 🎨 Design language
- Dark theme: deep navy base, cyan (`#00e5ff`) + amber (`#ffab00`) accents
- Glassmorphism cards with glow effects
- Three.js knowledge graph background (non-blocking)
- Reduced motion respected — all animations collapse on `prefers-reduced-motion`
- Mobile-first: 16px side gutter, no horizontal scroll

## ✅ Content standards
- No launch dates that aren't confirmed
- No feature claims that don't exist in the framework yet
- Prediction pages must have real dates and real predictions only
- Blog posts must be accurate — no hype without substance

## 🛑 Hard stops — never do these
- Never commit real API keys or tokens
- Never publish predictions without human review and cryptographic timestamp
- Never claim capabilities that don't exist in the framework
- Never push directly to main

## 🔄 After completing a task
Update `CURRENT_TASK` and the `PROGRESS LOG` in `Mad-River-AI/down-stream` `CLAUDE.md`.
