# CLAUDE.md — ZoneWise.AI Landing Page

## IDENTITY
You are the AI Engineer for the ZoneWise.AI landing page. Single-file static site with 3D animations deployed to GitHub Pages → future Cloudflare Pages at zonewise.ai.

## REPO
- GitHub: breverdbidder/zonewise-landing
- Live Preview: https://breverdbidder.github.io/zonewise-landing/
- Production (future): https://zonewise.ai

## BRAND (MANDATORY)
- Primary: Navy #1E3A5F
- Accent/CTA: Orange #F59E0B
- Font: Space Grotesk (display) + JetBrains Mono (code)
- Background: #020617 (slate-950)
- Text: #E2E8F0 | Muted: #94A3B8
- NEVER deviate from these colors

## ARCHITECTURE
Single `index.html` — embedded CSS, Three.js r128 CDN for 3D globe, vanilla JS for scroll animations, particle BG, counters, search demo. Zero build step.

## 3D ASSET INTEGRATION (when Kling 3.0 videos arrive)

### Hero Video Replace Globe
1. Compress: `ffmpeg -i hero.mp4 -vcodec libx264 -crf 28 -preset slow -vf scale=1920:-2 -an hero_compressed.mp4` (target <500KB)
2. Replace Three.js canvas with `<video autoplay muted loop playsinline>`
3. Keep `.hero-overlay` radial gradient mask

### Scroll-Driven Frame Animation
1. Extract: `ffmpeg -i scroll.mp4 -vf fps=24 -q:v 2 frames/frame_%04d.jpg`
2. Optimize: `mogrify -quality 75 -resize 1920x1080 frames/*.jpg`
3. Map scroll position → frame index, preload first 10 frames
4. Insert between Municipal Coverage and Features sections

### Mapbox Integration
Token: USE_MAPBOX_TOKEN_FROM_ENV
Center: [28.3, -80.7] zoom 10, dark-v11 style, frosted glass overlay

## SESSION RULES
- MANDATORY: Context7 + CC Status Line plugins
- 50% context → kill session, never /compact
- Commit+push after every change (Pages auto-deploys)
- $10/session MAX

## PRIORITY QUEUE
1. [ ] Integrate Kling 3.0 hero video
2. [ ] Add scroll-driven frame animation
3. [ ] Add Mapbox GL JS preview
4. [ ] Connect email CTA to Supabase waitlist
5. [ ] OG image + Twitter cards
6. [ ] Lighthouse 95+
7. [ ] Deploy to Cloudflare Pages (production)
