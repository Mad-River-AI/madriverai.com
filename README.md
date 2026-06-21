# madriverai.com

Source for the Mad River AI website.

## Stack

- [Astro 6](https://astro.build) — static site generator
- [Tailwind CSS v4](https://tailwindcss.com) — via `@tailwindcss/vite`
- [Three.js](https://threejs.org) — knowledge graph background, 3D effects

## Develop

```bash
npm install
npm run dev          # http://localhost:4321
```

## Build

```bash
npm run build
npm run preview
```

## Deploy

GitHub Pages. Pushes to `main` trigger `.github/workflows/deploy.yml`,
which builds to `./dist` and deploys to Pages.

The custom domain `madriverai.com` is configured via `public/CNAME` —
point the DNS at GitHub's Pages servers (see repo Settings → Pages for
the current IPs and the ALIAS/ANAME setup).

## Structure

```
src/
  layouts/Base.astro          # shell, fonts, knowledge graph + orbital nav
  components/
    KnowledgeGraph.astro      # Three.js force-directed background
    OrbitalNav.astro          # 3D revolving section directory
  pages/
    index.astro               # home
    mission.astro             # mission & goals
    projects.astro            # public projects
    links.astro               # contact + handles
    blog/
      index.astro             # blog index
      2026-06-21-v0-1-release.astro   # first post
  styles/global.css           # design tokens, glassmorphism, glow
public/
  favicon.svg
  CNAME                        # madriverai.com
.github/workflows/deploy.yml
```

## Design notes

- **Dark theme**, deep navy + cyan/amber accents.
- **Knowledge graph** is a Three.js force-directed graph with 80 nodes
  (40 on mobile), drifting slowly, never blocking pointer events.
- **Orbital nav** is six glassmorphic "planets" orbiting a central hub.
  Auto-rotates by default; drag to override.
- **Reduced motion** is respected — animations collapse to instant.

## License

MIT. See [LICENSE](LICENSE).
