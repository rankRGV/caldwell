# Caldwell Humane & Animal Services Consultants — Sample Homepage

A single-page Astro sample built to show what a custom site could look like vs. the Wix placeholder.

## Run it
```bash
cd Caldwell
npm install      # first time only
npm run dev      # → http://localhost:4321
npm run build    # static output to dist/  (deploys to Vercel like the other sites)
```

## Design decisions (the "why")
- **Direction:** refined editorial / institutional warmth — positions him as a *premium mission-driven consultant*, not a pet-clinic site. This is what keeps it from looking like AI slop.
- **Palette** (pulled straight from his graphics): navy `#16243f`, olive `#6e7a37`, gold `#c6a14b`, cream `#f4f1e7`.
- **Type:** Cinzel (wordmark, matches his logo) · Fraunces (display serif + italic for the "script-feel" words) · Hanken Grotesk (body). Deliberately not Inter/Roboto.
- **Psychology layer:** hero leads with the outcome ("More lives saved"), a contrast-effect problem section, authority-bias About, one repeated CTA.

## Sections
Header → Hero → values marquee → The Challenge (4 pressures) → Services (6 pillars) → Approach → About → CTA → Footer.

## Images
- `public/images/hero-real.jpg` (hero) and `approach-real.jpg` (approach) — **real photographs from Pexels** (free for commercial use, no attribution required). Swapped in to replace the AI-rendered look.
- `img1–img5` — his original AI brand graphics (kept in repo, currently unused on the page). Available if he wants them back anywhere.

## ⚠️ Placeholders to fill after he confirms details (search the code for `TODO`)
1. **Founder bio** in the About section — the credibility anchor. Needs his real story.
2. **About stats** (`[ — ]`) — years, orgs supported, grant dollars. **Honest-proof rule: no fabricated numbers.** Left blank on purpose.
3. **Contact** — currently `hello@caldwellhumaneconsultants.com` (guess) + a `mailto:`. Swap for his real email / a real form (FormSpark like the other sites).
4. **LinkedIn link** in footer.
5. **Final hero photography** — the crop works, but if he wants pristine quality he can generate text-free AI photos (he already has the tooling).

## Open questions for him
- Exact services / packages and whether pricing goes on the site
- Real customer type (shelters? municipalities? nonprofits?) to sharpen copy
- Service area / geography
- Does he want a contact form, booking link (Calendly), or just email?
