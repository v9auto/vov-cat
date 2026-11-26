# DESIGN.md — vov.cat redecorate-hybrid

Tokens evolved from the CURRENT site's :root palette. The warm cocoa/cream identity
stays; nothing is rebranded. New sections (hero, journey, page gallery) use only these.

## Colors
| Token | Value | Role |
|---|---|---|
| `--bg` Nits (night) | `#000000` | Page/stage ground — the ASCII-video darkness the site already lives on |
| `--card` Cacau (cocoa) | `#2E2015` | Card and caption-card surface |
| `--ink` Crema (cream) | `#F6E8D8` | Primary text (contrast on #000 ≈ 16.5:1, on Cacau ≈ 11.9:1) |
| `--ink-soft` Llet condensada | `#CBA98C` | Secondary text (on #000 ≈ 9.6:1, on Cacau ≈ 6.9:1 — body-safe) |
| `--accent` Albercoc (apricot) | `#F0975F` | Interactive accent, caption titles' partner color |
| `--accent-strong` Albercoc clar | `#F7AC7C` | Caption titles (.ca-cap already uses it), hover states |
| `--gold` Or (gold) | `#EFB254` | Journey progress rail active stop, rewind button |
| `--rose` Rosa (rose) | `#D98A6D` | Hero reveal-state word (DORMINT) — the pink-nose color |
| `--line` Vora (edge) | `#4A3220` | Borders/dividers (structural only, never text) |
| `--lime` Llima | `#ceff1c` | RESERVED: existing play-FX only (gate paw, intro). Not used in new sections' UI |

## Type (max 2 families — the ones the site already loads)
- Display: "Baloo 2" — headlines, hero word, caption titles. Rounded, warm, kitten-soft.
- Body: "Nunito" — paragraphs, captions, UI text. Chinese falls back to
  "PingFang SC" / "Hiragino Sans GB" / "Microsoft YaHei" as today.
- Type roles: hero word clamp(3.5rem, 14vw, 10rem) Baloo 800; section titles
  clamp(1.9rem, 6vw, 3.2rem) Baloo 800; caption title 1.05rem Baloo 700
  accent-strong; body 17px/1.6 Nunito (site standard).

## Layout concept
One sentence: **A dark warm room you scroll through like a camera — the cat is always
the largest thing in frame, everything else is a quiet caption at the edge.**
Left-aligned captions, full-bleed photography, generous black breathing room;
structure lines (--line) only where they separate real things.

## The ONE bold place
The hero cat: layered pointer parallax + feathered-circle reveal that swaps the
cat's state (awake ↔ asleep) and flips the giant headline word, plus a springy
squash-and-meow on drag. Everything else — journey included — is calm, scrubbed,
and quiet. Boldness is spent here only.

## Principles for the new sections
- Photography first: journey slides are full-bleed, no card frames around photos;
  the caption card is small, cocoa, and anchored to a corner (NAÏADE-style settle).
- Numbers only when they mean something: the journey rail's 01–05 are the photo's
  real position in the gallery story.
- No purple/blue gradients, no glassmorphism, no SaaS card kit, no ALL-CAPS
  eyebrows, no scattered fade-ups (motion is scrubbed or physics, never ambient),
  no emoji icons — line SVG only (paw/arrow paths already in the site's vocabulary).
- prefers-reduced-motion: journey un-pins into stacked stills, parallax/reveal off.
- Focus visible everywhere (:focus-visible outline in --gold), 390px safe.
