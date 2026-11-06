# Wheeli handover: Johanah and Kristina take over

From Josh, 6 Nov 2026. **Johanah** takes Wheeli live and owns the code, hosting and backend. **Kristina** owns the content and the Resvita IP, and trains Wheeli. Josh signs off; you two run it.

Read with: `CLAUDE.md` (every feature and file, for whoever changes code, including Claude), `BACKEND-TODO.md` (every saved store and what the backend does with it), `HOW-TO-EMBED.md` (features in plain words).

---

## 0. Start here (10 minutes)

**The links**
- **Build Plan** (the live task list; Josh signs off here): https://claude.ai/artifact/Ff9eYBaPxrfvvRnpXcnFN4
- **Code**: GitHub `main` (this folder, `Website-Embed/`). Build everything with `python3 -I source/build_all.py`.
- **Files**: Google Drive › 0. RESVITA › Wheeli (this guide, the Word copy, `Wheeli-Deck.html`, the ad drafts, the ResVita-IP folder).
- **Launch Pack** (prices, terms, welcome video script, ad concepts, pitch outline): https://claude.ai/artifact/74SH7wgJqd2Bkkd3DZdmvj
- **Landing page mock-up**: https://claude.ai/artifact/S7kKCSzC93ahDmo4uzXA9t · **Backend brief**: https://claude.ai/artifact/WmSZfbfexHEoqvhmgMxXRW

**Where it stands (audit, 6 Nov 2026)**
- Build Plan: **88 items, 84 signed off.** Open: B11 (stop login sharing, Johanah), G4 (Johanah's go-live list), G5 (Kristina's go-live list and tests), B16 (coach cartoons: waiting on Josh).
- **All 20 decks rebuilt and checked**: each one opened with every tab and every Live tool visited, no errors.
- Everything Josh signed off is now in every deck it belongs in (see §2). The welcome tour, the phone tour and the job profit tracker were rolled out to every member deck in this audit.
- Everything still saves in the browser only. Nothing reaches another person or device until the backend is live (§3).

## 1. What Wheeli does today (the short version)

**Members** (every member deck, by programme): Home (30-day path, 90-day win, your crew: Wheeli, Bailey, Flow, the overwhelmed button, refer, follow, share your story), My Dashboard (pinned parts, Working on now, the Resvita Community with Share & collaborate), 10 Miles (coaching paths, 90-day destination, B.I.G Projects), Live tools (Build Your Blueprint with the 99-point check, Pricing with world-class quote PDFs, Get paid, Job profit, Budget, Build the role with team seats, Your week, Tasks, Communication, Live event resources), Get it done (What do I work on, Get it done with Make it mine and the quality check, Asset studio, Review & Improve with the filing cabinet), The Numbers (Bailey's leak check, On track, Budget vs actual, paid ads, ask for a dashboard), Rocket fuel (ProjectU: Project You, Train & Transfer, Get It Done Live, Resvita 50 Weekly Session, Events, Trusted Network, Get there faster; sourcing, Canton Fair, M&A). Plus 🔎 Search and Walk me through, Ask Wheeli / Ask my coach, the welcome tour, Resvita Coin and celebrations, coach pop-ups, and the phone view.

**Coaches** (Coach view, every deck): Today, My clients, Inbox (messages, intros, Get there faster, event bookings, stories, dashboard requests, session ratings, Wheeli feedback, community), Platform content (every list members read, coaching sessions, forms, lessons, Resvita 50, booking links, team drops, Wheeli's jokes & lines, coach characters), the client card (Before the call, milestones, brand, coaching path, calls & context, monthly report, quote details, AI tools, pricing rates, filing cabinet), Wheeli improvements (team tasks, suggestions).

**Resvita admin** (Wheeli deck only, so no client's file holds another client's details): Ad creatives (all 18 drafts on the board), Pitch deck, Access & security (roles, what each person sees, client team seats), Links (every button that goes somewhere), Opportunities (sourcing across clients, shopping list by Canton Fair stand, who knows who with Nudge both).

Every feature, the file it lives in and its store: `CLAUDE.md`.

## 2. What's in which deck

| | Wheeli (Resvita) | Murphy's + 17 clients | Wheeli Free |
|---|---|---|---|
| Every member feature in §1 | ✓ | ✓ (in the client's brand) | Free parts only (path, 99-point check, Pricing, events, network) |
| Welcome tour, phone ▶ Tour, Job profit tracker | ✓ | ✓ (rolled out 6 Nov) | – |
| Coach view (Today, My clients, Inbox, Platform content, client card, Wheeli improvements) | ✓, every client listed | ✓, that client only | – |
| Ad creatives, Pitch deck, Access & security, Links, Opportunities | ✓ | – (by design) | – |
| Blueprint board (Excalidraw) | ✓ trial | – (not signed off) | – |

The phone view (`📱 Mobile` in the top bar) is in every member deck.

## 3. Johanah: getting it live (in this order)

1. **Accounts and sign-in.** Real logins per person (email + code, or Google/Microsoft); replace the coach PIN; one session per seat with a new-device alert (B11). Roles (B9): **Resvita admin** (Josh, Kristina, Johanah: everything) · **Head coach** (Heidi: her clients plus every mindset coach's) · **Coach** (own clients only) · **Support** (messages and setup, no coaching notes) · **Member** (own business only) · **Team seat** (only the areas the owner and coach agree on). Access & security already holds who's who and what each person sees (`access`, with `see`); enforce it on the server.
2. **Storage layer.** One thin layer in `source/` that sends the `<brand>-…` saves to the cloud per member instead of `localStorage`. Order: BACKEND-TODO §1 (the member's own data), then §2 (shared: messages, community, intros, team tasks), then the 6 Nov table at the top of Recent additions.
3. **Content from the backend.** Platform content, Lessons, Coaching sessions, Blueprint forms, B.I.G, Resvita 50, drops, booking links, Wheeli's lines and coach characters save straight to the backend (no more Publish → `add_content.py` → rebuild).
4. **Messages and notifications** through Flow (GoHighLevel): Ask my coach, coach replies, nudges, Get paid reminders (only when the member taps send), Nudge both intros, Resvita 50 timestamps to one client.
5. **Calls**: Zoom on one Resvita account, a licence per coach, cloud recording + transcripts into Calls & context. My clients' next sessions should come from each coach's calendar.
6. **Files and video**: Bunny Stream (or Vimeo) for video, Bunny Storage / Cloudflare R2 for PDFs and uploads, private links.
7. **Claude in Wheeli**: Resvita's own API key on the server (Ask Wheeli, Get it done, Review & Improve, drafted replies, the weekly five jokes). Answers only from the approved Method Library and approved teachings; usage metered per member.
8. **Customer inbox** (phone Messages), **analytics** (Clarity or PostHog with a privacy notice), **phone app** (installable web app → Capacitor → stores).

**Rules that must survive the move**: a client only ever sees their own business; members keep the version of a session, form or plan they started; `teach` and the Method Library are Resvita-wide, everything else is per member; Wheeli never sends on a member's behalf without them tapping send; coach prep (`prep`) never reaches a member.

**Staging before live**: publish `main` to a staging address behind sign-in; Josh and a coach check it; then members.

## 4. Kristina: content, the IP and training Wheeli

**Where content lives**: Coach view › 🛠 Platform content (each item shows TO ADD or DONE; add, hide and re-order anything). Publish to all decks downloads a file; `python3 -I source/add_content.py <file>` then `build_all.py` (Johanah or Claude can run these) until the backend takes over.

**Your IP into Wheeli in one go** (B27): fill in a `lesson.md` card per lesson in ResVita-IP (`_templates/lesson.md`). `python3 -I source/import_ip.py "<path to ResVita-IP>"` is a dry run that reports every match and gap (the first run matched all 38 cards; all still draft). When cards are approved: add `--write --approved-only`, then `add_content.py` and `build_all.py`. Still needing cards: 7 for the Results Pack, 2 for Momentum, 3 for Traction.

**Fill these in first**: Resvita 50 Weekly Session topics (next 8 Thursdays) · Coaches & booking links · Links (tick "Only show what's missing") · Project You lessons (pre-linked to the closest library lessons until the real ones) · Pricing ready-made rates and their groups · Trusted Network listings, logos and offers · Get there faster links · Coach characters (three words and lines for each person) · Wheeli's jokes & lines (approve the weekly five).

**Training Wheeli (weekly)**: Inbox › ⭐ Wheeli feedback (every 👎 becomes a fix, a great question a test question, a question with no method the next interview) and 🧠 Taught by coaches (approve the good replies). Wheeli improvements › 💡 Suggestions shows what members ask for that isn't in the library yet. Best-practice templates (one Markdown file per asset type in the IP folder) set the quality bar Wheeli checks drafts against.

## 5. Working together, and with Claude

- **GitHub `main` is the truth.** Johanah works on a `backend` branch and merges `main` in every day or two. Never merge `Wheeli-Deck.html` by hand: rebuild it and commit it from `main`.
- **Content vs code.** Kristina changes content; Johanah changes code and infrastructure. If content needs a new field, Kristina asks and Johanah (or Claude) adds it.
- **Every change that saves data** gets a line in `BACKEND-TODO.md` › Recent additions.
- **Weekly 30-minute check-in** (Monday): Kristina brings content gaps, Wheeli feedback and Suggestions; Johanah brings what's live and what's blocked; both update the Build Plan. Josh only signs off.
- **Working with Claude** (Claude Code, opened in `Website-Embed/`): it reads `CLAUDE.md` first. The loop that worked for Josh: add an item or a note in the Build Plan, then ask Claude "check the Wheeli Build Plan for new sign-offs, Needs changes notes and answers, and action them". Claude builds in the Wheeli deck first, screenshots it, commits, adds the BACKEND-TODO line, and sets the item to Ready; roll out to every deck once it's signed off.
- **Check before you push**: `python3 -I source/build_all.py` must end "all built". Open the Wheeli deck and click through the page you changed.
- **Decisions only Josh makes** are the items with a question in the Build Plan. Everything else, decide between you and note it there.

## 6. Go-live lists (G4 and G5 in the Build Plan)

**Johanah**
- [ ] Texts, nudges and emails through Flow (one workflow per nudge type; templates, opt-outs and records stay in Flow).
- [ ] Get paid: 📤 Send via Flow sends the member's approved draft and ticks the step (requests queue in `getpaid` › `sendQ`).
- [ ] Coach booking links and meeting rooms saved to the backend (`booking`, `coach-rooms`).
- [ ] Heat maps (Clarity or PostHog) with a privacy notice; numbers and messages masked.
- [ ] Connect clients' own AI tools (MCP where the tool has one, otherwise OAuth or their API key, stored encrypted).
- [ ] App stores: privacy policy, terms, real sign-in, delete-my-account; web app first, then TestFlight / Google testing.
- [ ] Login sharing (B11): one active session per seat, new-device email, exports carry the member's name and date.

**Kristina**
- [ ] Zoom: one Resvita account, a licence per coach, recording and transcripts on.
- [ ] Best-practice templates in the IP folder (capability statement, brochure, social post, landing page, Meta ad, quote), confirmed.
- [ ] Approve the lesson cards and run the import (above).

**Go-live tests (both)**
- [ ] Every booking, link and send button goes somewhere real (Coach view › Links shows what's missing).
- [ ] A coach and a test member run a full week: Ask my coach and an answer round, a Get It Done Live and a Resvita 50 RSVP, a call logged in Calls & context, a session rating, a milestone congratulated.
- [ ] AI creative tools with a test member, checked against the templates and the cost per member.
- [ ] Each programme level shows the right parts (set a test member to Start Right, then Grow, Build, Partner).

## 7. Still open (Josh's calls)

- **B16 coach cartoons**: Heidi, Nadja and Johanah are their photos on the same Handle It circle as the cartoons; true cartoons when Josh makes them with the prompt in B16. And what Alyssa does, so she pops up at the right moment.
- **Coach view sidebar**: three options drafted (`team-mockups/coach-sidebar-options.png`); Claude recommends B (four doors + Resvita HQ).
- **Prices for rewards** (C3: prize prices against ~500 coins a month), **the Google review link** (C2), **which programmes get the job profit tracker** (C12: every programme from Start Right for now), **ads to the agency** (E8/E10; #11 and #14 need real proof), **the Filson Pro font** (A6: the Adobe Fonts project id), **real client names in the Community examples** (C5: fine in client decks until the backend is live?).

Answered and built: Synergy Lab states and seats, admins and coach access, team seats ($29–$49 a seat, $39 to start), referrals, social links, Claude on Resvita's own account, programme prices (Start Right $3,000 + $997 × 6 · Grow 1.0 $5,000 + $1,997 × 12 · Build 2.0 $9,000 + $3,497 × 12 · Partner 3.0 $15,000 + $7,997 × 12, inc GST), platform-only price and terms (the Launch Pack), the Resvita 50 Weekly Session, brand option A and the button system.

## 8. Placeholders to replace before members see them

Example data shows until a member adds their own (marked "example" in the deck): Bailey's leaks, Flow's quotes, Get paid invoices, the six example jobs, team tasks, the Community's example posts and members, the Share & collaborate posts, Wheeli's example Suggestions. Content still to confirm: the 99-point check wording (until Resvita's checklist), the B.I.G Projects tasks, the 20-20 Vision rituals, the Project You lessons (pre-linked), event dates other than Synergy Lab, the Mission figures and the Boardroom date. Coaches' next sessions in My clients are example times until calendars sync.
