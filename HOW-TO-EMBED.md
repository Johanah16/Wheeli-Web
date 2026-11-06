# Embedding the Resvita AI Brain

## The two decks (start here for sales calls)

| File | Tabs |
|---|---|
| `Wheeli-Deck.html` | The same layout and features as Lance's deck, with Wheeli branding and example content for any trade business. Opens on Home (the AI brain + 20-20 timer + level bar; click the Wheeli logo to return) · 1 Your 10 Miles · 2 Get it done · 3 Asset studio · 4 The Numbers · 5 Live tools (with Communication and Tasks & projects) · 6 Rocket fuel · 7 Community · 8 Blueprint (named by programme, e.g. $700K Blueprint) |
| `Murphys-Construction-Deck.html` | Opens on Home (Lance's AI brain + 20-20 timer; click his logo to return) · 1 Your 10 Miles · 2 Get it done · 3 Asset studio (click any asset for its layer below) · 4 The Numbers (Project 271 & 15, then the 3 Major Growth Pipelines) · 5 Live tools (incl. Communication and Tasks & projects) · 6 Rocket fuel (China sourcing list) · 7 Community · 8 Blueprint |

Each deck is one self-contained file. Open it in Chrome, then click the tabs or use the keys:
- **→ / Space** next page, **←** previous page, **1–8** jump to a tab (only the tabs in the member's programme), **0** Home, **F** full screen (the tab bar hides).
- Each page's animation starts from the beginning when you open it. Click the open tab again to replay it.
- Adding `#3` to the address opens straight on page 3.

**ROI dashboard:** every orange cell can be typed in during a call, and all figures, charts and the progress gauges update instantly. Project 271 = leads × average proposal value × conversion × times. Project 15 = revenue lifted in three steps with costs held flat. Change the example numbers in `source/build_roi.py`, then run `python3 -I source/build_roi.py`.

**Live tools:** Bailey (Databox), the BYB sheet (Google Sheets) and Miro show live inside the deck once a link is added. Flow (GoHighLevel) opens in a new tab, because it blocks being shown inside other pages. The Circle community and the LaunchBay install portal have their own tabs now (Community and Blueprint), so they're no longer in Live tools.
- Links pasted on the page are saved in that browser only.
- To build a deck with the links already in place (e.g. Lance's own sheet and board), add them to `LINKS` in `source/build_tools.py`, then run `python3 -I source/build_tools.py` and `python3 -I source/build_deck.py`.
- Use embed-friendly links: the Databox **public share** link, the Google Sheets **Publish to web** link (read-only), and any Miro **board** link (converted automatically).

**Home:** a welcome message, the journey tracker, a card for every page and tool (click to jump straight there), and the 20-20 Vision timer. The 20-minute timer chimes at zero and ticks off the day. Event days are counted with + and −. Both are saved in that browser only. Change the welcome text, journey or card text in `source/build_home.py`, then run it and `build_deck.py`.

**Awards (XP and levels):** both decks reward the habits that grow the business. Every page reports to one score, saved in that browser only.
- XP for: starting today's 20 (+10), finishing the full 20 minutes (+10), a 5-day week (+50), a live event day (+100), keeping an asset (+20), a Review & Improve (+20), a task done (+5, or +15 if urgent and important), finishing What do I work on? (+50, once a day), and the Project 271 / Project 15 "We hit it" buttons on The Numbers (+150 to +500, self-reported).
- Daily caps stop farming: 5 assets, 5 reviews and 12 tasks a day count. Each day, task and stage only counts once.
- Levels 1–10. Unlocks: level 3 Early access, level 5 Community spotlight, level 7 Free 1:1 session, level 10 Event perks.
- A pop-up shows each award. On Home, the level bar above the timer opens the awards pop-up: level path, unlocks, 20 badges, how to earn XP and recent activity.
- Get it done has three modes in both decks: **What do I work on?** (Symptoms Survey → 9 moves → 80/20 top 3 → the one thing → uplift, then "Let's get it done" carries the one thing into Get it done), **Get it done**, and **Review & Improve** (sales call, social, brochure, CV, financials, each with an optional question). Edit the example in `source/focus_content.py` and the review examples in `source/review_content.py`.
- The Numbers (both decks): a **How I'll improve this** box under Project 271, Project 15 and each of the 3 buckets, with idea chips and **⚡ Work on it in Get it done**, which opens an improve plan in Get it done. The sales pipeline, invoice schedule and cashflow each have **🔍 Scan for opportunities**, which reads the figures on the page and lists opportunities, improvements and risks. Edit the boxes in `source/improve_content.py` and the scan rules in `source/scan-panel.html`.
- Rocket fuel (both decks): **⬇ Download shopping list (PDF)** makes an A4 Canton Fair checklist (cover page, then one page per category with tick boxes and fill-in lines). Under it, **Mergers & Acquisitions** lists companies with website, merger or acquisition, comments, files, a 6-factor opportunity score and Send to coach. Code in `source/rocket-extras.html`; example companies in `source/build_rocket.py`.
- Both decks: **Your week** in Live tools (ideal week, this week with demo calendar connect, Friday review with hours back × hourly rate and Action × Amount; code in `source/week-panel.html`, targets in `source/build_tools.py`). On Home, a **first-visit coach video** (paste a Loom, YouTube or Vimeo link into `VIDEO` in `source/build_home.py`) and an **Updates & news** button (next to Welcome & Navigation) with tabs for Updates, Notifications (worked out from the member's tasks, miles, sign-offs and rewards) and Industry news (`NEWS` in the same file) (add items to `ALERTS` in the same file; each needs a new `id` so it shows as unread).
- Home (both decks) is now a path (`source/home-path.html`): **Start here** (5 first-week steps), **Today** (one thing, 3 actions from Your week, tasks from plans), live tools shown only once connected, resources behind **More**, and a **Friday nudge** (demo; sends through Flow once connected). Improve plans and Review & Improve fixes add tasks automatically; Friday review XP is 20 + half the score. `murphys-home-demo.html` is the stand-alone demo with stage buttons.
- Both decks have a **phone view** (screens under 600px wide): Today, Tasks, Ask, Week, More, on the same data as desktop. Built by `source/build_mobile.py` from `source/mobile-app.html`; `murphys-mobile-demo.html` is the stand-alone demo.
- **Live event resources** (Live tools, both decks): a card per event, with the Handle It masterclasses as tabs in one card. Each event has a handout to download and a place to upload the completed copy, which is kept in that browser, added to the AI brain (demo) and copied to My assets. Handouts live in `resources/` next to the decks: **upload that folder with the decks when hosting**. Add a handout or links in `EVENTS` in `source/build_tools.py`.
- **Your Blueprint** (Home, both decks): a card with a mini map opens the full Resvita structure: 81 parts in the 9 Squared Grid, 10 levels of 90 Degrees of Scale and 5 parts of the 180 Power Frame. Coaches sign parts off in Coach mode: **demo PIN `2020`**, change `BP_PIN` in `source/build_home.py`. Part names are placeholders: add real ones to `names` in the same file (ids `g<block>-<part>` from 0, `s<level>`, `f<part>`). Example progress is in `BP_SEED`. Progress is saved in that browser only until there's a shared backend. The blueprint now has three sheets (tabs): **Resvita structure** (with the **12 Pillars** laid over the grid, ids `p0`–`p11`), **Bricks and Blocks** (3 elevations from the boot camp handout, ids `k<elevation>-<part>`) and **B.I.G Framework** (centre + 8 parts + Be Courageous / Present / Empathetic, ids `b0`–`b8`, `v0`–`v2`; placeholder names).
- **Your 10 Miles** (tab 7, both decks): a 90-day road in 10 miles (about 9 days each). Members set a 90-day destination, tick suggestions to add moves (from their one thing and top 3, Improve plans, Review & Improve fixes, pipeline scans, the next blueprint parts, and coach-pinned moves), drag miles to swap them and tick each one done (+40 XP; +200 for all 10). Key resources show the PPCP workbook and example, their uploaded PPCP and the boot camp handouts. Coaches pin moves with the blueprint PIN. Built by `source/build_tenmiles.py`.
- **Monthly measurements** (bottom of Your 10 Miles): Life Blueprint (9 areas /10, centre = average), Goals & Rewards (rewards list, dreams → goals, claim the reward when a goal is hit) and Life ROI (time, money, energy, profit, conversion, revenue, team, lifestyle vs the first banked month). **Bank this month** saves a snapshot (+50 XP). Example data is `MONTHLY_SEED` in `source/build_tenmiles.py`; code in `source/monthly-panel.html`.
- **Canton Fair plan** (Rocket fuel, both decks): per item area, hall · booth, day, order m³, AU/NZ standards, proforma collected and price, and next steps; a simplified map of Areas A–D, a 3-day itinerary (Auto-plan keeps areas together) and a container estimate. All of it prints in the shopping list PDF (new fair-plan page and bigger item boxes). Example plan is `PLAN` in `source/build_rocket.py`.
- **The Boardroom**: Home shows a countdown to the next Boardroom (set `NEXT_BOARDROOM` in `source/build_home.py`, or it uses the first Thursday of next month; members can change it and add it to their calendar). In Live tools › Live event resources, the Synergy Lab and The Boardroom cards each have My #1 constraint, a presentation upload (kept in the browser and copied to My assets) and a two-part ring timer, blue for presenting and amber for the same time with the board, with chimes and full screen: **Synergy Lab 14 minutes (7 + 7), The Boardroom 60 minutes (30 + 30)**. Change the lengths in `DAY` in `source/events-panel.html`.
- **Our 2027 Mission** (top of The Numbers, both decks): group progress to $50M revenue (Project 271) and $5M profit (Project 15), set monthly in `MISSION` in `source/build_numbers.py` (example figures now). "Your contribution" is the member's growth since their first banked month in Your 10 Miles, as a yearly figure. Coach view (PIN) lists members and a leaderboard (`COACH_MEMBERS`; edits are saved on that device).
- **Welcome & Navigation video** (both decks): a 3½-minute captioned screen tour, `videos/murphys-welcome-tour.mp4` and `videos/wheeli-welcome-tour.mp4` (about 64 MB each). Upload the `videos` folder next to the decks. To use a Loom or YouTube version instead, put its link in `VIDEO › url` in `source/build_home.py`.
- **Monthly report** (every deck, rebuilt 4 Nov 2026): a 4-page A4 board report for the month, opened from Updates & news, the Coach view and the phone's More tab, with a month picker; 🖨 Save as PDF / Print gives the 4 pages. 1 · Snapshot: a one-line verdict, 8 key numbers (revenue vs budget, net profit, cash buffer, profit an hour, 99-point check, Blueprint, 10 Miles, life score), a traffic-light scorecard and From your coach. 2 · The Numbers: budget vs actual for the month and year to date, accounts to look at, income by month, cash, pipeline and jobs, cost per billable hour and what Project 15 adds. 3 · Progress & coaching: 10 Miles, Blueprint parts signed off, the 99-point check by area, this month's calls with what was agreed and whether it's done, tasks, 20s and Friday reviews. 4 · People, life & next month: the team, Life ROI, wins from the community, next month's 3 priorities and what's coming up. Every number comes from what the member keeps in Wheeli; anything not filled in yet says where to add it. Coaches write From your coach and Next month's 3 priorities in Coach view › client card › 📄 Monthly report (✨ drafts both from that month's calls).
- **New members start on Focused**: Today opens on 🎯 Focused for a member's first 7 days (desktop and phone), then Everything, unless they've picked for themselves. Members who used the deck before this change aren't affected.
- **What's new** posts are the first two items in `ALERTS` in `source/build_home.py`.
- **Phone view Today** (both decks): Wheeli's check-in at the start of each phone session (Not great → coach heads-up task), the latest shared coach note (all of them under More; they count on the bell), Your priorities (the two top quadrants, ⇄ to move across), the Boardroom countdown, Blueprint progress, and 🎯 Focused / Everything / ⚙ (Focused keeps coach notes, one thing, the 20 and priorities). Same saved data as desktop. In `source/mobile-app.html`.
- **Focused / Everything / ⚙ on every page** (both decks; small control bottom-left, top-right on Live tools): 🎯 Focused hides the extras, Everything shows all, ⚙ picks part by part, remembered per page in that browser. Focused hides: 10 Miles › Spotlight, Key resources, Monthly measurements · The Numbers › Our 2027 Mission · Live tools › every tool except Your week, Communication, Tasks & projects, Flow and Bailey (and any not linked yet) · Rocket fuel › Canton Fair plan, M&A. Get it done and Asset studio have none. Change the parts and Focused sets in `VIEWS` in `source/build_deck.py`.
- **Today, focused or everything** (Home, both decks): 🎯 Focused shows just My one thing and Your priorities; Everything shows all of Today; ⚙ picks each part (My one thing, Today's 3 actions, From your plans, Last Friday review, Your priorities). The choice is remembered in that browser. Your portal, Live tools and Resources lower down each have their own show / hide button.
- **Your priorities** (Home › Today, both decks): Urgent & important and Important, not urgent side by side, from the same saved tasks as Live tools › Tasks & projects. Tick a task done, tap its status to change it, drag it (or tap ⇄) to the other column, or add one; the board in Live tools shows the same. Each column scrolls when full. In `source/home-tasks.html`.
- **Communication and Tasks & projects** (tools inside Live tools, both decks; the separate Comms & Tasks tab is gone, and old links to it open Live tools › Tasks & projects). Task quadrants have a fixed height and each scrolls on its own. Built into Live tools by `source/build_tools.py` from `<brand>-comms.html` and `<brand>-tasks.html`.
- **Communication stats** (one compact strip at the top of the Communication tool, both decks): email open, click and reply rates, response time, Google rating, unsubscribes and NPS (promoters / passives / detractors) for 30 or 90 days. Example figures in `STATS` in `source/build_comms_tasks.py` until Flow and Google reviews are connected.
- **Josh pop-ups** (both decks, over every tab): "Handle it, my boy!" on level-ups and badges, "Chur bro, where you been?" after 3+ days away, "Come on…" when the 20, the Friday review or a mile is overdue, and Josh arriving in the van ("Get in!") when the 20-minute timer starts and finishes. Wording in `source/mascot-panel.html`; image `source/josh-mascot.jpg`.
- **Wheeli talks** (Home, both decks): tap the Wheeli mascot. It pops up with "How's it going?" the first time Home opens in each new session (new tab or visit), and with a joke or quote (alternating) every time they come back to Home after that; those close themselves after 15 seconds. "Not great" offers to tell the coach (adds a coach task with their note). It also tells corny jokes, quotes, original rhymes, the question of the day and where to go next, and makes a fuss on birthdays and business anniversaries. All lines are in `source/wheeli-chat.html`.
- **Your 20 soundtrack** (timer card on Home, both decks): a Spotify player with quick picks (Deep Focus, Beast Mode, lofi beats, All Out 2000s, Peaceful Piano) or any pasted Spotify link. "Play with my 20" starts and pauses it with the timer. Needs the deck to be hosted (Spotify won't load from a file opened on the computer); full songs need the member logged in to Spotify, otherwise it plays 30-second previews.
- **New business** (bottom of Rocket fuel, both decks): new services, products and ideal clients in one table (filter by type), with who it's for and the problem it solves, price / cost / margin, revenue a year, a 4-factor score (fit, demand, margin, ease), stage, and next step / owner / date. Actions: Build it (Get it done), Add to 10 Miles, Send to coach. Examples in `NB_LANCE` / `NB_GENERIC` in `source/build_rocket.py`.
- **Blueprint lessons in Circle** (Your Blueprint, both decks): tap any part and "▶ Watch the lesson" opens its Circle lesson in a new tab; parts with their own lesson show a small ▶ on the sheet. Add links in `BP_LESSONS` in `source/build_home.py` by part id (`g0-0`…`g8-8` core blocks by block then part, `s0`–`s9` scale, `f0`–`f4` power frame, `p0`–`p11` pillars, `k0-0`…`k2-4` bricks, `b0`–`b8` and `v0`–`v2` B.I.G). `BP_COURSES` sets a whole section's course for parts without their own lesson (for now every section opens the Circle community platform). Coaches can also paste a link per part in coach mode (saved on that device only).
- **Coach view** (🧑‍🏫 Coach button in the header, both decks, coach PIN 2020; see **Added 2 November 2026** below for the dashboard, programmes and coaches): a client list with a status dot (red needs you, amber worth a look, green on track). This deck's client shows live data from the browser: blueprint %, 10 Miles done, 20s this week, Friday review score, level, the last Wheeli check-ins, alerts, numbers and plans. Dated coach notes tagged Strategy, Mindset, Progress or Action; tick "Share with…" and the note appears in the client's Updates › Notifications. Quick actions: sign off blueprint parts, pin a move to their 10 Miles, set their Spotlight, add a task. The other clients (Sarah, Dave, Priya) are examples in `COACH_EXAMPLES` in `source/build_deck.py`; real multi-client data needs the hosted backend, since notes are saved on the device they're written on.
- Change points, levels, unlocks or badges in `source/game.js`, then run every `build_*.py` (Home, Get it done, studios, tasks, ROI, numbers, tools, deck).

## Added 2 November 2026

**Programmes** (every deck and phone view): Start Right → Grow 1.0 → Build 2.0 → Partner 3.0. Each level is a bigger business and opens more of the deck, so smaller businesses stay on the work that matters. A member with no programme set sees everything.
- **Start Right:** Home · Your 10 Miles (90-day destination, the road, Monthly measurements with Life ROI) · Get it done (What do I work on?, Get it done, Review & Improve) · The Numbers (Our 2027 Mission, Project 271 & 15 calculators) · Live tools · Rocket fuel (New services, products and ideal clients) · Community · Blueprint.
- **Grow 1.0** adds: the full Your 10 Miles page · Assets · 3 Major Growth Pipelines · the high-impact sourcing list (with Think Global and the shopping-list downloads) · Canton Fair plan.
- **Build 2.0** adds Your M&A opportunity list. **Partner 3.0** has everything.
- **Live events by programme:** Start Right gets Synergy Lab, the One Day Intensive and Boot Camp; Grow 1.0 adds the Handle It Masterclass Series; Build 2.0 adds The Boardroom; Partner 3.0 all events.
- Hidden tabs disappear from the bar; a link to one shows a friendly "isn't in your programme yet" page. Hidden parts leave the page and its 🎯 Focused / ⚙ picker. On the phone, links to hidden parts don't show.
- The coach sets the programme, and adds or removes any part, in the Coach view (**⚙ Turn tabs and sections on or off**): every tab, Home's sections (Start here, Today, Blueprint card, journey, timer, Friday nudge, Boardroom countdown, AI brain, portal), each Live tool, each live event and the sections of 10 Miles, Get it done, The Numbers and Rocket fuel. **🌱 Start minimal** leaves just Home's welcome, Start here and Today, for onboarding or a member in overwhelm; tick parts back on as they're ready (a tab switched back on comes back whole). Levels per part are `PG_PARTS` in `source/build_deck.py`. When adding a new tool, decide which programme gets it.

**Coach view** (PIN 2020):
- **📊 Everyone** (Wheeli deck): opens first. Totals for needs you / keep an eye / on track, average blueprint, 20s this week, average Friday review and rewards waiting. Three views, remembered per coach by the name they sign in with: **☰ Table** (worst first), **▦ Board** (drag members between Needs you / Keep an eye / On track, or use the 🔴🟠🟢 buttons; a 📌 shows a coach moved them, ↺ puts them back), **🟩 Scorecard** (green / amber / red cells). Filter by status, programme or coach. Columns include Life (score and change) and Goals (achieved and rewards waiting); click a cell to jump to that part of the profile.
- **Profile:** the member's **🧠 Mindset coach** (Heidi or Nadja) and **🎯 Strategy coach** (Josh) at the top, changed with the dropdowns (list in `COACH_BASE['coaches']`). A **Programme** card with ⚙ Customise parts. A **💙 Life Blueprint** card (this month vs last, all 8 areas, the three to work on). A **🏆 Goals & Rewards** card (achieved, enjoyed, waiting) with **🎁 Nudge**, which shares a note asking them to claim it. **Open [name]'s deck ↗** opens another client's deck (same folder); for the live client, **Go to [name]'s deck ›**.
- **Client list:** drag cards to reorder (or Alt + ↑ / ↓; press and hold on a touch screen). **↻ Refresh** reloads everyone's figures, and refreshing the page keeps you in the Coach view in that browser tab.
- Everything the coach sets (programmes, coaches, board moves, order, nudges) is saved in that browser until the shared backend is live.

**Your 10 Miles › Monthly measurements:**
- **Life Blueprint:** a smaller **Last month** grid sits beside this month's. **🔄 Review this month** flashes until that month's review is done: it moves the scores across so the member can rescore, then shows ▲ / ▼ for what changed.
- **Goals & Rewards:** rate dreams and goals **$ to $$$$$** (Sort by $ on the dreams list; the rating carries from dream to goal). Once a goal is achieved and its reward claimed, it moves into **The Vault**: the treasure chest opens a pop-up of every goal and reward.

**Community tab:** the Resvita Circle feed (`COMMUNITY_URL` in `source/build_deck.py`) with an Open in a new tab button. Members only stay signed in inside the frame when the decks are hosted on a blueprinttobrilliance.com.au address.

**Blueprint tab and Home card:** the last tab is named by programme ($700K / $1.8M / $5.1M / $13.9M Blueprint) and opens the install portal (`INSTALL_URL`, resvita.wheeli.ai/client-login) in a new tab. LaunchBay can't be shown inside other pages. On Home, the Blueprint card lifts off the page with a gold border and a gold button to the same portal, and blueprint cubes in the nine Resvita blues drop from above it, stack 3 high on the section below, then tumble away and start again (`source/blueprint-panel.html`).

**Phone view:** the Blueprint card and More tab link to the install portal by programme name; More links to Community; Today shows a **🔄 Monthly review** reminder until it's done and a **🎁 You've earned it** card for unclaimed rewards (both can be switched off in ⚙).

**Referral programme PDF:** the Home page's "Referral programme" link opens `ResVita-Member-Referrals.pdf`, which must sit in the same folder as the deck. If you upload or send a deck, include that PDF next to it. The PDF is 18 MB, so it's kept out of the decks themselves.

## Added 3 November 2026: Ask Wheeli and live feedback (all decks)

- **Ask Wheeli** (blue button, top right of the header; on the phone, Ask tab › Ask Wheeli a Resvita method question). Answers come only from method files Josh has approved (Increasing Cashflow so far). If there's no method yet, Wheeli says so instead of guessing, and logs the question. Every programme has it; the coach can switch it off (Programme › Home › Ask Wheeli). Start Right members asking about Grow-level methods are pointed to the basics.
- **"Was this useful? 👍 👎"** on everything Wheeli makes: Ask Wheeli answers, Get it done drafts, Review & Improve, drafted replies in Communication and phone answers. A 👎 asks why in one tap (e.g. Not in my voice, Missing something) plus an optional note.
- **Coach view › ⭐ Wheeli feedback:** the weekly review. Each item shows what the member was working on: the tab they were on, their one thing, what they asked (or the message that came in), earlier questions in the chat, and what Wheeli made or said. Filter by what Wheeli made, mark each item Fix the method / Train Wheeli / Make a test question / Add to interview list / Done, and download a CSV. Kristina's how-to is in the IP folder: `00-Admin/wheeli-feedback-review.md`.
- Today ratings are saved in the member's browser (`<brand>-wheeli-feedback`). With the backend they become a `wheeli_feedback` table; see "Wheeli answer feedback" in the backend brief.
- Coach 🧑‍🏫 and Mobile 📱 in the header are now icons (hover for the name) so every tab still fits beside Ask Wheeli.

## Added 3 November 2026: the Foundation Form (all decks)

- The LaunchBay **Foundation Form** (31 questions) now lives in Wheeli, so answers don't need downloading and copying. Clients open it from the gold **📝 Your Foundation Form** banner on Home (above Start here) or the card on the phone's Today. It shows until they send it. Every programme has it; the coach can switch it off (Programme › Home › Foundation Form).
- **One question at a time.** On a laptop the "think about" prompts sit beside the answer and tick green as they're covered, with a list of every question on the left. On a phone the prompts are chips above the answer.
- **Talk or type.** 🎙 *Talk your answer* uses the browser's own speech-to-text (Chrome, Safari, Edge; not Firefox), in Australian English. **⏸ Pause** and **▶ Resume** any time (to think, or take a call), then **✓ Done talking**. No audio is kept.
- **Wheeli's draft stays on screen** under the answer, with what's still to cover. In the preview it tidies their words (numbers, %, brand names, capitals); once the backend is live, Wheeli writes it up properly with Claude. *Use this answer* swaps it in; *Keep my words* hides it.
- Saves as they go (`<brand>-foundation`). **Send to Resvita** on the last question marks it sent and downloads a Markdown copy for them to email their coach until the backend syncs it.
- **Coach view:** each client's profile has a 📝 Foundation Form card with progress, every answer, and *Open the form*.
- **Hosting:** if a deck is ever put inside another page's `<iframe>`, add `allow="microphone"` to the iframe or talk-to-type won't work. Microphone access also needs `https://` (or localhost).
- Uploads (P&L, balance sheet) only record the file names for now; the coach collects the files until the backend stores them.
- Question wording was copied from a screenshot of the LaunchBay form: check it against LaunchBay before going live (`Q` at the top of `source/foundation-form.html`).

## Added 3 November 2026: Build Your Blueprint, the first 30 days (all decks)

- Home's **Start here · your first week** is now **Build Your Blueprint · your first 30 days**: the 21 LaunchBay tasks in four stages (Get set up, Tell us about you, Know your numbers, Make it run), with progress and the day count.
- **One task per card, 5 at a time.** The first is highlighted. When a task is done its card **flies into the cube** and clicks a blue piece in; the next task slides in at the end, marked **NEW**. All 21 banked = the cube is built and spins, +100 XP, and the section clears after 7 days. Tap the cube to see every banked task and its date.
- **Each task opens in a pop-up** that can hold: what to do and why, an embedded **Loom** video, downloads, links (out, or to a tab or Live tool), a checklist, an upload, a form (the Foundation Form opens in Wheeli; the other three open in LaunchBay for now), a typed-name **sign-off**, and a note to the coach (lands in their tasks). **Mark done and bank it** finishes it (sign-off first, where needed).
- Some tasks tick themselves: Josh's video, the Foundation Form once sent, the ideal week, the first 20 and the first Friday review (the old five steps live on inside these).
- **Phone:** a Build Your Blueprint card on Today with the next task. **Coach view:** progress, every task with dates, sign-offs and uploads, and *Bank it for them*.
- **Editing tasks:** everything is in `source/byb-tasks.json` (titles, why, Loom link, files, links, checklist, upload, form, sign-off). Change it and run `build_all.py`. Items marked `todo` still need their content copied from LaunchBay (Loom links, file links, checklist items, booking links).

## Added 3 November 2026: Build Your Blueprint, native (all decks)

The BYB Google Sheet, built into **Live tools › 🧱 Build Your Blueprint** (Josh's pick: tables on a laptop, cards on a phone). It replaces the BYB Google Sheet link in every deck.
- **Asset register:** 15 asset areas (website, email, social, proof library, blog, newsletter, referral, sales scripts, videos, recruitment, project planning, safety, contracts, print media, funnel); add rows, link each asset, progress, impact, priority, cost, project, who, when, comments.
- **Company health checks:** all 54 checks from the sheet (Get the work, Complete the work, Field team, Get paid for the work, Business performance, Culture) with progress, impact, essential, priority, cost, prescription, who, when, comments.
- **Team & roles:** by department (Sales, Projects, Accounts, Operations, Admin, Trade team): name, position, reports to, and position description / KPIs / workflow status.
- **Lessons learnt:** mistake, cost, impact, priority, lesson learnt, wisdom implemented, under Get / Complete / Get paid for the work.
- **Employment cost:** the sheet's calculator working live (same maths: $30/hr gives $140.23 per billable hour), other employment costs, overheads, and the whole team with direct and overhead cost per hour, plus the break-even rate per billable hour.
- **Planner:** six months at a time, click a day to add what's on (live event, coaching, business, team, holiday), colour-coded.
- Coloured dropdowns as in the sheet (Need to do / In progress / Done, Impact 1–5, Yes/No, Low–High, $–$$$$$), tick boxes, progress per section and in total. **Resvita comments** can only be written in coach mode (🧑‍🏫 Coach, coach PIN).
- **Make it yours:** + Add a check under any health-check group, + Add a row / + Add a person anywhere, and **+ Add a section** at the bottom of every tab (name it, remove it with ✕). Built-in checks stay; your own rows can be removed (it asks first if they have something in them). **✓ Hide done** hides finished rows.
- Saved in the browser (`<brand>-byb-sheet`) until the backend; clients with a Google Sheet start fresh (Johanah can import later). Coaches can switch it off (Live tools › Build Your Blueprint).

## Added 4 November 2026: 🌱 ProjectU (at the top of Rocket fuel)

Everything Resvita gives beyond the tools, at the top of **Rocket fuel** above the China sourcing list. Four cards; tap **Open ›** on any of them (‹ ProjectU takes you back).
- **🧠 Project You:** your own growth in two tracks, **Mindset Development** (with your Mindset coach) and **Strategic Thinking** (with your Strategy coach). Tick lessons as you go, score your capabilities out of 10 each quarter (the chart shows where to lift first), and write a weekly reflection you can share with your Mindset coach.
- **🎓 Train & Transfer:** the 9 Core areas (Administration, Marketing, Pricing & Estimating, Sales, Operations & HR, Projects & Delivery, Accounts & Finance, Leadership & Culture, Reporting & Improvements). Pick an area to score you and each person from Build the role on its skills: **Do** (can they) and **Will** (will they), out of 10. Write who trains whom. Wheeli points out skills only one person has, and gaps nobody covers. **Team view** shows everyone across all 9 areas at once. When someone reaches 8+ on both, the skill goes into their Train & keep in Build the role.
- **1% Tradie:** the gold button (on the card, the page and each area) asks Resvita to develop a team member in an area for you. It goes to your Strategy coach.
- **📅 Events:** the live events in your programme. **Book my seat** adds it to your planner (Build Your Blueprint › Planner) and asks the Resvita team to confirm.
- **🤝 Trusted Network:** Trusted Platforms, Partners, Suppliers and the Resvita 50 Synergy Lab, each with what they do, any member offer, and **Introduce me** (or **Ask to join**), which messages your coach.
- Coaches can switch ProjectU, or any of its four parts, on or off per client (Coach view › Programme › Rocket fuel), and members can pin ProjectU to My Dashboard. The lesson lists, skills, event dates, network listings and 1% Tradie details are placeholders marked "to confirm" until Resvita supplies the real ones.

## Added 4 November 2026: Wheeli Free, the 📚 Library and the 99-point check

**Wheeli Free** (`Wheeli-Free.html`) is the same Wheeli for prospects in the Resvita community, at the Free level: the same tabs, with the members' parts locked (🔒) and their content left out of the file.
- **Home:** *Your 7 days to real numbers* (know your cost per hour, price one job, score the 99-point check, watch Start Right, your results), then **Your results so far** with **Apply to join the Resvita 50** and **Book a call**.
- **Open:** My Dashboard and the community, Live tools › Build Your Blueprint (Employment cost and the 99-point check) and Pricing (all four tabs: Quick, Fixed, Detailed and Popcorn), the Playbooks & training courses in the 📚 Bonus Library (no Start here section), Rocket fuel › ProjectU's Events, Trusted Network and Get there faster, and Ask Wheeli (3 questions a week).
- **Locked:** 10 Miles, Get it done, The Numbers, the members' Live tools and courses, and the rest of Rocket fuel. Tapping one says what it does, with Apply or Book a call.
- When someone joins, they move to the member Wheeli: same tabs, same places, the locks come off. Their results go with the application.

**Sign-in (so competitors can't open it):** host `Wheeli-Free.html` on its own address (e.g. free.wheeli.app) behind **Cloudflare Access**:
1. Put the file on the host (Cloudflare Pages, Netlify or similar) and point the address at it through Cloudflare.
2. In Cloudflare: Zero Trust › Access › Applications › Add an application › Self-hosted. Enter the address.
3. Add a policy: Allow, Include › Emails (paste the approved emails), or an email list you keep up to date. Login method: One-time PIN (they get a code by email).
4. Share the address from Circle's welcome space: "Get your free Wheeli: sign in with your email."
Free for up to 50 users. With the backend, this becomes proper free sign-up.

**📚 Bonus Library** (every deck): the gold 📚 Bonus Library button beside the Blueprint's sheet tabs (Home › your Blueprint card) opens every course in one place: Start here, Playbooks & training, Your Blueprint. Courses above your programme show 🔒 and the level they open in. Coaches set each course's section, and whether it's free, in Coach view › 📚 Lessons.

**99-point check** (every deck): a new tab in Live tools › Build Your Blueprint. Answer Yes, Partly or No to 99 checks across the 9 Core areas: you get a score out of 99 and your 3 weakest areas. (The checks are Wheeli's draft until Resvita's checklist goes in.)

**Get it done** no longer has the Focused / Everything bar.

## Added 4 November 2026: My Dashboard, Pricing, Focused for every page, Asset studio in Get it done

- **⭐ My Dashboard** (new tab after Home): the member's own one-page dashboard. Pin any part of any page with 📌 in that page's ⚙ list, or use **+ Add parts** (tick parts page by page) or **⭐ Wheeli's picks** (Today, On track, Your coaching, your Blueprint card, Tasks & projects). Each part is the real thing, live: tick tasks, open the timer, add numbers, just as on its page. ↑ ↓ to reorder, ⇔ for full or half width, ↗ to open its page, ✕ to take it off. Under the parts sits the **💬 Resvita community** (the Circle feed): members sign in with their community login the first time; **Open in a new tab** if their browser won't let them sign in there (some phones and Safari); **Hide ▴** folds it away. Coaches can switch it off per client (Programme › My Dashboard › Resvita community).
- **💲 Pricing** (Live tools, every programme): **Quick pricing** (job cost + admin % + margin % by job size, for projects and services, ex and inc GST), **Fixed pricing** (a package or unit rate: pick one of 13 ready-made trade rates such as Colorbond fence per metre, painting per m² or pressure washing per m², set the labour and materials, enter how many, get the price and the price per unit), and **Detailed pricing** (scope of works by section with materials, labour and subbie costs, a margin on each, the quote total always showing, and Add from a rate). Wheeli warns when a labour rate is under your cost per billable hour from The Numbers. Save quotes, or copy the price or summary. **🍿 Popcorn pricing:** give the client three options, $ · $$ · $$$, side by side: name each, list what it includes (each step up includes the one before), and set its price. The middle is marked Most popular, as most people pick it. Put in a starting price and **Fill the three prices** sets $$ about 30% and $$$ about 70% higher. Add each option's cost to see its profit and margin. Or use **⇢ Fill from** on any option to bring across what you've priced in Fixed or Detailed pricing, or any saved quote: its name, what's included, the price and the cost, ready to change. Once one option is filled in, **✨ Draft the other two from this one** writes the others for you: prices about 30% and 70% apart, each step up listing "Everything in …" plus upgrades that suit the job (pressure washing, decks, bathrooms, fences, painting, roofing, concrete, flooring, electrical, plumbing, landscaping, or general upgrades). Check the upgrades, then add each option's cost to see its margin. **Choose the one to sell:** tap **☆ Make this the one to sell** under any option's price. It gets the Most popular tag, and Wheeli re-prices the three so it's the best value: sell $ and the steps up are big, sell $$ and $$$ makes it look good value, sell $$$ and it's only a little more than $$ for a lot more. Save it as a quote, copy the three options, or copy them and open Get it done to write the proposal. **Your own packages:** set up any package or unit rate (or change one of Wheeli's), tap **💾 Save as my package**, name it, and it's in the drop-down (⭐ My packages, at the top) and the chips from then on, and in Detailed pricing's Add from a rate. Change one and **Save changes**, save a copy, or delete it.
- **🎯 Focused and Everything on every page:** each page's ⚙ list now has every section (Home included). **Coaches** set what each client's Focused view shows in Coach view › the client › Programme › ⚙ Turn tabs and sections on or off: tap 🎯 on any section. **✓ Everything on**, **🌱 Start minimal** and **🎯 Reset Focused** are there too. Clients can still change their own view with ⚙.
- **Asset studio** is now a button in Get it done (What do I work on? · Get it done · **Asset studio** · Review & Improve). It opens the same Asset studio as a pop-up; ✕ Close or Esc takes you back. The Assets tab is gone, so the tabs are simpler.
- **Build the role** and **Pricing** are in every deck.

## Added 4 November 2026: Build the role, find the person

**Live tools › 👥 Build the role**, from Resvita's Build the role / Find the person and Training & Culture sheets. Roles first, then people.
- **Org chart** drawn automatically from who each role reports to: filled roles in blue, roles being built or hired for in gold dashed boxes. Click a role to work on it. **Board** shows every role moving left to right: Build the role › Find the person › Hired · costed › Train & keep › Done, with each role's next step.
- **⭐ Company values** (value, what it is, what it is not), set once and used in every job ad, the interview questions and Train & keep.
- **6 steps per role**, each with Wheeli's advice and a blue **Next** bar to the following step:
  1. **The role:** task, measurable KPI, workflow and who they report to. ✨ *Fill it in for me* starts from Wheeli's example for 8 common roles (owner, sales & estimator, project manager, office & accounts, admin, leading hand, tradesperson, apprentice).
  2. **The person:** personality traits, skills, experience and pay, with what that pay really costs per billable hour (from Build Your Blueprint › Employment cost).
  3. **Job ad:** drafted from steps 1 and 2 and your values; edit it, ✨ Redraft, copy for Seek or Facebook, then mark it as posted.
  4. **Candidates:** add each person (or drop in a CV). **✨ Score the CV** opens Get it done › Review & Improve, scores the CV against this role's skills, experience and personality (demo scores until Wheeli reads real files), writes interview questions for the gaps, and saves the scores back. Plus interview questions for the role.
  5. **Hire & cost:** puts them on the org chart, adds them to Build Your Blueprint › Team & roles (ticked off once the position description, KPIs and workflow are done), and adds their pay to Employment cost: billable staff as employees, office and management wages as an overhead. Later changes to the role keep both up to date.
  6. **Train & keep:** Do? (capabilities) and Will? (capacity out of 10), how to improve each by +1, and training and culture for the position.
- People already in a role skip the job ad and candidates. Saved in the browser (`<brand>-roles`).

## Added 3 November 2026: Blueprint board (trial, Wheeli deck only)

Resvita's own whiteboard, in **Live tools › Blueprint board**, to try with a client before deciding to replace Miro. Built on Excalidraw (MIT licence, free to use in a paid product), loaded from the internet when the tool opens.
- **Boards:** as many as they like (tabs across the top), saved in the browser as they draw; ✎ Rename and 🗑 Delete.
- **Templates** (panel on the right; **+ New board** or **Add to this one**): **90 Day Focus** (destination, 3 outcomes, the one thing, 13 weeks), **Workflow map** (Owner / Office / Crew swimlanes across Get the work → Complete the work → Invoice the work, with a "Paid?" decision), **Ideal client**, **Org chart**, **Core Cause Rectification Plan**, or a blank board. Every shape can be typed in, moved, recoloured and connected.
- **⬇ Picture** saves a PNG. **🧑‍🏫 Share with my coach** sends a picture of the board to their Strategy coach in Ask › Ask my coach.
- **Limits of the trial:** one person per board (no live editing together; that needs the backend), boards stay in that browser, and it needs internet to load. Coaches can switch it off (Live tools › Blueprint board).
- Once tried: decide whether to roll it out to every deck and replace the Miro link in Business Blueprint.

## Added 3 November 2026: Coach view › ➕ New client (Wheeli deck)

Set up a client's Wheeli from the coach view: **logo** (drop it in; Wheeli picks the brand colour from it, which you can change), **brand colour** and logo background with a **live preview of their header**, the business (name, short name, website, trade, area, tagline, 90-day goal), the people (owner, what Wheeli calls them, email, phone, office person), **what Wheeli's brain needs** (3 services, 3 differences, 5 typical jobs), their tool links (Databox, BYB sheet, Miro, Flow), **programme, Mindset and Strategy coach**, start date and build notes. Saves as you type; **Mark ready to build** checks the essentials; **⬇ Download the setup file** gives `wheeli-client-<key>.json`. Then: `python3 -I source/add_client.py wheeli-client-<key>.json` saves the logo and setup and lists what's left (client entry, brain profile, icons, build). Once the backend is live, this creates the sub-account and emails the invite straight away (the "Creating a client" flow in the backend brief).

## Added 3 November 2026: Ask my coach (messages with attachments, all decks)

The header button is now **💬 Ask**, with two tabs (Josh's pick B):
- **💬 Ask Wheeli:** as before. When Wheeli has no method for a question, it offers **🧑‍🏫 Send this to Josh** with the question already filled in.
- **🧑‍🏫 Ask my coach:** three buttons across the top (Strategy coach, Mindset coach, Support) and the conversation gets the rest of the panel; pick **their Strategy coach**, **their Mindset coach** (the names come from Coach view assignments) or **Support** (the Resvita team: billing, tech help, anything else), then message with **📎 attachments** (quotes, CVs, photos, PDFs, spreadsheets). "Usually replies within 1 business day" (`reply_time` in `source/hub.json`).
- Ask my coach stays available even if the coach switches Ask Wheeli off for a member.
- Shortcuts: **💬 Message Heidi / Josh** on the Mindset and Strategy cards (10 Miles) and in its See all pop-up; **🧑‍🏫 Message my coach** in the phone's Ask tab. Unread replies show as a gold number on the Ask button.
- **Coach view › 💬 Messages:** opens on the logged-in coach's own conversation (Strategy, Mindset, Resvita team), unread first; open attachments, reply with attachments. Unread messages also show in the client's alerts.
- **Preview limits:** messages and attachments are saved in the browser they're written in (attachments up to ~0.9 MB are kept; bigger ones keep just the name), so a coach on another computer won't see them yet. With the backend: a `messages` table and file storage per sub-account (in Australia, visible only to that client and their coaches, deleted after a set time), plus an email or SMS through GoHighLevel when a message arrives or a coach replies. Still to decide: who reads **Support** messages (`team` in `hub.json`).

## Added 3 November 2026: Coach view › 📚 Lessons

Where coaches set what members see when they tap **Watch the lesson** on a Blueprint part: for every course and lesson, the title, **video link** (Wistia, Loom, Vimeo or YouTube; a Wistia share link like `resvita.wistia.com/s/…` is converted automatically and fills in the title), key points, **resources** (name + link, e.g. Google Drive), and which **Blueprint boxes** open it: click the boxes on a map laid out like the member's Blueprint (the Core 9 grid, 12 Pillars, 180 Power Frame and 90 Degrees of Scale, plus the Bricks and Blocks and B.I.G sheets). Gold = this lesson, light blue = opens the course, grey = another lesson; one box opens one lesson. Courses tick the sections that open them (e.g. Core block 1, the 12 Pillars). Add, reorder and delete lessons and courses, and **Preview as a member**. Edits are saved in that browser and used straight away there; **⬇ Download lessons.json** and send it to Johanah to replace `source/lessons.json` so every client gets them (with the backend, saving updates everyone).

## Added 3 November 2026: On track (The Numbers, all decks)

A quarterly scorecard at the top of The Numbers (Josh's pick A), so members can see they're on track for this quarter's goals, month by month, **without connecting Xero**:
- Gauges for **revenue (Project 271)**, **net profit (Project 15)** and the **lifestyle number** (net profit this year against what their life costs). The dashed line is where they should be for the months entered; green, amber or red says how they're going ("On track · $3k ahead", "A bit behind · $1k to catch up").
- **Month by month:** revenue, net profit, gross margin, cash in and out, owed to you and you owe, with green, amber and red dots. Months not entered yet show their target in grey. ‹ › moves between quarters.
- **+ Add <month>'s numbers:** seven figures from their P&L and balance sheet (about two minutes; their bookkeeper can do it). **⚙ Targets:** yearly revenue, net profit, gross margin goal and lifestyle number, set once with their coach. Each month's target is a twelfth of the year.
- **🔑 Key number · cost per billable hour** (under the gauges): what every billable hour costs the business (wages, on-costs and overheads, team average), split into labour and overheads, straight from Build Your Blueprint › Employment cost (same maths). Add **your charge-out rate** to see the profit (or loss) per hour. **Open the calculator ›** jumps to Live tools › Build Your Blueprint › Employment cost.
- Example figures show until they add their own. Saved to `<brand>-ontrack` (a `monthly_numbers` table with the backend). Coaches can switch it off (The Numbers › On track). Every programme.
- This is step 1 of replacing Databox for goal tracking. Step 2 (after the beta): each client connects their own Xero, read-only, summary figures only, to fill the months in automatically. Facebook and Google Ads stay on Databox (or a smaller plan) for those who want them.

## Changed 3 November 2026: Updates & coaching moved into 10 Miles

The Updates tab is gone. The top of 10 Miles has two cards side by side, for every programme and in the Focused view too: **🧠 Mindset coaching** and **🎯 Strategy mentoring**. Each shows that coach's sessions (path, next session and what to prepare), the next call with that coach (Join, Add to calendar), Book and 💬 Message. Updates aren't on 10 Miles any more: they're on Home (Updates & news) and in See all. **See all** opens the full view in a pop-up: every update by type (News, Events, Recordings) and every call, past calls with notes, actions and recordings. On the phone: the next-call card on Today and *Updates & coaching* in More open the same pop-up. The Circle community link was removed. Tabs are now Home · 10 Miles · Get it done · Assets · The Numbers · Live tools · Rocket fuel. (Start Right members don't see the 10 Miles list, so the two cards sit side by side.)

## Removed 3 November 2026: the Blueprint Install tab

The tab is gone from every deck: the gold **Open my $… Blueprint Install** button on Home's Blueprint card (named by programme) does the same job with less clutter. 

## Added 3 November 2026: lessons in Wheeli, and Updates & coaching (all decks)

Moving off Circle (Josh's picks: B, D and E).
- **Lessons play inside Wheeli.** A Blueprint part with a course shows **▶ Watch the lesson · In Wheeli**, which opens the course player at that course and the first lesson not yet watched: a big video, key points, the course's lessons down the side (ticking as they're watched), resources, **Mark watched**, **Ask Wheeli about this lesson** and **Ask my coach to sign off** (a task for the coach). Videos can be Wistia, Loom, Vimeo or YouTube. Courses and lessons are in `source/lessons.json`: the Big 12 Pillars (with Josh's 12 Pillars video) and Increasing Cashflow so far, with key points from the approved method. A Wistia share link (`resvita.wistia.com/s/…`) needs its embed link (`fast.wistia.net/embed/iframe/<id>`).
- **The Community tab is now Updates** (Updates & coaching). Left: Resvita's updates as an inbox (News, Events, Recordings, read or unread, Mark all read), each opening to read, watch or follow its button. Right: **Your coaching**, with the next calls (Join, Reschedule, 📅 Add to calendar as an .ics file), **Book Mindset** and **Book Strategy** with their own coaches, and past calls with notes, ticking actions and recordings. A link at the bottom keeps the Circle community reachable while everything moves across.
- **Coach view › 📣 Updates & calls:** post an update (type, title, text, video link, button, pin), pin or remove updates, add a coaching call (type, date, time, length, Zoom link), and after a call add the recording, notes and actions.
- **Phone:** a 🎧 next-call card on Today (within the week) and **📣 Updates & coaching** in More.
- **Examples and links** are in `source/hub.json`: the booking links for Heidi, Nadja and Josh are still to add (until then *Book* sends the coach a task).
- Until the backend is live, posts and calls are saved in the browser they're made in. With it, they become `updates`, `update_reads`, `calls` and `call_notes` tables for each sub-account, and posts go to every member (plus email or SMS through GoHighLevel for the important ones).

## Install on a phone (home-screen app)

Each deck can be installed as an app, but only once it's **on a website** (https). It won't install from a file sent by email.
1. Upload these together, in one folder: the deck (`Wheeli-Deck.html` or `Murphys-Construction-Deck.html`), its `.webmanifest` file, `sw.js`, the `app-icons/` folder and `ResVita-Member-Referrals.pdf`.
2. **iPhone:** open the deck link in Safari, tap Share, then **Add to Home Screen**.
3. **Android:** open it in Chrome, tap ⋮, then **Install app** (or Add to Home screen).

It opens full screen with the Wheeli mascot (or Murphy's "M") as its icon. The last version opened works offline. Live tools and links still need internet. Home, Live tools and the ROI dashboard suit portrait. The animated slides read best with the phone turned sideways.

**Communications:** a demo of Wheeli's inbox triage with example messages. Pick a message, switch between the standard and shorter draft, edit it, then Approve and copy. Complaints show as flagged, not drafted. The buttons open Claude (where members connect their own Gmail or Outlook) and Flow conversations. Change the example messages in `source/build_comms.py`.

**3 Major Growth Pipelines:** sales pipeline (GoHighLevel), rolling invoice schedule (job software) and 13-week cashflow (Xero), each shown as a bucket against its target, with a Wheeli warning that reads all three. Bank, overheads, payment terms and buffer are editable. Change the example figures in `source/build_cashflow.py`.

**Tasks & projects:** add anything on the member's plate with what, who, when, priority (urgent/important), pipeline, type and why. Switch between the list and the Urgent / Important matrix, filter by person or status, and download a CSV. Tasks are saved in that browser only. Change the example tasks in `source/build_tasks.py`.

To rebuild the decks after changing any page, run `python3 -I source/build_deck.py` from this folder.

There are two animated embeds in this folder. Both embed the same way (see the options below). Just swap the file name.

| File | What it is | Size |
|---|---|---|
| `resvita-ai-brain.html` | The Resvita AI brain graph | ~63 KB |
| `murphys-ai-brain-capabilities.html` | Lance's brain on a screen, with the three capabilities playing out live | ~580 KB |
| `murphys-asset-studio.html` | Lance's asset studio: his brief types in, then 12 assets generate one by one | ~124 KB |
| `wheeli-asset-studio.html` | Wheeli-branded asset studio for sales calls: a generic brief types in, then 12 assets generate (still: `Wheeli-Asset-Studio.png`) | ~266 KB |
| `wheeli-layer-below.html` | Clicking into the sales script card: the card zooms open, the script types in, and each numbered tag lights up its source file (still: `Wheeli-Layer-Below.png`) | ~1 MB |
| `murphys-layer-below.html` | Lance's version: retaining wall script in his voice, his folders, Murphy's green (still: `Murphys-Layer-Below.jpg`) | ~930 KB |
| `wheeli-capabilities.html` | The same, unbranded for marketing: Wheeli lockup, the mascot rolling in, examples that fit any trade business | ~620 KB |

The Wheeli still image (`Wheeli-AI-Brain-Capabilities.png`) is the finished frame of `wheeli-capabilities.html`. Open the file with `?static=1` on the end to see that frame in a browser. To rebuild the Wheeli file after editing `source/wheeli-template.html`, use the same command as the Murphy's one below, but swap in `wheeli-template.html`, `wheeli-capabilities.html`, `__MASCOT__` → `wheeli-mascot.png` and `__SCREEN__` → `generic-screen.jpg`.

### What the Murphy's capabilities embed does

- The header, the screen with Lance's slide and the three cards slide in. A scan line sweeps the screen.
- **1 · Full business analysis:** Lance's question types itself out. Each of the five checks spins, then ticks green, while the progress bar fills to "Report ready".
- **2 · Bespoke assets:** the quote, social post, flyer and safety document each show a "generating" shimmer, then pop in.
- **3 · Opportunities:** a new example event slides in at the top of the live feed every few seconds and the older ones shuffle down. It cycles through 8 examples.
- The ask bar types a different example question every few seconds.
- The analysis and asset sequences replay every 10 seconds or so, so visitors who arrive late still see them.
- Visitors with "reduce motion" turned on get the finished state with no movement.

To change it, edit `source/capabilities-template.html`, then rebuild the single file by running this from the `Website-Embed` folder:

```bash
python3 -c "import base64;b=lambda f,t:'data:image/'+t+';base64,'+base64.b64encode(open('source/'+f,'rb').read()).decode();s=open('source/capabilities-template.html').read();open('murphys-ai-brain-capabilities.html','w').write(s.replace('__RESVITA__',b('logo-small.png','png')).replace('__MURPHY__',b('murphys-logo-small.png','png')).replace('__SCREEN__',b('murphys-screen.jpg','jpeg')))"
```

---

`resvita-ai-brain.html` is one self-contained file (about 63 KB). The graph data and logo are built in. It only loads two things from the web: the Montserrat font (Google Fonts) and d3 (cdnjs).

## What it does

- Starts when it scrolls into view. The brain appears first, then the engine, the agents and each outer section fly out ring by ring.
- The headline and copy slide in, and the stats count up to 10 / 12 / 8 / 181.
- After the intro, the dots float gently, the brain pulses, and small "data" pulses travel along the connections.
- Hover (or tap on mobile) a dot to light up everything it connects to. Hover a legend item to light up that whole group.
- Scales to fit any box it's placed in, keeping its 16:9 shape.
- Visitors who have "reduce motion" turned on get a still version.

## Option 1: Host the file (best)

Upload `resvita-ai-brain.html` to your website hosting, for example `https://resvita.com.au/embed/resvita-ai-brain.html`. Then paste this where you want it:

```html
<div style="position:relative;width:100%;aspect-ratio:16/9;border-radius:12px;overflow:hidden;">
  <iframe src="https://resvita.com.au/embed/resvita-ai-brain.html"
          title="The Resvita AI Brain"
          loading="lazy"
          style="position:absolute;inset:0;width:100%;height:100%;border:0;"></iframe>
</div>
```

Change the `src` to wherever you uploaded the file.

## Option 2: Website builders that won't take .html uploads (Wix, Squarespace, some WordPress themes)

Add an **Embed / Custom HTML / Code** block. Open `resvita-ai-brain.html` in a text editor, copy everything, and paste it into the block. Set the block to a 16:9 shape, for example 1200 × 675.

## Changing it

Edit `source/template.html` and `source/graph-data.json`. Then rebuild the single file by running this from the `Website-Embed` folder:

```bash
python3 -c "import base64,json;t=open('source/template.html').read();d=json.dumps(json.load(open('source/graph-data.json')),separators=(',',':'));l='data:image/png;base64,'+base64.b64encode(open('source/logo-small.png','rb').read()).decode();open('resvita-ai-brain.html','w').write(t.replace('__DATA__',d).replace('__LOGO__',l))"
```

## Client decks (one per client, in their brand)

Each client gets a full Wheeli deck in their brand: their logo, colour, name and example content. Their saved data is kept apart from every other deck.

1. Add the client to `CLIENTS` in `source/clients.py`, with:
   - name, how Wheeli greets them, brand colour, and their logo in `source/clients/`
   - their 90-day goal, example tasks, sourcing list, M&A and new business ideas, and phone answers
   - `replace`: example wording to swap for wording that fits their trade
   Anything left out falls back to the Wheeli examples.
2. Make home-screen icons named `app-icons/<key>-180.png`, `-192.png` and `-512.png`.
3. Build everything (from Website-Embed/): `python3 -I source/build_all.py`. This writes `<Name>-Deck.html` and `<key>.webmanifest`.
4. Record their welcome video as `videos/<key>-welcome-tour.mp4`, then rebuild. Until it exists, Welcome plays the Wheeli tour.

**First client: 365 Alongside** → `365-Alongside-Deck.html`
- Brand blue #3E52D9, with their navy logo on a white card.
- Greeted as "Team 365" until the founder's first name is set (`who` and `first`).
- Examples are written for Queensland strata remediation, maintenance and cleaning.

**Second client: iClimb Tree Services** → `iClimb-Tree-Services-Deck.html`
- Founder Dylan Nacamuli.
- Deeper lime #7CC242, their brand lime #B5ED78 made dark enough for white button text.
- Their logo sits on a black card (`card` in the client entry).
- Examples are written for a Mornington Peninsula and Bayside tree service: removals, hedging, stump grinding and arborist reports.

**More clients (2026-10-28):**

| Deck | Owner | Colour | Examples written for |
| --- | --- | --- | --- |
| `Onsite-Mechanical-Repairs-Deck.html` | Steve | #0084C0 | Mobile mechanics and fleets, Newcastle, Lake Macquarie and the Hunter |
| `Pinnacle-Surface-Solutions-Deck.html` | Bryn and Heiko | #4F7FA8 | Driveway, roof and deck restoration, Melbourne |
| `AquaWave-Plumbing-Solutions-Deck.html` | Trent | #1890CC | Plumbing for homes, agents and builders, SEQ |
| `Gard-Coatings-Deck.html` | Matt | #0078B4 | Epoxy floors, Rockingham and Perth |
| `Platinum-Surface-Solutions-Deck.html` | Isaac | #B8862E | Pressure and commercial cleaning, Gold Coast and Brisbane |
| `Graphite-Glass-Solutions-Deck.html` | Jon | #E8770A | Glass and glazing (no website; examples with no suburbs) |
| `Love-Your-Reno-Deck.html` | Clint | #4E6A86 | Kitchen and bathroom renovations, North Brisbane |
| `Twigg-Electric-Deck.html` | Tim | #D9341A | Commercial and residential electrical, Melbourne's inner north |
| `Fawcett-Group-Deck.html` | Mark | #D63A2F | Plumbing, gas and electrical, Adelaide |
| `Solutions-240-Deck.html` | Andrew | #2E6DA4 | Solar, batteries and aircon, south-east Melbourne |
| `Neon-Deck.html` | Luke | #D93A3A | Building and renovations (no website; no suburbs) |
| `Fine-Line-Carpentry-Deck.html` | Sean | #B08A62 | Carpentry, joinery and fit-outs (no website; no suburbs) |
| `Freeman-Electrical-Communications-Deck.html` | James | #4E9A2E | Electrical and data cabling (no website; no suburbs) |
| `Cool-Innovations-Deck.html` | Lee and Lisa | #2A7FC1 | HVAC and electrical (no website; no suburbs) |
| `Parker-Dean-Construction-Deck.html` | Harry and Amy | #C0913A | Formwork, decks, pergolas and carpentry, Gold Coast |

Pinnacle's logo was cropped from their website header image, because the logo file their site lists belongs to another business.

Deck file names use letters, numbers and dashes only, so they're safe in web links (for example `Freeman-Electrical-Communications-Deck.html`). Clients without a website get examples with no suburbs or state. Accent colours are made dark enough for white button text: Freeman's is the green from their logo rather than its yellow.

**Coach roster:**
- **Wheeli deck:** its Coach view (PIN 2020) lists every client: Murphy's plus everyone in `source/clients.py`, each with their goal, one thing, 10 Miles and Rocket fuel ideas. Their progress figures are placeholders until the backend syncs real data.
- **Client decks:** each client's own Coach view shows only that client, live, so no client's file contains another client's details.
- **Adding a client** to `clients.py` adds them to the roster on the next build.

**Client AI brains:**
- **How they're built:** each client deck's Home shows their own animated AI brain, Murphy's brain and page-turn with the client's name, logo, colour, services, facts and five sample jobs. `source/build_client_brains.py` builds them from `murphys-brain-animated.html`.
- **To add a client:** add a line for them to `BRAIN` in that file (3 services, 3 facts, 5 jobs). Without one, their Home uses the Wheeli brain.
- **Wheeli deck:** keeps the generic Resvita brain.

**🎥 Get It Done Live** (every deck, Wheeli Free too): Rocket fuel › ProjectU's second row shows the next three weekly masterclasses as cards, with Join live while one is on, I'm going and 📅 Add to calendar, and Recordings › for past sessions. Coaches add sessions, recordings and the live room link in Coach view › 🎥 Get It Done Live.

**📚 D.I.Y 7 Figure Playbook** (Bonus Library): tap it to see its 3 steps, Step one: Get results (Results Pack), Step two: Gain traction (Traction Toolkit) and Step three: Build momentum (Momentum Blueprint), each with its progress. A step opens at the first lesson not watched; the list down the side is split into its sections with each lesson's length, and shows how many lessons are complete. Coaches add videos, key points, sub-tasks, outcomes, uploads and resources to any lesson in Coach view › Platform content › Lessons (pick the step, then the lesson), and can set a lesson's section and length, a course's About text, and for a step its label, card word and shade. **Sub-tasks:** coaches add them one per box (+ Add a sub-task, Enter for the next, ↑ ↓ to reorder, ✕ to remove) in Coach view › Platform content › Lessons; members see them under a lesson's video (tick them off, or + Add to my tasks). A guide with screenshots: How-to-add-lesson-sub-tasks.png in Brand copy.

**Your journey** (Home): the five steps now show where each member is up to and open it. **Complete business audit** is optional: for each area (bookkeeping, accounting, website, insurance …) members ask for an intro to a Resvita trusted partner, mark the session done, or skip it if they're happy with who they have. A **Business audit** row under the 30-day path shows each area as a chip (green done, blue intro asked, faded skipped); tap one to ask for an intro, mark it done or skip it. **20-20 Vision** keeps them proactive: a weekly, monthly and quarterly (Boardroom 90-day plan) checklist, each linking to the right tool, showing when it was last done and when it's due. The Build Your Blueprint 30-day path no longer includes the forms; they sit in the Your Blueprint forms banner so members can do tasks and forms side by side.

**🚀 B.I.G Projects** (every member deck): the three projects for each programme (e.g. Grow 1.0: Selling system, Training system, Recruitment system), done in order (a Grow member does Start Right's three first). On 10 Miles (and pinned to My Dashboard) members see the ladder and their current stage: its three projects and the current one's tasks to tick. ✎ Tasks sets the tasks for any project with the coach; 🛣 Put this stage on my 10 Miles makes it the 90-day destination, the projects the miles, and sends the tasks to Tasks. Coaches set Resvita's starting tasks in Coach view › Platform content › 🚀 B.I.G Projects, and see each client's progress (and mark stages already in place) on their client card.

**📝 Blueprint forms** (every member deck): the Build Your Blueprint forms from LaunchBay, by programme like the Blueprint: everyone gets the Foundation Form and Member care; Start Right adds Big 12 Pillars and B.I.G Framework; Grow 1.0 adds Core Nine Blueprints; Build 2.0 adds 90 Degrees of Scale; Partner 3.0 adds 180 Powerframe. Home's banner lists them with progress. Members answer a section at a time, tap 🎤 Talk to speak any answer, and it saves as they go; Send to my coach lets the coach know. Coaches change questions, sections and which programme gets each form in Coach view › Platform content › 📝 Blueprint forms, and read every answer on the client card.

**🎧 Coaching sessions** (every member deck): Mindset coaching and Strategy mentoring as a path of sessions, like LaunchBay. Members see it in 10 Miles › Your coaching: a tab per coach, where they're up to (Build Your Blueprint sessions for their programme, then the member sessions) and the next session with what to prepare. Opening a session shows why we're doing it, the worksheet, the pre-session form (saves as they type; the coach reads it before the call), sub-tasks, an upload box and sign-off (type your name and tick); finishing it opens the next. Coaches edit every session and form in Coach view › Platform content › 🎧 Coaching sessions, and see each client's path, pre-session answers and Mark done / Open early on their client card. Edits reach new clients; anyone part-way through a session keeps the version they started.

**📞 Calls & context** (Coach view › each client card): after a coaching call, drop or paste the transcript (Zoom, Teams, Otter, Fathom, a text or Word file) or record a voice note, then tap ✨ Read the call. Wheeli drafts a summary, the actions (with due dates) and the new things it learnt about the member and their business. Check and edit it, untick anything Wheeli shouldn't use with the member (it's kept in your coach notes with a 🔒), choose whether to share the summary and the transcript, then ✓ Approve & send: the summary shows in their Your coaching, the actions land in their Tasks, and what Wheeli learnt is added to their context, so its answers get more specific to them over time. The call history keeps every call, its actions (tick them off) and its transcript; 🧠 Everything Wheeli has learnt lists what it knows, with where each point came from. Until the backend is live, other clients' summaries reach them once their deck syncs.

**🛠 Platform content** (Coach view): every card, check, lesson and event members see, edited in one place. Pick what to edit, pick the item (DONE / TO ADD), then fill in the description, video, resources (a name box and a link box for each, + Add a resource) and action points (one box each). 👁 Preview as a member shows how it will look. Saving shows it in your browser straight away. To put it in every deck, tap **⬆ Publish to all decks**, then run:

```bash
python3 -I source/add_content.py ~/Downloads/wheeli-content-<date>.json
python3 -I source/build_all.py
```

**Lesson sub-tasks:** in Coach view › Platform content › Lessons, each lesson can have sub-tasks (one per line), an outcome and a file upload box. Members tick the sub-tasks off under the video (or add them to their tasks) and upload their finished work.

**🏆 Top 50 Awards** (every deck, Wheeli Free too): a gold banner on Home with Nominate and Vote (top50tradebusinesses.com.au) and a countdown to voting closing on 30 Sep 2027. Change it in Coach view › Platform content › Top 50 Awards; the coach can switch it off per member (Home › Top 50 Awards banner).

**📒 Chart of accounts & budget** (Live tools, every programme): set up your accounts (income, cost of goods sold, operating expenses, or paste them from Xero), set a budget for the financial year month by month, then each month type or paste your actuals to see what's over and under. The Numbers shows it as **Budget vs actual**, and your actuals fill On track too.

**📥 Update my numbers** (Live tools › Chart of accounts & budget › tab 4): export from Xero, your job software (simPRO, AroFlo, ServiceM8, Tradify, Fergus) and your CRM as CSV, and drop them in. Wheeli matches the columns once, and every dashboard in The Numbers (Budget vs actual, On track, the ROI dashboard's actuals, Your contribution and the 3 Major Growth Pipelines) switches from example figures to yours. About 5 minutes on a Friday.

**▴ Collapse sections:** hover any section and tap the small ▴ at its top right to tuck it away into a slim bar; tap the bar to bring it back. The ⚙ button (bottom left) also has Collapse all and Expand all. It's remembered per page, and works alongside 🎯 Focused. Use ↑ ↓ in the same ⚙ list to move sections up or down the page; ↺ Order puts it back.

### 🤝 Intros and "Build Your Blueprint complete" (4 Nov 2026)

- **Intros:** when a member taps 🤝 Introduce me in the Business audit, or Introduce me / Ask to join in Trusted Network, the coach gets a message and the request also lands in **Coach view › 📥 Inbox › 🤝 Intros**, where it stays until it's done. Type the partner's name (and a note if you like), set it to **Introduced**, and the member's audit shows who to expect. It closes when the member ticks ✓ Done, or when you set Done / Not needed.
- **Build Your Blueprint complete:** a week after a member banks all 17 tasks, Home swaps the 30-day path, the forms banner and the audit row for one slim green bar with 📝 My forms, 🧊 My 17 banked tasks and 🔍 My audit, so everything stays one tap away.

### 📱 The phone app: Ask, Messages, Tools (5 Nov 2026)

- **Tabs:** Today · Messages · Ask · Tools · Me. Community is now inside Me.
- **Messages:** every customer message with Wheeli's reply ready. Check it, change the tone if you like, Copy reply, send it from your email or texts, then tap Mark as sent. Complaints are flagged, not drafted. Examples for now; real inboxes connect once the backend is live.
- **Ask my coach:** pick what kind of question it is, tick Add my numbers, and see when your coach will answer before you send. Or tap Save it for my next session, and it shows in that session. Can't wait? Book a 15-minute call or come to Get It Done Live.
- **For coaches:** set when you answer messages in Coach view › Inbox › Messages (default 12pm and 4pm, Monday to Friday, quiet after 6pm). Members see it before they send.
- **Coaches on a phone:** open the Coach view on your phone and it becomes a coach inbox. ⏱ Round shows each member's question with Wheeli's reply already drafted from the Resvita method: ✓ Send it, ✎ Edit it, or 🎤 talk your own. After you reply, **+ Teach Wheeli this** saves it so Wheeli can answer the next member, once it's approved in Inbox › Wheeli feedback › Taught by coaches on the laptop.

### 📈 Paid ads review (5 Nov 2026)

Get it done › Review & Improve › **Paid ads: Google / Meta**. Drop in the monthly report your agency sends (or an export from Google Ads or Meta Ads Manager). You get a score, what's working, the top 3 fixes, **Is your agency doing right by you?**, three questions to ask them this month, and a ready-to-send email. Demo feedback for now, like the other review types.
- **What did the ads actually win?** Under the review, type how many real enquiries, quotes and jobs came from the ads that month. Wheeli works out the cost per job won, the return, and what's left after the agency fee, then 💾 Save puts it on **The Numbers › Paid ads** (with a 6-month trend) and in the monthly report.
- Get it done now remembers which tab you were on (What do I work on?, Get it done, Review & Improve) when the page is refreshed.

### 💰 Get paid (6 Nov 2026, every member deck and programme)

Live tools › **Get paid** makes sure the work turns into money.
- **💸 Who owes you**: what's owed, what's overdue, money owed by age, and a 6-step chase for each invoice (friendly reminder, firm reminder, phone call, final notice and pause work, letter of demand, recovery options). Wheeli drafts every message from the invoice: copy it, or 📤 Send via Flow (switched on at go-live; nothing sends unless the member taps it). Payment plans, ✓ Paid, Ask my coach, and Paste from Xero (Aged Receivables).
- **🤝 Suppliers**: what you spend with each supplier and your terms; tick what to ask for (longer terms, trade discount, early-payment discount, price lock, rebate, free delivery, credit limit) and Wheeli writes the email. Record what you won.
- **🛡 Stop it happening**: the 10 habits that get you paid on time.
- Bailey's "Owed to you · Chase" opens it. General information, not legal advice (it says so on the page).

### 🧑‍🏫 New in the Coach view (6 Nov 2026)

- **📅 Coaches & booking links** (Platform content): each coach's calendar link; members' Book Mindset / Book Strategy buttons open it.
- **🗓 Resvita 50 Weekly Session** (Platform content): every Thursday 1:30–4:30pm QLD; set each week's topic, see who's coming and the questions sent in. Members see it under Get It Done Live in Rocket fuel, with I'm coming, Ask in advance and a 15-minute slot.
- **🤖 AI tools they use** (client card): tick the tools a client uses, see what each does, 🔌 Connect (switched on at go-live).
- Wheeli deck only (Resvita's admin area): **🗂 Wheeli improvements** (feedback and the weekly update with Claude), **📣 Ad creatives** (the 20 Meta ads: vote, go live, results; link to the landing page), **📊 Pitch deck** (15 slides, ⛶ Present), **🔐 Access & security** (roles, client team seats), **🔗 Links** (every button that goes somewhere, set or missing).

- **🌅 Today**: who needs this coach today (messages waiting, overdue actions, Needs you, gone quiet), most urgent first.
- **Inbox › 🏙 Event bookings** (who booked which Synergy Lab state, seats left) and **⭐ Session ratings** (members rate each call and live session; an improvement note per rating).
- **✅ Team tasks** beside Wheeli improvements: owners, due dates, the daily huddle, this week and the monthly review.
- **Resvita 50 recordings**: add the recording and timestamps after each session; members get them under the session.

- **📣 Team drops** (Platform content): share a Loom, a post, a book or a tip; members see it once as a pop-up.
- **🧑‍🏫 Coach prep** inside each coaching session (coaches only), and **📋 Before the call** on each client card: a one-page summary to copy into your notes.
- **📚 Working on now**: the course a member is working through sits at the top of My Dashboard (the coach can pick it on the client card).

- **🎯 Your 90-day win** on Home (one number to hit in 90 days), and a **🎉 celebration** when they hit it or move up a programme (share it, refer someone).
- **📊 Ask for a custom dashboard** at the bottom of The Numbers (coaches answer in Inbox › Dashboard requests).
- **🗄 Filing cabinet** in Review & Improve: keep any review to come back to; coaches see it on the client card.

### 🧪 Drafts in the Wheeli deck only (6 Nov 2026), rolled out once Josh signs them off

- Live tools › **🏗 Job profit & cost to complete**: every job's quoted vs forecast profit, and each job from quote to sign-off. Signed off; waiting on which programmes get it.
- Home › **🎬 Welcome tour**: the welcome video script, narrated, moving around the deck.
- 📱 Phone view › **▶ Tour**: a walk through each tab of the app.
- Brand option A has started on Home: the one next step is the Sand card.

### Also on 6 Nov 2026 (every member deck)

- **Synergy Lab**: pick QLD (Wed 20 Jan), NSW (Thu 21 Jan) or VIC (Fri 22 Jan 2027), 10am–2pm.
- **Get It Done Live and Resvita 50 RSVPs**: the pop-up the day before and on the day, with 15-minute time slots.
- **Your crew**: 😮‍💨 I'm overwhelmed (the one next move, loop in a coach), 🤝 Refer a trade owner (50% of their Build Your Blueprint fee, or give it to them as a discount), 📣 Follow Resvita.
- **Platform content**: add, hide and re-order items in every list.

### 🪣 Wheeli's sidekicks: Bailey and Flow (5 Nov 2026)

- **Bailey** looks after the numbers. His leak check sits at the top of The Numbers: costs over budget, money stuck with customers, ads that didn't pay. Each one has a button to fix it. Until a member's own numbers are in, he shows example leaks.
- **Flow** looks after customers: he's at the top of the phone's Messages and on Live tools › Communication, telling you who's waiting and how many replies are ready.
- **Your crew** on Home (and the phone's Today): one line each from Wheeli, Bailey and Flow, with one tap to their part of Wheeli.

