# Notes for Claude: Westwood Women’s Soccer Boosters website

This repository is the live site at https://wwsboosters.org, published by GitHub Pages from `main` (root). Every push to `main` goes live within a couple of minutes. The person asking is a booster parent volunteer, not a developer: explain in plain words and skip git jargon. See README.md for the full handbook and account list.

## Files
- `index.html`: the whole site (HTML, CSS and JS in one file). It is the single master copy. Edit it directly; there is no build step.
- `CNAME`: must contain exactly `wwsboosters.org`. Never delete or change it.
- `favicon.png`, `apple-touch-icon.png`, `og-image.png`: icons and the link-preview image (1200×630).
- Sponsor logos or photos, if added, go in folders like `sponsors/` and `photos/`, referenced with relative paths.

## Where the data lives in index.html
- `EVENTS`: schedule. Fields: `d` (YYYY-MM-DD), `end` (multi-day), `t`/`tEnd` (24h "HH:MM"), `title`, `team` (`varsity` | `jv` | `both` | `all` for booster club), `kind` (`game` | `event`), `ha` (`Home` | `Away` | `Tournament`), `where`, optional `map`, `desc`, `note`, `bye`. Helpers: `pair(date,title,ha,where,note,jvTime,vTime)` makes a JV + Varsity game; `bye(date)` makes a BYE. Default district times: JV 4:45 PM, Varsity 6:30 PM; scrimmages and tournaments use their printed times. Home venue is `HOME` ("Warrior Bowl").
- `MEETINGS`: first Wednesday of each listed month, 6–7 PM. December is intentionally skipped.
- `RESULTS`: `"YYYY-MM-DD|varsity":"us-them"`. Scrimmages (title contains "Scrimmage") are listed but not counted. District = Home/Away non-scrimmage games from Jan 22 to Mar 12, 2027.
- `ROSTER`: `{varsity:[{num,name,pos,grad}], jv:[...]}`. Minors: post only number, name, position and graduation year.
- `SPONSORS`: `{name, tier:"warrior"|"orange"|"white", url, logo, slogan}`. Warrior and Orange get logo, link and the weekly Featured Partner spotlight; White is listed by name only.
- `TIERS`: sponsor levels and perks. Must match the Cheddar Up sponsorship page.
- Season-specific links: the Cheddar Up dues link (Support section), the sponsorship link (`SPONSOR_URL` and the Support card) and the SignUpGenius links (`#signups`) are for 2026–27 only. Each new season they get new links; ask the user for them rather than reusing old ones.
- `SPOTLIGHT_PINS`: `{"<Monday YYYY-MM-DD>":"Sponsor Name"}` to pin a sponsor to a week.
- `MAPQ`: venue name → Google Maps search text.
- Support cards: `<section id="support">`. Volunteer sign-up list: `<div class="signups" id="signups">` (order: Committees and Coaches’ Meals, then Varsity, then JV). Board: `<ul class="board-list">`.

## Rules
- Keep it accessible (WCAG 2.1 AA) and phone-friendly: alt text on every image, no auto-moving carousels, colors from the CSS tokens at the top of the style block, light and dark themes both working.
- The team app is the source of truth for game times. Keep both "Team families" notices.
- Never put the SignUpGenius committee access code, passwords or personal phone numbers on the site or in this repository (it’s public).
- Don’t add a card whose link is a placeholder (`href="#"`); leave it out until the real link exists.
- After editing, sanity-check the script (no syntax errors), then commit with a short plain-English message and push to `main`. Tell the user what changed in one or two sentences.
