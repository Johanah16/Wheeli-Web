# Backend to-do

For Johanah. Every Wheeli deck saves to the member's browser today (`localStorage`, one key per feature, named `<brand>-<store>`, e.g. `wheeli-tasks`, `murphys-budget`). The backend takes these over behind the same calls, so the pages don't change. This list is every store, what it holds, and what the backend needs to do with it.

**How this list stays current:** whenever a feature that saves data is added or changed, a line goes in **Recent additions** at the bottom (Claude does this with each change). Work through it top to bottom; tick a store once it saves to the backend.

- **6 Nov 2026 · Reports this month (H7):** same store `<brand>-report-coach`; a drafted-but-not-saved entry has `draft: 1` and no `at` (only `at` counts as done). Content gaps (H11) and the unpublished-edits warning (H10) save nothing.

- **6 Nov 2026 · Real checklists (not live yet):** no new store. When switched on, answers stay in `<brand>-byb-sheet` › `check`, keyed by the new ids (`p0-0`, `g0-0`, `s0-0`, `f0-0`), with a value of 1 / 0.5 / 0; content from `source/checklists.json`.

`CLAUDE.md` explains each feature in full. The plan is the Wheeli Backend Architecture Brief: https://claude.ai/artifact/WmSZfbfexHEoqvhmgMxXRW

---

## 1 · The member's own data (sign-in first, then move these to the cloud)

One record per member. Only that member (and their coaches) can read it.

| Store | What it holds | Written by |
|---|---|---|
| `tasks`, `tasks-inbox` | Tasks; the inbox is where other tools drop new tasks (lessons, calls, Make it mine, Update my numbers) | Live tools › Tasks, many tools |
| `week` | Your week: ideal and actual week, actions, Friday reviews (`hist`) | Live tools › Your week |
| `focus` | My one thing and the moves for it | Home › Today |
| `home`, `home-byb`, `home-byb-sum`, `week1-done` | Home: days and minutes of 20s, the 30-day path ticks, sign-offs | Home |
| `tenmiles` | Your 10 Miles: goal, the 10 miles, coach's pinned moves | 10 Miles |
| `monthly` | Monthly measurements: Life ROI and life score history | 10 Miles |
| `ontrack` | On track: monthly revenue, gross and net profit, targets | The Numbers |
| `budget` | Chart of accounts, budget by month, actuals, what goes across to The Numbers | Live tools › Chart of accounts & budget |
| `feed` | Update my numbers: bank / owed / owe, jobs CSV, pipeline CSV, P&L month, column mappings | Live tools › Update my numbers |
| `byb-sheet`, `byb` | Build Your Blueprint: costs, team, cost per billable hour, health checks, the 99-point check (`check`), planner | Live tools › Build Your Blueprint |
| `chargeout` | Charge-out rate | The Numbers › On track |
| `pricing`, `pricing-biz` | Saved quotes, packages, Popcorn; business details for PDFs (logo, ABN, terms) | Live tools › Pricing; Coach view › Quote details |
| `roles` | Build the role: roles, people, candidates, meta programmes, training | Live tools › Build the role |
| `grow` | ProjectU: Project You, Train & Transfer scores, events booked, Get It Done Live going | Rocket fuel › ProjectU |
| `foundation` | Foundation Form answers (+ attached file names) | Foundation Form |
| `blueprint` | Blueprint parts: status, who signed off, when, note | Home › Blueprint (coach signs off) |
| `asset-mine`, `<brand>-kept-assets` | Asset studio: Make it mine answers, pinned cards; kept assets | Get it done › Asset studio |
| `improve`, `gid-handoff`, `cv-pending` | Get it done and Review & Improve hand-offs, CVs waiting to be scored | Get it done |
| `boards` | Blueprint boards (Excalidraw), Wheeli deck only | Live tools › Blueprint board |
| `boardroom`, `boardroom-next`, `mission-members`, `newbiz`, `ma` | Rocket fuel: Boardroom, Our 2027 Mission, new business ideas, mergers & acquisitions | Rocket fuel |
| `dashboard` | My Dashboard: which parts are pinned, and their widths | My Dashboard |
| `lessons` | Lessons watched (id → time) | Lesson player |
| `lesson-work` | Sub-task ticks and uploaded file names per lesson | Lesson player |
| `game` | Level, XP, badges | Everywhere |
| `wheeli-chat`, `ask-week` | Ask Wheeli conversation, free-level question count | Ask |
| `flow-done` | Quotes marked followed up on Flow's page | Live tools › Flow |
| `ads` | Paid ads by month: platform, shown, clicks, report enquiries, spend, real enquiries, quoted, jobs won, average job, margin, agency fee, agency check counts, score, file | Get it done › Review & Improve › Paid ads; read by The Numbers and the monthly report |
| `teach` | Answers coaches taught Wheeli (question, answer, by, status new / approved / no). Approved ones are answered by Ask Wheeli for every member, so this is shared across all members (like the Method Library), not per member | Coach view on a phone › + Teach Wheeli this; Inbox › Wheeli feedback |
| `coach-hours` | Each coach's answer rounds: times, days, quiet-hours start (defaults in hub.json › rounds). Notifications to coaches should respect quiet hours | Coach view › Inbox › Messages |
| `session-agenda` | Things a member saved for their next Mindset / Strategy session (role, kind, text, used = the session id once done). The coach sees them before the session | Ask my coach; coaching sessions |
| `comms-sent` | Which customer messages the member marked as sent, and when (keyed by subject until real message ids exist) | Phone › Messages |
| `intros` | Intro requests from the Business audit and Trusted Network: area or partner, when asked, who was introduced, note, status (new / introduced / done / not needed). The coach's Inbox › Intros list; should be shared between the member and their coaches | Home › audit, Rocket fuel › Trusted Network; Coach view › Inbox › Intros |
| `audit` | Complete business audit: per area asked / done / skipped, who they use if skipped, when | Home › Your journey |
| `vision` | 20-20 Vision: which ritual items were ticked each week, month and quarter | Home › Your journey |
| `bigprojects` | B.I.G Projects: each project's tasks (done, due), plus stages the coach marked already in place | 10 Miles / My Dashboard (member), client card (coach) |
| `bpforms` | Blueprint forms: per form the answers (by question id), the section they're up to, when sent, and a copy of the form as it was when they started | Home › Your Blueprint forms (member), client card (coach) |
| `coaching` | Coaching sessions: per session the pre-session form answers, sub-tasks ticked, upload names, done (when, signed by, member or coach), opened early, and a copy of the session as it was when they started | Your coaching (member), client card (coach) |
| `programme` | The member's programme level, parts turned on or off, Focused view | Coach view (per member) |

## 2 · Shared between people (needs the backend to work at all)

**Move first (Build Plan H1): the Resvita-wide team stores.** These live in one coach's browser today and feel shared but aren't: `improve`, `team-tasks`, `ad-creatives`, `access`, `booking`, `coach-chars`, `drops`, `wheeli-lines`, `r50`, `gidl`, `content`, `lessons-custom`, `coaching-content`, `bpforms-content`, `report-coach`, `coach-calls`, `context`, `opp-shop`, `opp-nudges`. Mark them **shared, Resvita-wide**, one copy for the whole team, and load them before anything else in the Coach app.

| Store | What it holds | Who sees it |
|---|---|---|
| `community` | Feed posts, likes, comments, pins, answered, hidden | All members (and coaches) |
| `community-me` | My profile in the Members directory, connections, member-to-member messages sent | All members see the profile; messages go to the other member |
| `messages`, `msg-read` | Ask my coach threads (Strategy, Mindset, Resvita team), read markers | The member and that coach |
| `hub-posts`, `hub-pins`, `hub-hidden`, `hub-read` | Updates & news posted by coaches; pinned, hidden, read | Coaches post; every member reads |
| `hub-calls`, `hub-callnotes` | Coaching calls: booked calls, and notes, recording and actions after each | The member and their coaches |
| `gidl` | Get It Done Live sessions, live room, recordings | Coaches edit; every member |
| `coach-notes` | Coach notes per client (shared ones reach the member) | Coaches; shared notes to the member |
| `coach-calls` | Calls & context: each call's transcript, summary, actions, what Wheeli learnt, approved or draft | That member's coaches |
| `context` | What Wheeli has learnt about each member (approved facts, each with its source call) | Coaches; read by Wheeli for that member only |
| `report-coach` | The coach's two monthly report boxes, per client per month | Coaches write; the member's report shows them |
| `coach-assign`, `coach-status`, `coach-order` | Which coaches each client has; status and order in the Coach view list | Coaches |
| `quote-details` | Quote details for other clients, kept until synced | Coaches |
| `new-clients`, `programmes` | New clients set up in the Coach view; programme per client | Coaches |
| `wheeli-feedback`, `wheeli-feedback-review` | 👍 / 👎 on Wheeli's answers, and the weekly review | Member writes; coaches review |
| `fast-interest` | Get there faster requests (1% Tradie, Results@, Support Structure) | Coaches |

## 3 · Content coaches publish (replace the download-and-rebuild step)

| Store / file | What it holds |
|---|---|
| `content` + `source/content.json` | Platform content: 99-point check, 30-day path, Free path, events, Trusted Network, offers, Project You lessons, pricing rates, Top 50 |
| `bigprojects-content` + `source/big-projects.json` | Resvita's starting tasks for the 12 B.I.G projects (the projects themselves are set) |
| `bpforms-content` + `source/blueprint-forms.json` | The Build Your Blueprint forms (sections, questions, which programme gets each) |
| `coaching-content` + `source/coaching.json` | Coaching sessions (Mindset and Strategy, onboarding by programme and member sessions) and the shared pre-session forms |
| `lessons-custom`, `lessons-deleted`, `lessons-boxes` + `source/lessons.json` | Courses and lessons (sections, lengths, sub-tasks, outcome, upload, resources, free preview, steps, cards) and Blueprint box links. 15 courses, 404 lessons |
| `source/hub.json` | Starting updates, calls, community examples, Get It Done Live |

Today: a coach edits, taps ⬆ Publish to all decks, and `add_content.py` writes the file before a rebuild. With the backend: Save writes straight to the backend and every deck reads it on load.

## 4 · Files (Australian storage)

Lesson uploads (`lesson-work`), event uploads (`event-uploads`, `event-files`, `event-pick`), CVs (`cv-pending`), community photos (in `community`), Foundation Form attachments, message attachments, call recordings and transcripts. Today only file names (or small images) are kept in the browser.

## 5 · Keep in the browser (per device, no backend needed)

`timer`, `mobile-tab`, `mobile-tf`, `today-hidden`, `mobile-today-hidden`, `coach-session`, `coach-dbview`, `first-seen`, `last-visit`, `home-last-visit`, `video-seen`, `nudge`, `alerts-read`, `fast-hide`, `msession`, `session`, `roi-hits`, `blueprint-coach` (the coach's name on this device), and each page's `<view key>-col` / `-ord` (collapsed sections and order). These can sync later if members want the same layout on every device.

---

## Recent additions

Newest first. One line per change that adds or changes saved data.

### The 6 Nov 2026 stores, sorted (audit for the takeover)

Every store added on 6 Nov, by what the backend has to do with it. The full shape of each is in its line below.

| Kind | Stores |
|---|---|
| **The member's own** (per member, sync after sign-in) | `getpaid` (+ `sendQ`), `jobs`, `win90`, `focus-course`, `cabinet`, `<storeKey>-coins`, `grow` (`ev`, `evLabel`), `gidl-rsvp`, `r50-q`, `ratings`, `stories`, `net-reviews`, `dash-req`, `search`, `team-scorecard`, `week` (+ `labels`, `team`), `collab`, `referrals`, `milestones`, `wt-20`, `wt-phone`, `<home>-team-pop` |
| **Coach writes about a member** (per member, coaches and that member) | `rate-cats`, `brand-edits`, `midmonth`, `coach-outbox`, `milestones-ack`, `ai-tools`, `access` › `clients` (team seats: member requests, coach agrees) |
| **Shared between people** (needs the backend to work at all) | `collab` (other members' posts), `opp-nudges` (to both clients), `r50-sends` (timestamps to one client), `access` (sign-in, roles, `see`), `coach-rooms` |
| **Resvita-wide content** (the team writes, every member reads: replace Publish → rebuild) | `r50` (+ `recs`), `drops`, `booking`, `wheeli-lines`, `coach-chars`, `coaching-content` (`prep` is coach-only: never send to members) |
| **Resvita team only** (never in a member's Wheeli) | `improve`, `team-tasks`, `ad-creatives`, `opp-shop`, Opportunities' read of every client's Rocket fuel lists |

- **6 Nov 2026** · `improve` (new, Resvita-wide, team only): `{ items: [{ id, t, d, type, pri, when, client, from, st, note, at, upd }], lastWeekly, lastMonthly }`, the Wheeli improvements board in the Coach view.
- **6 Nov 2026** · `gidl-rsvp` (new): `{ sessionId: { st: 'yes'|'no', time, topic, q, at } }` (member writes, coaches read: list every member's RSVPs per session in the coach room). `gidl` recordings now carry `stamps` (timestamps text). Platform content kinds can hold `_order`, added items (`add: 1`, `area`, `grp`) and `hide: 1`. `gidl-rsvp-ask` is browser-only (asked today).
- **6 Nov 2026** · `grow` › `ev`: an event with state options (Synergy Lab: QLD 20 Jan, NSW 21 Jan, VIC 22 Jan 2027, 25 seats each) now saves `'<booked at ISO>|<option id>'` (e.g. `'…|qld'`). Count seats per option and stop booking at 25.
- **6 Nov 2026** · `r50` (new, Resvita-wide, coach writes): the Resvita 50 Weekly Session `{ title, day, time, mins, room, topics: { 'YYYY-MM-DD': { topic, desc, join, off } } }`. `r50-q` (new, member writes): questions in advance `{ 'r50-YYYY-MM-DD': [{ q, by, at }] }`, list every member's in the coach room. RSVPs share `gidl-rsvp` (ids `r50-…`).
- **6 Nov 2026** · `ad-creatives` (new, Resvita team only, Wheeli deck): `{ items: { adId: { st: idea|ok|live|pause|gone, img, votes: { coachName: 1|-1 }, notes: [{ by, t, at }], res: [{ wk, spend, impr, clicks, leads }] } }, added: [{ id, n, angle, h, v, p }] }`. Share it across the team; later pull `res` from the Meta Marketing API by ad id.
- **6 Nov 2026** · `ai-tools` (new, coach writes): `{ clients: { clientId: { use: [toolId], note } }, extra: [{ id, n, what, where }] }`. `extra` is Resvita-wide (tools added for every client); `clients` is per member. Later: connect each tool's account (OAuth / API key, the client's own) so Get it done and the Asset studio can use it.
- **6 Nov 2026** · `booking` (new, Resvita-wide, coach writes): `{ coachName: { role: mindset|strategy|support, url } }`, over hub.json › booking. `ai-tools` › `clients[id].connect` (new): `{ toolId: { at, st: 'requested', by } }`: each is a connection to set up (MCP server, OAuth sign-in, or the client's API key, stored encrypted per member).
- **6 Nov 2026** · `jobs` (new, member writes; every member deck since Josh's sign-off): `{ example, jobs: [{ id, name, addr, client, lead, start, due, contract, vars: [{ t, amt, at, signed }], parts: [{ n, budget, spent, ctc }], docs: { quote, scope, boq, before }, notes: [{ by, at, t, photos: [jpeg data URLs] }], sign: { index: true } }] }`. Move photos and documents to file storage; let team seats add site notes from their phones; later import jobs and costs from simPRO / ServiceM8 / AroFlo.
- **6 Nov 2026** · `access` (new, Resvita admins write): `{ people: [{ id, n, email, role: admin|head|coach|support, coach: mindset|strategy|'' }], incl: { start, grow, build, partner }, seatPrice, clients: { clientId: [{ id, n, job, email, areas: [], owner, coach }] }, oneSession, newDevice }`. This is the sign-in and permissions model: create accounts from `people` and each client's seats, enforce roles and areas server-side, bill seats above `incl + 2`.
- **6 Nov 2026** · `getpaid` (new, member writes; every member deck): `{ example, sel, inv: [{ id, no, client, first, phone, job, amt, issued, due, steps: { stepIndex: dateDone }, plan, paid }], sup: [{ id, n, what, spend, terms, disc, rep, asks: [], won, saved }], prevent: { index: true } }`. Later: pull unpaid invoices from Xero (Aged Receivables) and send the reminders by email / SMS through Flow on the member's say-so.
- **6 Nov 2026** · `getpaid` › `sendQ` (new): `[{ inv, step, text, at }]`, Send via Flow requests. At go-live: send each through the member's Flow (GoHighLevel) by email / SMS to the invoice's client, then set `inv.steps[step]` to the send date. Only ever on the member's tap.
- **6 Nov 2026** · `referrals` (member writes; was missing from this list): `[{ id, at, st: 'sent', name, biz, contact, prog: start|grow|build|partner, reward: pay|discount, note }]` from Refer a trade owner. The team gets a message now; at go-live list them in the coach room, track sent → talking → joined → paid (paid 60 days after they join: 50% of their Build Your Blueprint fee, or passed on as their discount).
- **6 Nov 2026** · `wt-20`, `wt-phone` (new, every member deck since the welcome tour's sign-off): the welcome tour's two self-ticked first tasks (started the 20 minutes, added Wheeli to the phone). Per member, no backend logic needed beyond saving.
- **6 Nov 2026** · `grow` › `evLabel` (new): `{ eventId: { n, when, date } }`, what was booked in words. List every member's `grow.ev` bookings in the coach room (Event bookings) and stop Synergy Lab bookings at 25 per state.
- **6 Nov 2026** · `team-tasks` (new, Resvita team only): `{ items: [{ id, t, owner, due, pri, client, st: todo|doing|done, notes, idea, at, doneAt, by }] }`. Share across the team; later remind owners of overdue tasks.
- **6 Nov 2026** · `r50` › `recs` (new): `[{ date, title, url, stamps }]`, the Resvita 50 recordings and timestamps (coach writes, members read).
- **6 Nov 2026** · `ratings` (new, member writes, coach reads and replies): `[{ id, kind: call|gidl|r50, title, coach, at, stars, good, better, rated, reply, replied }]`. Gather every member's ratings in the coach room; report averages per coach monthly.
- **6 Nov 2026** · `drops` (new, Resvita-wide, coach writes): `[{ id, kind: loom|social|book|product|referral|tip, title, text, url, at }]`; `drops-seen` (member): ids already shown. Send each drop to every member once.
- **6 Nov 2026** · `coaching-content` sessions gain `prep: { notes, prompts: [], res: [{ name, url }] }` (coach only): never send `prep` to members' devices.
- **6 Nov 2026** · `focus-course` (new, member or coach writes): `{ id, by }`, the course pinned to the top of My Dashboard. The coach's pick should reach the member's Wheeli.
- **6 Nov 2026** · `win90` (new, member writes, coach reads): `{ t, unit, base, target, now, start, end, by, log: [{ at, v }], hit }`. `grad-last` (member): the programme last celebrated.
- **6 Nov 2026** · `dash-req` (new, member writes, coach updates `st` and `reply`): `[{ id, kind: new|change|help, what, why, at, st: new|doing|done, reply }]`.
- **6 Nov 2026** · `cabinet` (new, member writes, coach reads): `[{ id, at, type, short, title, score, file, q, summary, wins, fixes, html }]`. Store the uploaded file with it once files are hosted.
- **6 Nov 2026** · `<storeKey>-coins` (new, member writes): `{ spent, claims: [{ id, n, cost, at }], seen }`. Claims need fulfilling (merch, sessions, seats); keep coin balances server-side so they can't be edited in the browser.
- **6 Nov 2026** · `access` › people gain `see: { area: bool }` (per-person visibility over the role default). Enforce server-side.
- **6 Nov 2026** · `r50` › `recs[].st` (new): `[{ t, l, who }]` (who = client id or '' for everyone); `r50-sends` (new): `[{ client, text, at }]`, timestamps to deliver to each client's Wheeli as a coach message.
- **6 Nov 2026** · `net-reviews` (new, member writes): `{ listingId: { stars, text, at } }`. Average every member's ratings per Trusted Network listing and show the average and count to members.
- **6 Nov 2026** · `stories` (new, member writes, team reads): `[{ id, kind: fb|greview|testi|podcast, text, mood, file, at, seen }]`. Store the testimonial video file; verify Google reviews before rewarding if needed.
- **6 Nov 2026** · Opportunities reads every client's Rocket fuel lists (`<brand>-rocket` items, New services, M&A list): serve them to the Wheeli admin Coach view from each member's live data instead of clients.py.
- **6 Nov 2026** · `rate-cats` (new, coach writes, member reads): `{ clientId: [category] }`, which ready-made Pricing rate groups each client sees. Deliver each client's list to their Wheeli (as `live`).
- **6 Nov 2026** · `opp-nudges` (new, coach writes): `[{ key, a, b, text, by, at }]`, intros sent from Opportunities › Who knows who. Deliver `text` to both clients (a and b are client keys, 'live' = this deck's member) as a coach message, with {name} as each first name.
- **6 Nov 2026** · `opp-shop` (new, coach only): `{ day1, n, d }`, the team's Canton Fair shopping-list day plan. Share across the coaching team.
- **6 Nov 2026** · `team-scorecard` (new, member): `{ show: { rev, np, cash, jobs, win, q99, bp, miles, wins, pri, who, team }, word }`, what the member shares in their team scorecard. Per member; later, team seats (B10) can open it read-only.
- **6 Nov 2026** · `search` (new, member): `{ recent: [text], counts: { text: n }, miss: { text: n } }` (miss = found nothing), their searches. Later: add up counts across members so Popular reflects everyone, and show the team what members search for and don't find (B15 suggestions).
- **6 Nov 2026** · `midmonth` (new, coach): `{ clientId: { 'YYYY-MM': { at, by } } }`, mid-month calls done. `coach-rooms` (new): `{ coachName: meetingUrl }`. `coach-outbox` (new): `[{ to: clientId, text, by, at }]`, coach messages to clients other than this deck's member: deliver to that client's thread. Next sessions should come from each coach's calendar (Calendly / Google / GHL) instead of the example times.
- **6 Nov 2026** · `week` (changed): adds `labels: [[key, name, colour]]`, `who`, and `team: { personName: { ideal, actual, idealSet } }` (each team member's weeks). With team seats (B10), a team member's own Your week should read and write their entry. Calendar sync should write the ideal week to their calendar instead of the .ics download.
- **6 Nov 2026** · `brand-edits` (new, coach): `{ clientId: { logo (data URL), accent, card, at, by } }`. Once live, save it to the client's settings so their Wheeli loads it (logo, colours, favicon) without a rebuild.
- **6 Nov 2026** · `collab` (new, member): `{ mine: [{ id, kind: lead|client|subbie|supplier|project, title, text, where, val, vis: all|conns|pick, to: [memberId], at, ins: [memberId] }], in: { postId: at } }`. Share each post with everyone, the poster's connections, or only `to`; record who taps I'm in on the poster's post (`ins`) and message them.
- **6 Nov 2026** · `access` › `clients.live` (member writes, coach approves): the member's own team seat requests from Build the role (`owner: true`, `coach: false` until the coach agrees). Sync to that client's record so the coach sees it; once both agree, create the team member's sign-in limited to `areas`.
- **6 Nov 2026** · `milestones` (new, member writes): `[{ id, k: level|badge|celebrate, t, at }]`, and `milestones-ack` (coach): `{ id: { at, by } }`. Share with the member's coaches; a push or email to the coach for big ones (90-day win, programme move) would help.
- **6 Nov 2026** · `wheeli-lines` (new, coach writes, every member reads): `{ jokes: [{ t, by, at }], rhymes: [...], topical: [{ t, until, by, at }], skip: [text] }`. Resvita-wide: deliver to every deck. Later: Claude drafts the weekly five from the season and the news, still approved by the team.
- **6 Nov 2026** · `coach-chars` (new, coach writes, every member reads): `{ heidi: { words, lines: [] }, … }`, each person's personality words and lines for their pop-ups. Resvita-wide. `<home>-team-pop` (member): which coach pop-ups they've seen.
- **5 Nov 2026** · `flow-done` (new): `{ quoteKey: at }`, quotes the member marked ✓ Followed up on Flow's page (key `q-<quote's saved at>`). Later this should come from the CRM (GoHighLevel) pipeline instead.
- **5 Nov 2026** · `ads` months are now per platform: `'YYYY-MM'` = Google Ads, `'YYYY-MM-meta'` = Meta, and Meta months also hold `reach`, `impressions`, `cpm`, `frequency` (leads go in `enq`). `ads-plat` remembers which platform the member last reviewed (browser only).
- **5 Nov 2026** · `ads` (new): `{ months: { 'YYYY-MM': { platform, shown, clicks, enq, spend, real, quoted, won, avg, margin, fee, ok, watch, ask, score, file, at } } }`. Later: read the figures straight from the uploaded report or a Google Ads / Meta connection. Also `gid-tab` (which Get it done tab was open; a convenience, can stay in the browser).
- **5 Nov 2026** · `teach` (new): `[{ id, q, a, by, at, st: 'new'|'approved'|'no', okBy, okAt }]`. Coaches add from the phone Coach view; approved in Wheeli feedback; Ask Wheeli answers approved ones. Must be Resvita-wide (every member's Wheeli reads it), and the backend's search should replace the word matching. Feeds the Method Library review.
- **5 Nov 2026** · Phone app (Josh's mock-up): `messages` entries can now carry `kind` ('quick'|'decision'|'stuck'|'win') and `ctx` (the member's numbers as text). New: `coach-hours` `{ strategy|mindset|team: { times: ['HH:MM'], days: [0-6], quiet: 'HH:MM' } }` (coach writes, members read: must sync both ways), `session-agenda` `[{ id, role, kind, text, at, used }]` (member writes, coach reads), `comms-sent` `{ subject: at }`. The phone's Messages tab needs the real customer inbox (email, SMS, Facebook, reviews, web forms) and sending, plus push notifications that wait for the coach's next round during quiet hours.
- **4 Nov 2026** · `intros` (new): `[{ id, src: 'audit'|'network', key, name, partner, note, at, st: 'new'|'introduced'|'done'|'not-needed', by: 'coach'|'member', upd }]`, newest first, one open request per area. Written by the member (asking, closing) and the coach (partner, note, status), so it needs to sync both ways. The Business audit's `asked` areas now read their status from it. No new store for the Blueprint complete bar (it reads `home-byb`, `week1-done`, `bpforms`, `foundation`, `audit`).
- **4 Nov 2026** · `bigprojects` simplified: `{ projectId: { tasks: [{ t, due, done }], started, done }, _skip }` (no outcome or named sub-projects; older plans are flattened on read). Tasks ids `big-<projectId>-<n>`. Content `{ levels: [{ lvl, name, big: [{ id, title, tasks }] }] }`.
- **4 Nov 2026** · `audit` `{ areaId: { st: 'asked'|'done'|'skip', who, at } }` (Introduce me also sends a message to the Strategy coach) and `vision` `{ 'weekly:YYYY-MM-DD' | 'monthly:YYYY-MM' | 'quarterly:YYYY-Qn': { itemId: time } }`. Content in `source/journey.json`. The 30-day path (`byb-tasks.json`) lost its 4 form cards, so saved `home-byb` ticks on `foundation`, `member-care`, `big12-form`, `big-form` no longer count.
- **4 Nov 2026** · `bigprojects` and `bigprojects-content`: B.I.G Projects. Plan `{ bigId: { outcome, due, projects: [{ t, done, tasks: [{ t, due, done }] }], started, done }, _skip: { start|grow|build|partner: true } }`. Put it on my 10 Miles also writes `tenmiles` (goal, miles) and `tasks-inbox` (ids `big-<id>-<project>-<task>`). Content `{ days, levels }` as in `source/big-projects.json`.
- **4 Nov 2026** · `bpforms` and `bpforms-content`: Blueprint forms. Answers `{ formId: { a: { questionId: answer (text, pick, date, or [file names]) }, sec, sent, sentBefore, snap: {form}, started } }`; their coaches read them on the client card, and they should become part of the member's context pack. Content `{ forms }` as in `source/blueprint-forms.json`. A coaching session may carry `bpform` (the form it opens).
- **4 Nov 2026** · `coaching` and `coaching-content`: coaching sessions. Progress `{ sessionId: { f: { questionId: answer }, t: [ticked sub-task numbers], up: [file names], done: { at, name, by: 'member'|'coach' }, open: true, snap: {session}, snapForm: {form}, started } }`. The coach's pre-session view reads the member's `f`, so the backend should let that member's coaches read it. Content `{ forms, tracks }` as in `source/coaching.json`. Approving a session's sub-tasks into Tasks writes `tasks-inbox` (ids `coach-<session id>-<n>`). Form file answers and uploads are names only until file storage exists.
- **4 Nov 2026** · Lessons: new fields on courses (`about`, `parent`, `step`, `banner`, `shade`, `cards`) and lessons (`section`, `len`, `free`, `tasks` as a list, `upload`). Old courses retired from `lessons-custom` on load (see `retire()` in `lesson-player.html`). No new store.
- **4 Nov 2026** · `report-coach`: the coach's monthly report boxes `{ clientId: { 'YYYY-MM': { from, next[3], by, at } } }`.
- **4 Nov 2026** · `coach-calls` and `context`: Calls & context on the client card. Calls `{ clientId: [ { id, at, type, mins, rec, transcript, summary, actions[{ t, due, done }], facts[{ k, t, use }], shareSum, shareTr, status, by } ] }`; context `{ clientId: [ { id, k, t, src, at, call } ] }`. Approving also writes to `tasks-inbox`, `hub-calls` / `hub-callnotes` and (for coach-only facts) `coach-notes`.
- **6 Nov 2026** · `coach-journey`: the 🧭 Client journey checklist on each client card `{ clientId: { 'stage:step': { at, by } } }` (7 stages, 43 steps; ⚡ steps aren't saved, they're worked out from the member's own stores). Coach-side, shared by every coach who sees that client.
- **6 Nov 2026** · `beta-feedback` (phone app beta only, `mobile-beta/`): `[ { at, kind, t, where, dev, v } ]` on that phone. At go-live: send to Wheeli improvements as bugs and ideas.
- **6 Nov 2026** · `access` › people gain `awayFrom`, `awayTo`, `cover` (H6: away mode; the cover coach gets their clients on Today and My clients, members see who's covering). Resvita-wide.
- **6 Nov 2026** · `programme` gains `demo` (H16: false = hide example data for a real member). Per member.
- **6 Nov 2026** · `improve` can now be written by members (H19, ? Help › Report a problem: `{ type: bug|idea, from: 'Member', d: what happened + page + screen size + screenshot name }`); at go-live these must reach the shared Resvita board, not stay on the member's device. The report also messages the team through `messages`.
- **6 Nov 2026** · `coach-journey`: stage 6 keys now end in the month (`rhythm:<step>:YYYY-MM`, H24) and a new optional stage `leave:<step>` (H22). ⬇ Export their data (H22) downloads every `<brand>-` store of the member (not coach-only stores) as JSON; at go-live the backend should produce this export for any member.
- **6 Nov 2026** · sessionStorage `wheeli-pop` (H17): which pop-up already showed this visit (one per visit). Not saved data.
- **7 Nov 2026** · new store `results` (K2, the results ledger): `{ [clientId]: { start: { rev, gm, cph, dtp, hrs, at, by }, months: { 'YYYY-MM': { rev, gm, cph, dtp, hrs, st: { <field>: 'v' | 'w' | 's' }, at, by } }, share: 'no' | 'anon' | 'name' } }`. Written by coaches (client card › 📈 Results ledger), read by the member (The Numbers › Your results, under the key `live` today) and by Resvita (Coach view › Everyone › 🏆 Results ledger). At go-live: one record per member, written only by their coaches; `start` can't change once locked without the head coach; only `share` ≠ `no` and `st` = `v` numbers may leave Resvita (ads, landing page). Resvita-wide.
- **7 Nov 2026** · Pricing › 🖼 Project mock-up: `pricing` gains `mock: { mode: 'one'|'pop', desc, style: [...], cur }` and `pop.mock: [resId ×3]`, `pop.mockOn`. Pictures live in a new store `pricing-mock` `{ up: [{ kind: photo|plan|example, name, src (JPEG data URL ≤1000 px) | pdf: true }], res: [{ id, at, src, ex, prompt, tier, label, onQuote }] }`, per member, on the device today (localStorage, so a few MB at most). At go-live: (1) move pictures to file storage, keyed to the job; (2) connect an image AI so ✨ Make my mock-up sends `prompt` + the uploads and returns the picture (`ex: false`); PDF plans go to it too. Until then ✨ makes a clearly marked EXAMPLE and members can ⬆ upload a picture made elsewhere. Per member.
- **7 Nov 2026** · two new coach-only stores (per coach, keyed by the name they log in with): `coach-tab-order` `{ [coach]: { [tab row label, e.g. "Platform", "Inbox", "My clients"]: [tab keys in order] } }` (Coach view tabs dragged into a new order) and `coach-mineview` `{ [coach]: 'sess' | 'table' | 'board' | 'score' }` (My clients › All my clients view). Preferences only; sync per coach so they follow them across devices.
- **7 Nov 2026** · G30, Resvita's real checklists switched on: answers still live in `byb-sheet` › `check`, now keyed by the real check ids (`p<i>-<j>` Big 12, `g…` Core 9, `s…` 90 Degrees, `f…` 180 Power Frame; values `y` for yes / no lists, `n` / `p` / `s` for rated lists), beside any old 99-point answers (`<area>-<i>`, kept as history). New `byb-sheet` › `start` `{ key, area, by, at }`: where the coach confirmed the member starts (written from Coach view for this deck's member). New coach store `cl-start` `{ clientId: { key, area, by, at } }` for other clients until their deck syncs: the backend should write it into that member's `byb-sheet.start`. Platform content edits for checks stay in the `c99` content kind, now keyed by check id; added checks carry `aid` (the area id).
- **7 Nov 2026** · 🙋 Ask for help: new member store `help-asks` `[{ id, at, choice: unclear|content|session, title, ref: { lesson, area, course }, text, files: [names], st: new|made, madeAt, made }]` (newest 300). Each ask is also a coach message (`messages`, `kind: 'help'`, with `files` and `help: { choice, title, ref }`), and "session" asks go on `session-agenda` (`kind: 'help'`). Coaches read all members' `help-asks` together in Suggestions › Content requests (the backend should pool them across members, names kept from Kristina). Ask Wheeli records (`wheeli-feedback`) gain `files: [names]`; attachments themselves follow the same storage as Ask my coach's.
- **7 Nov 2026** · 📝 1:1 session plans: new store `session-plans` `[{ id, client ('live' = this deck's member, else the client id), coach, track: strategy|mindset, at, next, topic, title, result, actions: [{ t, who, due, done, doneAt }], agreed, bring, attach: [{ k: lesson|tool|file, id, label, sub, url, data }], notes (coach only, never sent to the member), transcript, extra, checks, st: team|coach|sent, draftSnap, sentAt, by }]`. Written by coaches (client card), the Resvita team (Inbox › Session plans) and the member (ticks). The backend should hold it per client, deliver `st: 'sent'` plans to that member's deck (without `notes`, `transcript`, `checks`, `draftSnap`), take the transcript straight from the meeting tool, and send the member's ticks back to the coach. Approving also writes the actions to `tasks-inbox` (`sp-<plan>-<n>`) and a coach message.
