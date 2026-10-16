# Westwood Women’s Soccer Boosters: Website Handbook

- **Live site:** https://wwsboosters.org
- **Club email (owns every account):** wwsbooster@gmail.com
- **Last updated:** October 2026

This handbook is for whoever keeps the booster website up to date. You don’t need to know how to code. Everything visitors see comes from one file, **index.html**, in this repository.

---

## 1. Accounts the club uses

Every account is registered to **wwsbooster@gmail.com**. Handing over that email hands over everything below.

| What | Where | Notes |
|---|---|---|
| Domain name (wwsboosters.org) | **Porkbun** (porkbun.com) | Auto-renew ON. Renews once a year, under $12. Don’t change the DNS records (see section 6). |
| Website hosting | **GitHub**: organization `westwood-soccer-boosters`, repository `website` | Free. GitHub Pages publishes the `main` branch automatically. |
| Dues, fees, team meals | **Cheddar Up** | https://team-booster-2026-2027.cheddarup.com |
| Sponsorships | **Cheddar Up** | https://team-sponsorship-2026-copy-25932.cheddarup.com |
| Volunteer and committee sign-ups | **SignUpGenius** | https://www.signupgenius.com/go/10C0949AEAE22A3FEC52-66751535-westwood. Committees use an **access code**, shared in the team app only. **Never put the code on the website.** |
| Reimbursements | **Google Form** | Linked from the Support section |
| Donations | **Square** | Not set up yet. The Donate button was removed until it is. |
| Game-day info for team families | **Team app** (Stack Team App) | The team app is the source of truth for times and changes. The website says so in two places. |
| Social media | Instagram **@westwoodgirlssocceratx**, X/Twitter **@WWGirlsSoccer** | |
| Graphics | **Canva** | Keep designs in the booster account so they transfer with the club. |

---

## 2. How to update the site

Pick whichever is easier for you.

**Option A: Ask Claude to do it (easiest)**

1. In Claude, connect GitHub (the GitHub app at github.com/apps/claude) and give it access to the `westwood-soccer-boosters` organization, `website` repository.
2. In a Claude chat, say what to change, for example: *“In westwood-soccer-boosters/website, add the result: Varsity beat Cedar Ridge 2–1.”*
3. Claude edits index.html and publishes it. The live site updates within 1–2 minutes.

**Option B: Upload it yourself**

1. On GitHub, open `website`, click **index.html**, then the **download** button.
2. Attach that file to any Claude chat and ask for the change.
3. Back on GitHub, click **Add file → Upload files**, drag in the new index.html (it replaces the old one), then **Commit changes**.

Either way, open https://wwsboosters.org on your phone afterward to check.

---

## 3. Where each part of the site lives (inside index.html)

You can tell Claude these names, or search for them if you edit the file yourself.

| Part of the site | What to look for in index.html |
|---|---|
| Games and events (schedule and calendar) | `const EVENTS=[` |
| Monthly booster meetings | `const MEETINGS=` (first Wednesday, 6–7 PM; December skipped) |
| Scores and record | `const RESULTS={` — add lines like `"2027-01-22|varsity":"2-1"` (our score first) |
| Varsity and JV rosters | `const ROSTER={varsity:[],jv:[]}` — number, name, position, class only |
| Sponsors (logos, names, links) | `const SPONSORS=[` |
| Sponsor levels and perks | `const TIERS=[` (must match Cheddar Up) |
| Featured Partner of the Week | Rotates every Monday through Warrior and Orange sponsors. To pin a business to a week: `const SPOTLIGHT_PINS={` |
| Map links for venues | `const MAPQ={` |
| Support cards (dues, sponsor, reimbursement, social) | `<section id="support"` |
| Volunteer sign-up list | `<div class="signups" id="signups">` |
| Booster board names | `<ul class="board-list">` |
| Draft-free page title and Google description | top of the file, in `<head>` |

---

## 4. Common updates, in plain words

- **Post a score:** “Add result: Varsity vs. McNeil on Feb 9, we won 3–1.” Scrimmages show in the list but don’t count toward the record.
- **A game moved:** “Move the Feb 12 Lake Travis game to Feb 11 and add a ‘Moved from Feb 12’ note.”
- **New event:** give the date, time, place, and whether it’s Varsity, JV, both, or booster club.
- **New sponsor:** send the business name, level (Warrior, Orange, or White), website, slogan, and logo file. Warrior and Orange get a logo, a link, and the weekly spotlight. White is listed by name only.
- **Roster:** jersey number, name, position, graduation year. Nothing else (no birthdays, hometowns, or contact info).
- **Photos:** each photo needs a one-line description for screen readers (for example, “Varsity celebrating after the McNeil game”).

---

## 5. Start of each new season

- [ ] Replace the schedule (`EVENTS`) with the new season’s games, and update the playoff dates.
- [ ] Clear last season’s scores (`RESULTS`) and rosters (`ROSTER`).
- [ ] Update meeting months (`MEETINGS`) and the board names.
- [ ] Make new Cheddar Up pages (dues, sponsorship) and update both links.
- [ ] Make new SignUpGenius sign-ups and update the links. Set a new committee access code.
- [ ] Renew or remove sponsors, and check the sponsor perks still match Cheddar Up.
- [ ] Change “2026–27” wherever it appears.

---

## 6. Things not to change

- **The CNAME file.** It tells GitHub to use wwsboosters.org. Deleting it takes the site off the domain.
- **The DNS records at Porkbun:** four **A** records (blank host) pointing to 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.153, and a **CNAME** for `www` pointing to `westwood-soccer-boosters.github.io`.
- **GitHub → website → Settings → Pages:** source is the `main` branch, folder `/ (root)`, custom domain `wwsboosters.org`, **Enforce HTTPS** on.
- **The repository must stay Public** (required for free GitHub Pages).

---

## 7. Handing off to the next person

1. GitHub: **github.com/westwood-soccer-boosters → People → Invite member**, and make them an **Owner**.
2. Give them access to **wwsbooster@gmail.com** (share or reset the password; keep passwords out of this file).
3. Point them to this handbook.
4. Once they’re set, remove yourself or lower your role under **People**.

---

## 8. Ground rules

- The site meets accessibility standards (WCAG 2.1 AA) and works on phones. Keep it that way: photos need descriptions, and flyers should be posted as text, not just images.
- Players are minors. Post only what’s listed above for rosters, and check with the coach before adding player names or photos.
- Never post passwords, access codes, or personal phone numbers on the site or in this repository. The repository is public.
