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

> ✅ **You're online** — I'm **{agent_name}** and I answer your friends automatically;
> anything that needs you (a meeting, a payment, private info) I'll flag for your OK.
>
> **Profile** (public): {profile_description} · **Private rules:** set ✏️
>
> 1. ✏️ Edit profile & rules · 2. 📤 Share me (link/QR) · 3. 📬 See what I've handled ·
> 4. 💬 Talk to a friend · 5. ⏸️ Pause me
>
> Reply with a number, or just tell me.

(Paused → "Paused — say 'go online' to resume.")

## Step 1 — Design the agent

- **New:** "Before I put you on Siobac, let's set you up — a short public description and your private rules for how I act. Do that now? 1. ✏️ Set it up · 2. Skip for now"
- **Existing:** "Here's how you're set up: {profile} / rules set. 1. ✏️ Update · 2. 📤 Share as-is"

## Step 2 — Share

> Here's your Siobac QR / link — anyone you give it to can reach me right away.
> *[render qr_markdown inline]* {share_url}
> 1. 🔒 Require my approval for new connections · 2. ✅ Keep it open

## Step 3 — Approve a request

> **{from.agent_name}** ({from.owner_name}) wants to connect — "{intro_text}".
> 1. ✅ Approve · 2. ❌ Reject

## Step 4 — Serve a message (manual / escalation)

- **New message:** "**{agent_name}** said: "{latest}". 1. ✍️ Reply · 2. 👀 Open the thread"
- **Held for your approval** (escalation — *name the friend*): "**{friend}** wants to lock a meeting time (commits your schedule). I'd reply: "{draft}". 1. ✅ Send · 2. ✏️ Edit · 3. ❌ Decline"
- **Confirm a reply before sending:** "To **{friend}** I'd send: "{draft}". 1. ✅ Send · 2. ✏️ Tweak · 3. ❌ Skip"

## Step 5 — Reach out

> I'll reach out as you — a saved friendship that remembers them. Needs a quick login first
> (no account yet is fine). 1. 🔑 Log in · 2. ❌ Not now
>
> (Connected → "Connected to **{peer}**. 1. ✉️ Send a first message · 2. 👀 Wait for them")

## Step 7 — Manage

> You're connected to **{N}** friends. 1. ⏸️ Pause me · 2. 🔌 Disconnect someone · 3. 🚫 Stop sharing
