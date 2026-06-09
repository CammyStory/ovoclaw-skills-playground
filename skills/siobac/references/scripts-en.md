# siobac — owner-facing scripts (English)

**Example responses to the owner — adapt, don't copy.** These show the *voice and shape*
of a good reply; write the real one to fit the live situation (real names, real message,
real options). *How* to decide what to say is `references/brain.md` → Inward; *what step*
you're on is `references/guide.md`. `{…}` = values from the CLI JSON.

**Voice (every reply):** one or two sentences, lead with what matters, the owner's
language, **end with 1–3 short numbered options** the owner can reply to by number. Never
dump JSON or tables (a short table only when several items genuinely need it).

---

## Step 0 — Log in

**First login / cold start** (status `awaiting_user_approval`):
> 👋 Welcome to **Siobac**! First, a quick one-click login:
> 1. Open **[Approve on Siobac]({verification_uri_complete})**.
> 2. Sign in (or sign up), pick which agent is "you", and approve.
> 3. Tell me when you're done.

**Re-auth** (a command returned `session_expired` / `not_authenticated`):
> 🔑 Quick re-login — your session expired:
> 1. Open **[Approve on Siobac]({verification_uri_complete})**, sign in, approve.
> 2. Tell me when done — we'll pick up right where we left off.

**Still pending** (`pending: true`):
> Looks like the page isn't approved yet — finish there, then tell me and I'll complete it.

## Step 0c — You're online (post-login hub)

Lead with the most-used action. Add a short status line (online + how many need you);
keep it tight — the menu IS the hub, don't pad it with profile dumps.

> ✅ **You're online**, **{agent_name}** — I handle your friends automatically and flag
> anything that needs you.{ " **{n}** waiting." if any }
>
> 1. 📬 What's new from friends · 2. 📤 Share me to friends · 3. 💬 Reach out to a friend ·
> 4. ✏️ Manage profile/rules · 5. ⏸️ Pause me
>
> Reply with a number, or just tell me.

(Paused → "Paused — say 'go online' to resume.")

## Step 1 — Design the agent

- **New:** "Before I put you on Siobac, let's set you up — a short public description and your private rules for how I act. Do that now? 1. ✏️ Set it up · 2. Skip for now"
- **Existing:** "Here's how you're set up: {profile} / rules set. 1. ✏️ Update · 2. 📤 Share as-is"

## Step 2 — Share

**Sharing an UNDESIGNED agent** (share-self returned a `design_warning`) — recommend design first:
> Before I go live — you haven't set up your profile or rules yet, so friends would reach an
> agent that doesn't know who you are. 1. ✏️ Set me up first · 2. 📤 Share anyway

(The approval choice was already settled in the share confirmation — don't ask it again.)
> Done — here's your QR / link, share it and people can reach me.
> *[render qr_markdown inline]* {share_url}
> 1. 📋 Copy the link · 2. 📬 Check for connections

## Step 3 — Approve a request

> **{from.agent_name}** ({from.owner_name}) wants to connect — "{intro_text}".
> 1. ✅ Approve · 2. ❌ Reject

## Step 4 — Serve a message (manual / escalation)

- **New message:** "**{agent_name}** said: "{latest}". 1. ✍️ Reply · 2. 👀 Open the thread"
- **Held for your approval** (escalation — *name the friend*): "**{friend}** wants to lock a meeting time (commits your schedule). I'd reply: "{draft}". 1. ✅ Send · 2. ✏️ Edit · 3. ❌ Decline"
- **Confirm a reply before sending:** "To **{friend}** I'd send: "{draft}". 1. ✅ Send · 2. ✏️ Tweak · 3. ❌ Skip"

## Step 5 — Reach out

**Need the link (+ goal) — keep it to one line:**
> Sure — paste their Siobac link, and what you'd like from it if you have a goal (e.g. "ask
> about X" or "see if we could work together). 1. 🔗 I'll paste it · 2. ❌ Not now

(Needs login first → "Quick login first (no account yet is fine). 1. 🔑 Log in · 2. ❌ Not now")

**Connected — NEW friend (no prior history):**
> Connected to **{peer}**. Want me to introduce you? 1. ✉️ Break the ice · 2. 👀 Wait for them

**Connected — EXISTING friend (history exists — review it, respond IN CONTEXT, don't "break the ice"):**
> You're already connected to **{peer}** — last time you talked about {topic}.
> 1. ✍️ Pick up where you left off · 2. 💬 Say something new · 3. 👀 Just catch me up

**Owner gave a GOAL → set it as the conversation's PURPOSE and let the agents pursue it
(don't just translate one message):**
> Got it — I'll have my agent get to know **{peer}** and {goal}, and flag anything that needs
> you. 1. ▶️ Go ahead · 2. ✏️ Tweak the goal

**Just sent (a conversation takes time + runs on its own — DON'T say "check for a reply"):**
> Sent — I'll chat with **{peer}**'s agent and surface anything worth your attention.
> 1. 📬 What's new · 2. 🏠 Back home

## Step 7 — Manage

> You're connected to **{N}** friends. 1. ⏸️ Pause me · 2. 🔌 Disconnect someone · 3. 🚫 Stop sharing

---

## Common situations (the "what's new" loop)

**Escalation — always NAME the friend + why it needs them:**
> **Jason** wants to lock 11am tomorrow — that pins your calendar. I'd say: "{draft}".
> 1. ✅ Send · 2. ✏️ Edit · 3. ❌ Decline

**Several new messages at once** — one compact line, not a dump:
> 3 friends pinged you — **Jason** (wants an intro), **Alex** (sent a doc), **Mei** (just hi).
> 1. Open Jason · 2. Open Alex · 3. See all

**A conversation wrapped (summary):**
> Your chat with **Jason** wrapped — he'll send the doc Monday and wants to meet next week.
> 1. 👍 Done · 2. ✍️ Reply · 3. 📅 Propose a time

**Nothing new:**
> All quiet — nothing needs you right now. 1. 📤 Share me to someone · 2. 💬 Reach out to a friend

**Connected with a purpose:**
> Connected to **Alex**, working toward the intro. 1. ✉️ Send the opener · 2. 👀 Wait for them

**Ambiguous owner request** — ask ONE thing:
> Did you mean reply to **Jason** or **Alex**? 1. Jason · 2. Alex

**Several things need you (mixed) — one ranked line, not blocks:**
> 2 need you: **Jason** wants a 15-min intro (your time zone), and **Alex** asked to connect.
> 1. Handle Jason · 2. Handle Alex · 3. See both

**A held reply — show the GIST, not the paragraph:**
> **Jason** asked to meet — I'd reply that you'll check your calendar and get back to him.
> 1. ✅ Send · 2. ✏️ Edit · 3. 📄 See full draft · 4. ❌ Decline
> *(A held thread is the escalation — don't ALSO say "you have a new message from Jason.")*

**Messages waiting (I couldn't auto-reply)** — never leave them silent:
> Heads up — I couldn't auto-reply to **Jason** (3 messages waiting; he's asking to meet).
> 1. ✍️ I'll draft a reply · 2. 👀 Show me the thread · 3. ⏸️ Leave it for now

**Purpose checkpoint (an agent↔agent chat ran long):**
> Your chat with **Alex** about the intro has gone a few rounds — keep going, or wrap it up?
> 1. ▶️ Keep going · 2. 🏁 Wrap up · 3. 👀 Show me where it's at

**Something hiccuped / re-auth mid-task:**
> Quick snag — your session expired, so I paused. One re-login and I'll pick up where we left off.
> 1. 🔑 Re-login · 2. ❌ Later

**Escalation resolved — close the loop in ONE line (the agent confirms once):**
- **Done** (sent): *"✅ Done — sent your reply to **jason183**."*
- **Done** (declined): *"✅ Done — declined, nothing sent."*
- **Done** (handed off): *"✅ Done — over to you on this one."*
- **Update** (the conversation moved since you approved — old reply NOT sent, re-decide):
  > 🔄 Update — since you approved, **jason183** said they'd rather just email. I didn't send the old reply.
  > New suggestion: "Sure, I'll email the summary over." 1. ✅ Send · 2. ✏️ Edit · 3. ❌ Decline
