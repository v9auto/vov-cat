# DESIGN.md — vov.cat «SELENE» rebuild (branch: selene-rebuild)

Concept in one sentence: **老六的登月之旅** — the white kitten's scroll-driven voyage
from his home on Earth to the Moon and back, told in SELENE's cinematic language:
dust that clears on scroll, six parallax layers, a trajectory that inks itself to
384.400 km, a horizontal mission reel, and an Earthrise finale. Alignment: everything
is centred on a single vertical journey axis; acts are separated by near-black pauses;
nothing animates on a timer — all motion is scroll-scrubbed and reversible.

## Colour tokens (lunar)

| Token | Value | Role |
|---|---|---|
| `--ink` | `#060809` | Deep night ink — page ground, act breaks |
| `--ink-2` | `#0D1013` | Raised ground — caption blocks, lightbox |
| `--moon` | `#ECEEF0` | Moon white — display type, primary text |
| `--silver` | `#C9CDD2` | Moon silver — secondary text, hairlines, HUD |
| `--dust` | `#969CA4` | Dust grey — body copy, captions, chips |
| `--amber` | `#E8A33D` | Earthlight amber — THE warm accent: trajectory ink, counter numerals, stop markers, the rewind control. Used nowhere else. |
| `--ice` | `#A8C4DE` | Ice tint — reel frame numbers only (SELENE's numeral voice) |

The Earth in the finale is drawn as a photographic sphere (its own blues/greens) —
it is a picture of home, not a UI colour, and it is the only place saturated colour
appears outside the photographs themselves.

### Contrast (verified, WCAG ratios against `--ink #060809`)
- `--moon` on ink: **17.3 : 1**
- `--silver` on ink: **12.6 : 1**
- `--ice` on ink: **11.1 : 1**
- `--amber` on ink: **9.3 : 1**
- `--dust` on ink: **7.3 : 1** (body copy floor — never used smaller than 15px under 7:1 elsewhere)
- ink on `--moon` (inverse chips): **17.3 : 1**
Every text/background pair on the page is ≥ 7 : 1, comfortably past the 4.5 : 1 line.

## Type
Three voices, matching SELENE's treatment:
- **DISPLAY** — Baloo 2 (700), wide letterspacing (0.12–0.4em) for chapter titles,
  the giant finale wordmark, reel titles. Baloo's rounded terminals keep the cat in
  the room; the tracking gives it SELENE's mission-control posture.
- **DATA** — ui-monospace / "SF Mono" / Menlo / Consolas stack (no webfont load):
  distance counter, HUD readouts, frame numbers, chips. Data is always mono.
- **BODY** — Nunito (400/600): all sentences, bilingual captions. Catalan first,
  Chinese second — the site's established voice, unchanged.
Type evolution note: the previous build used Baloo 2 + Nunito only. SELENE's language
is unthinkable without its mono data voice (the counter IS the design), so a system
mono stack joins as the third voice — system stack, zero added weight.

## The ONE bold place
**The Earthrise finale.** Everything before it is silver, dust and ink; the finale
is where the Earth — full colour, glowing rim — rises over the horizon behind the
giant sliding wordmark while the cat watches from the rocks. Colour, scale and
motion budgets are all spent there. Everywhere else: quiet, grey, exact.

## Motion language
- Scroll-scrubbed only (GSAP ScrollTrigger + Lenis smoothing). No fade-up on enter,
  no hover animations except the reel frame's slight lift and the moon cat's bounce.
- Hero dust: veil scrubs off over the first ~90vh (blur 10px→0, brightness .72→1,
  milky overlay .85→0, fog sinks +6vh).
- Parallax depths (hero, back→front): stars 0 / nebula −2 / Moon −6 / far ridge −10 /
  dust band −16 / plain −24 / near rocks −34 (yPercent over the pin); pointer parallax
  on fine pointers only, multipliers 0.1→1.0 back-to-front.
- Trajectory: SVG stroke inks with scroll; counter = round(progress × 384400),
  formatted `384.400`; chapter cards settle from scale 1.16 → 1 (the NAÏADE landing).
- Reel: pinned, lateral scrub, card 3:4, gap 28px, hairline progress.
- Finale rewind: 2.2s smooth return with a brief blur/saturate ghost (the rewind smear).

## Rules kept (blacklist)
No purple/blue gradient wash (nebula is a desaturated grey smudge at 8% opacity),
no glassmorphism, no SaaS card kits (reel photos are borderless; chapter cards are
editorial blocks on ink-2, one per stop), no ALL-CAPS eyebrow on every section
(eyebrows exist only where SELENE has them: hero lockup + chapter data lines),
no scattered fade-ups, no emoji icons — line SVG only (crescent, speaker, paw,
arrow), focus-visible outlines in amber.

## Content law
- All 19 gallery items keep their ORIGINAL Catalan + Chinese captions, verbatim
  (verified by programmatic diff against main).
- New writing is limited to chapter headings/connective lines in the same bilingual
  voice, and is marked as new in the build notes.
- Only contact on the site: rbiovv@gmail.com. No X/GitHub/social links, ever.
- Media lives in ONE JS data array; hero/chapters/moon/reel/lightbox all reference
  it by index — no data URI is ever duplicated.

## Generated companion visuals (added 2026-11-26, user-supplied)
Two AI-generated stills of the real Lao Liu (identity from his photos: grey head
patch, pink nose, blue eyes) join the page as *想象图 · visualització*, each carrying
a small honest label in mono type: `moon-hero.jpg` (touchdown — hero reveal +
moon-surface panel, with `moon-ambient.mp4` as its living layer, desktop only) and
`zero-gravity.jpg` (the orbit chapter). They are illustrations of the voyage; the
19 real photographs remain the documentary record and keep their original captions.
