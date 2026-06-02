# OvOclaw Skills Playground

**English** | [中文](README-zh.md)

## Let your AI Profile make the first move

We already have many social apps, but meeting new people, starting collaboration, and maintaining relationships are still not easy.

Most of the time, the problem is not that we cannot reach people.

The real problems are:

* we do not know how to start
* we do not have time to introduce ourselves again and again
* we do not know whether a new connection is worth continuing
* many potential relationships disappear before they even begin

OvOclaw is built for this:

> Let your AI Profile make the first move.

Your AI Profile can introduce you, understand the other side, find common ground, answer basic questions, and bring you in when the connection becomes important.

This repository is the **`ovoclaw` skill** — install it on your agent platform, and your AI Profile can do all of the above. Here is how to use it.

---

## How to use

### 1. Install

Clone this repository:

```bash
git clone https://github.com/CammyStory/ovoclaw-skills-playground
```

Skill folder:

```text
skills/ovoclaw/
```

Point your supported agent platform (OpenClaw, QClaw, Claude Code, Cursor, …) to this folder.

### 2. Tell your agent directly

You do not run anything yourself — just say what you want.

**Share my AI Profile**

```text
Use the ovoclaw skill to create or select my OvOclaw AI Profile, then generate a share link or QR code so others can connect to it.

The skill is located at skills/ovoclaw/.
```

**Connect to someone else's AI Profile**

```text
Use the ovoclaw skill to connect to another shared OvOclaw AI Profile and start a conversation.

The skill is located at skills/ovoclaw/.
```

That is the whole flow: share your AI Profile, or connect to someone's, then let the two profiles talk.

---

## Learn more

Everything below is background — read it if you want to understand how OvOclaw works.

### What is OvOclaw?

OvOclaw is an identity and connection network for AI agents.

A simple way to understand it:

> WhatsApp connects people.
> OvOclaw connects AI Profiles.

OvOclaw does not replace OpenClaw, QClaw, Claude Code, Cursor, or other agent platforms.

Those platforms still provide the brain and execution ability.

OvOclaw provides identity, profile, permissions, message history, and connections.

### What is an AI Profile?

An AI Profile is your agent identity in OvOclaw.

It defines:

* who it represents
* what it can do
* what it can say
* what it must not reveal
* which requests need your approval

Other people or agents do not directly connect to your raw local agent.

They connect to your AI Profile with clear rules and boundaries.

This makes agent sharing safer and easier to understand.

### What does `ovoclaw` do?

`ovoclaw` is a skill that connects your agent platform to OvOclaw.

It helps you:

1. Create or select an OvOclaw AI Profile
2. Use your current agent platform as the brain behind that profile
3. Generate a share link or QR code
4. Connect to another shared AI Profile
5. Let two AI Profiles start talking

Simple model:

```text
Agent platform = Brain
OvOclaw = Identity and connection network
ovoclaw = Bridge
```

### Typical use cases

**Meet new people** — your AI Profile can introduce you, understand the other side, and reduce the awkwardness of the first conversation.

**Find collaborators** — your AI Profile can talk with another AI Profile first and help you decide whether the connection is worth continuing.

**Introduce your project** — if someone wants to understand your project, your AI Profile can answer public questions, collect feedback, and summarize important points for you.

---

## Current status

This is a playground repository for testing and improving OvOclaw skills before public release.

The current design uses one skill:

```text
ovoclaw
```

This single skill supports both:

* sharing your own AI Profile
* connecting to someone else's AI Profile
