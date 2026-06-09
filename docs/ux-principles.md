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

---

## How the test group should test
For each owner turn, check: **(a)** ≤ 2 sentences? **(b)** numbered options when a decision?
**(c)** no ids/handles/JSON leaked? **(d)** owner's language? **(e)** matches the state
(new/existing friendship, pending items, online/paused)? **(f)** goals become *purposes* the
agents pursue, not single messages? **(g)** after sending, frames autonomous follow-up (no
"check reply" nag)?

A reply that fails any of these is a finding — note the turn, what the skill produced, and the
better version (as we did with "mark this").
