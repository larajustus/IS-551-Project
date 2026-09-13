# Arcview

Helmet-cam weld review for welding instructors. Every student's helmet camera streams to one screen, so an instructor can watch a whole class weld live and then pin timestamped feedback to any individual recording.

---

## 1. Need, persona, capability, value

| | |
|---|---|
| **Need** | An instructor has a full room of students learning to weld. Walking the floor, they can't see what any one student's hands, angle, and travel speed are actually doing during the weld. They can only see the finished bead. That costs them the chance to give precise feedback and catch teaching moments while they matter. |
| **Persona** | Welding professor/teacher, class sizes of 15+, teaching beginning welding, required by curriculum to give specific feedback. |
| **Capability** | Provide welding feedback to students. |
| **Value** | *Tailored.* The teacher observes each student's individual weld and responds to that student's specific technique, instead of teaching to the average. |

---

## 2. The three screens

**Screen 1 — Landing**
- **Job:** In one glance, communicates that this site lets an instructor watch each student weld and respond to them individually, and sends them to Get Started.
- **Why it earned its slot:** First screen a user ever sees. It has to carry the value proposition and the entry point.
- **Design question it examines:** Why should this person care in the first three seconds? Could a stranger still tell what it does and who it's for?

**Screen 2 — Live class dashboard**
- **Job:** Show that the instructor can now watch an entire room of welders in detail at once instead of walking the floor.
- **Why it earned its slot:** Clearest demonstration of the "class of 15+" problem being solved.
- **Design question it examines:** Does the interface fit the real task (scanning a live class), or is it just data on a dashboard?

**Screen 3 — Individual weld review and feedback**
- **Job:** Show tailored feedback actually happening — one recorded weld, one comment being written at 00:42.
- **Why it earned its slot:** Screen 1 promises tailored feedback; this screen is the receipt.
- **Design question it examines:** What does "tailored" look like as an interface rather than a claim?

---

## 3. Feedback questions and what they predict

- **"What do you use to observe and give feedback to your students now, and what is annoying about it?"** — He walks around, sees only the *completed* weld, infers backwards from it, and ends up teaching general technique to the whole group. *Screen 3 rests on this:* close observation of one weld means he is no longer forced to be general.
- **"What would have to be true for you to use a different solution for observing your student’s welds and giving personalized feedback instead of what you do now?"** — A big class, plus many students struggling in visibly different ways. *Screen 2 rests on this:* many welds at once, in one manageable set.
- **"Who else do you know who deals with a large welding class and not enough time and space to get around and observe the specifics of each student learning to weld?"** — Very common among welding teachers at large schools; he meets them at conferences. *The vocabulary rests on this:* "class," "student," "station," "bay" — written for this exact role, not generic "users."
- **"Click around and tell me what this is for."** — "Watching streams of students doing welds with technology in place to give timestamped feedback." *Rests on:* the landing headline plus the literal button labels **View this weld** and **Comment at this moment**.

---

## 4. Your design justification and first read

Opened cold, as a stranger:

- **Does the landing screen signal the capability and value before reading?** Mostly yes — the largest element is a live weld-cam POV with a blinking LIVE / STATION 06 chip, so "someone is watching a weld through a camera" arrives pre-verbally. The headline then names the pain ("Watch a whole class weld at once") and the subhead names the capability. Figure/ground does the work: one bright arc on a dark plate against an otherwise quiet warm-white page.
- **Does every element earn its place?** Yes, after pruning. The page is a single visual, headline, subhead, one filled CTA, one text-link sign-in. Nothing competes with Get Started: it's the only saturated fill on the screen, and sign-in is deliberately demoted to type-only, using visual hierarchy rather than two equal buttons.
- **What belongs together, and which Gestalt principle says so?**
  - *Dashboard tiles:* **similarity** — identical size, shape, and internal layout make 16 feeds read as one scannable set, matching "scan the class."
  - *Tile internals:* **proximity** and **common region** — feed, name, station, and **View this weld** sit inside one bordered card, so the button unmistakably belongs to *that* feed.
  - *Timeline markers:* **proximity** — each diamond and its timestamp sit directly under the moment it refers to, so a comment reads as attached to a point in the weld, not to the video as a whole.
  - *Composer:* **enclosure** — the open text box is ringed in a heavy dark border with a "New comment at 00:42" header, binding the typed words to that timestamp.
- **Do screens 2 and 3 stay on mission, and can you get home from everywhere?** Yes. Screen 2 shows only what's needed to scan (feed, who, where, live status) — no vanity metrics. Screen 3 gives the video the majority of the canvas and keeps all feedback on the right rail. Home is reachable from every screen via the ARCVIEW wordmark, and screen 3 additionally has the back arrow to the dashboard.
- **What did the AI get wrong, and what changed?** The first mockup had no way back to the landing screen. Screen 3 had a back arrow to the dashboard, and screen 2 had a dead, non-clickable wordmark — so the landing screen was a one-way door. This took several iterations to get right: first pass made the wordmark clickable but labeled it "ARCVIEW Home," which was redundant *and* sat in a different position on each screen (second item on screen 3, first on screen 2), so the control appeared to move as you navigated. Final pass: the wordmark chip is the first item in the header on both screens, identical in size and position, with the same orange underline it has on the landing page — so it's positionally stable and reads as a home affordance without a label.
- **Which design question motivated each change?** The home-navigation work came from the *wayfinding/consistency* question — a control that changes position between screens breaks the user's spatial model, and an unlabeled logo only works if it's stable and always in the same slot. 

### Before / after (one concrete comparison)

| | Before (initial mockup) | After (revised) |
|---|---|---|
| **Problem** | Landing was a terminal state in reverse: screens 2 and 3 offered no path back to it. The only home-ish element — the ARCVIEW wordmark — was inert on screen 2, and on screen 3 the single arrow went to the dashboard only. | The wordmark is a real control, first item in the header, same position and size on screens 2 and 3, carrying the landing page's orange underline as its signifier. |
| **Named in course vocabulary** | A **missing signifier**: the wordmark *looked* like a logo, not a control, so its affordance was invisible — and the nav control's position was **inconsistent between screens**, breaking the user's mental model of where "home" lives. | Consistent placement plus a borrowed visual signifier (the underline) makes the affordance discoverable without adding a "Home" label that would duplicate the mark's meaning. |

> Replace this row with screenshots or a link to the initial commit beside the revised header: `git log` → first commit of `Arcview.dc.html` vs. current `HEAD`.

---

## Running it

`Arcview.dc.html` is a self-contained design component — open it in a browser. The demo header chip (Screen 1 / 2 / 3) jumps between screens; it can be hidden via the component's `showDemoNav` prop, alongside `classSize` and `liveOnly`.
