# CLAUDE.md — ZoneWise.AI Landing Page

## Project
ZoneWise.AI marketing landing page with 3D scroll animations, Three.js globe, and zoning map visualizations.

## Brand (MANDATORY)
- Primary: Navy `#1E3A5F`
- Accent/CTA: Orange `#F59E0B`
- Font: Space Grotesk (display) + JetBrains Mono (code/data)
- Background: `#020617` (slate-950)
- Text: `#E2E8F0` (slate-200)
- Muted: `#94A3B8`
- Reference: BRAND_COLORS.md in zonewise-web repo

## Architecture
- Single `index.html` file (self-contained HTML/CSS/JS)
- Three.js r128 for 3D globe (CDN loaded)
- Canvas-based zoning map animation (no external deps)
- CSS scroll-driven reveals + IntersectionObserver
- Zero build step — static file deployment

## Key Sections
1. **Hero**: Three.js rotating wireframe globe with orange/blue particles, radial gradient overlay
2. **Stats Bar**: Animated counters (78K+ parcels, 8 municipalities, 100% match, 250K+ zones)
3. **Zoning Map Canvas**: Grid-based parcel fill animation triggered on scroll intersection
4. **Municipal Coverage**: 8 municipality cards with progress bars (Palm Bay, Melbourne, etc.)
5. **Features**: 3-column grid (Spatial Join, GIS Integration, AI Classification)
6. **Search Demo**: Animated typewriter search bar with fake autocomplete dropdown
7. **How It Works**: 3-step flow (Enter Address → AI Classifies → Get Zoning)
8. **CTA**: Email capture with frosted glass card
9. **Footer**: ZoneWise.AI branding + Everest Capital USA

## Enhancement Priorities (for Claude Code sessions)
1. **Kling 3.0 Video Integration**: When MP4 assets arrive, replace Three.js globe with hero video background + gradient mask. Extract scroll animation video to JPEG frames.
2. **Mapbox Preview**: Add live Mapbox GL JS embed (token: `pk.eyJ1IjoiZXZlcmVzdDE4...`) centered on Brevard County (28.3, -80.7, zoom 10) with dark style + frosted overlay.
3. **Performance**: Compress all assets, lazy-load below-fold, target Lighthouse 90+.
4. **Mobile**: Full responsive optimization — stack grids, resize globe canvas, touch-friendly CTA.
5. **Scroll Animations**: Add GSAP or Locomotive Scroll for smoother frame-by-frame video scrubbing if Kling assets are integrated.

## Deployment
- **Preview**: GitHub Pages — `breverdbidder.github.io/zonewise-landing/`
- **Production**: Cloudflare Pages — `zonewise.ai` (DNS already on Cloudflare)
- **CI**: Push to `main` auto-deploys to GitHub Pages. CF Pages connects to same repo.

## Session Hygiene
- MANDATORY plugins: Context7 + CC Status Line
- Kill session at 50% context. NEVER /compact.
- Cost discipline: $10/session MAX. ONE attempt per approach.

## Testing
- Open in browser, verify globe renders, scroll animations trigger, counters animate
- Check mobile viewport (375px width)
- Verify no console errors
- Lighthouse audit: Performance ≥ 90, Accessibility ≥ 90

## DO NOT
- Change brand colors without explicit approval
- Add npm/build dependencies — keep it a single static HTML file
- Use Inter, Roboto, or Arial fonts
- Break the Three.js globe or canvas animations
- Remove any municipality data
