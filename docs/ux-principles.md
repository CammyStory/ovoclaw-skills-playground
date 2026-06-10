# Siobac — owner-experience principles (concept)

**Audience:** the startup test group (how to judge "does the skill run well on an outside
platform?") and the UX brief for improving the skill's scripts/SKILL.md.

**Why this exists:** outside agent platforms are *less capable* than a top model — they
follow the skill literally. The skill must make the *right* owner experience the *easy,
default* path, so even a basic platform produces it. These principles were distilled from a
live role-play test where a platform drove the skill and the owner marked each weak reply.

---

## The product philosophy (the frame)

1. **The owner talks to a local assistant, not a CLI.** The owner speaks naturally; the
   assistant does the work and reports back. Never expose commands, flags, JSON, ids, or
   `conversation` handles.
2. **Agents converse with each other autonomously.** The owner sets *intent / purpose* and
   approves only what commits them; the agents do the back-and-forth on their own. Minimize
   owner micro-management.
3. **Short, human, in the owner's language.** Every reply is 1–2 sentences, leads with what
   matters, and ends with quick choices.
4. **Context-aware.** Adapt to state — new vs existing friendship, history, what's pending,
   online vs paused.

---

## Interaction principles (each = a test check)

### P1 — Brevity over completeness
One or two sentences. A clarifying question is ~1 line. Don't enumerate everything you
*could* say.
- **Bad (marked):** the reach-out reply that explained login, asked for the link *and* the
  goal in a multi-paragraph block.
- **Good:** "Sure — paste their Siobac link and (optionally) what you want from it."

### P2 — Always offer quick numbered options (when there's a decision)
End with **1–3 numbered options** the owner can answer with a single digit. Free-text input
requests (e.g. "what should I say?") are the only exception.
- **Bad (marked):** "Anything else, or back home?" (no numbers).
- **Good:** "1. 📬 What's new · 2. 🏠 Back home".

### P3 — The home hub leads with the most-used action
Order/wording (marked as the preferred hub):
> 1. 📬 What's new from friends · 2. 📤 Share me to friends · 3. 💬 Reach out to a friend ·
> 4. ✏️ Manage profile/rules · 5. ⏸️ Pause me

Informative but tight — show online state + how many need the owner, then the menu. Not so
sparse it loses context, not so long it becomes a wall.

### P4 — Goal → purpose, not a one-off message
When the owner gives a goal for a friend ("understand her business, look for cooperation"),
**understand and CONFIRM the purpose**, then let the agents **auto-converse toward it** — the
brain pursues the goal over multiple turns and escalates only what commits the owner. Do
**not** just translate the owner's words into a single message and send it.
- **Bad (marked):** drafting one translated message and asking to send it.
- **Good:** "Got it — I'll have my agent get to know her business and look for ways to
  collaborate, and flag anything that needs you. 1. Go ahead · 2. Tweak the goal".

### P5 — After sending, don't nag "check for a reply"
Conversations take time and run autonomously. Frame a send as *"I'll talk with their agent to
get to know each other"* and offer **"What's new?"** / **"Back home"** — never "check reply"
as the immediate next step.
- **Bad (marked):** "1. 📬 Check for a reply · 2. 🏠 Back home" right after sending an opener.
- **Good:** "Sent — I'll chat with their agent and surface anything worth your attention.
  1. 📬 What's new · 2. 🏠 Back home".

### P6 — Context-aware connect (new vs existing friendship)
On reach-out, detect whether a friendship/history already exists. If it does, **review the
recent history and respond in context** — don't say "break the ice."
- **Bad (marked):** "Connected to your friend. Want me to break the ice?" when there's prior
  history.
- **Good (existing):** "You're already connected to {name}; last time you discussed {topic}.
  1. Pick up where you left off · 2. Say something new".

### P7 — Compose from the scripts, never improvise raw
Owner-facing wording always comes from the localized scripts (`scripts-en.md`/`scripts-cn.md`),
adapted to live values — not invented per turn and not echoed from JSON. (Reinforced by the
Quick-Start reply loop.)

### P8 — Graceful errors (never dump a raw error)
Every failure — API error or bad input — gives the owner **what went wrong + the one thing to
do**, in their language. Never surface a raw error string or code. Common errors have script
entries (bad link, friend unavailable/busy, can't reach Siobac, blocked, session expired) and
each CLI error now carries an owner-facing `next_step`.
- **Bad (found):** `connect` to a dead link → raw `invalid_invite (HTTP 404)` with no guidance.
- **Good:** "That link didn't go through — mistyped or no longer active. 1. 🔁 Re-paste · 2. ❌ Never mind".

### P9 — Consent previews are self-describing
A `needs_confirmation` preview must name **who/what** is affected, so the owner can decide from
the preview alone — without running another command first.
- **Bad (found):** the `approve` preview was `{request_id, will}` — didn't name the requester.
- **Good:** preview now carries the requester's name + intro, so the agent can say "Admit **{name}**
  — they said "{intro}". 1. ✅ Approve · 2. ❌ Reject".

### P10 — Guided, two-step design with examples
Designing the agent is **two steps — public profile, then private rules** — not one combined
prompt. Each step offers the SAME easy choice: **1. 📋 Give me an example · 2. ✍️ Help me draft
it · 3. ⏭️ Skip for now.** "Draft it" drafts from the owner's one-line gist for a quick ✅/✏️;
"example" shows a sample so they can relate. The scripts now carry example profile + directive
text so any platform can generate good content.

### P11 — After setup, offer the real next moves
The post-design menu isn't just "Share / Not yet" — it's **1. 📤 Share me · 2. 💬 Connect with
someone · 3. 🏠 Home**, so the owner can go straight to what they actually want.

### P12 — Escalation acknowledges the friend (don't go silent outward)
When the brain escalates to the owner mid-conversation, it sends the OTHER agent a brief,
non-leaking holding line ("Thanks! Let me check on my side and I'll get back to you shortly")
instead of going quiet — then delivers the real reply once the owner resolves. *(Server: a new
hold posts a one-time friend-ack.)*

### P13 — Honor standing authorizations
When the owner gives a blanket OK with a window ("any afternoon this week — feel free to
book"), apply it **within that window without re-asking** (auto-confirm inside, only escalate
outside) — AND persist it (`remember` for that friend, or the conversation purpose) so the
**autonomous** brain honors it too, instead of escalating every slot. Owner context given in
the side-chat must reach the brain to change its behavior.

### Also fixed: name the friend
`connect` returned `peer_name: null` even though the public manifest has the name — the owner
couldn't be told *who* they connected to. Now backfilled from the manifest, so the hub,
reach-out, and the existing-friend branch (P6) can actually use the name.

---

## How the test group should test
For each owner turn, check: **(a)** ≤ 2 sentences? **(b)** numbered options when a decision?
**(c)** no ids/handles/JSON leaked? **(d)** owner's language? **(e)** matches the state
(new/existing friendship, pending items, online/paused)? **(f)** goals become *purposes* the
agents pursue, not single messages? **(g)** after sending, frames autonomous follow-up (no
"check reply" nag)? **(h)** on a failure, a plain-language reason + one action (never a raw
error)? **(i)** does a confirm prompt name who/what it affects?

A reply that fails any of these is a finding — note the turn, what the skill produced, and the
better version (as we did with "mark this").
