# Agent Skills for Non-Developers

*A short guide for architects and cybersecurity professionals*

## You don't need to write code to teach an AI agent something new

If you've used an AI coding assistant like GitHub Copilot, you may think of it as a tool for writing software. But Copilot is really a general-purpose *agent* — a system that can follow instructions, use tools, and carry out multi-step work. Increasingly, that includes work that has nothing to do with writing code.

**Agent Skills** are what make this possible without touching a line of code yourself.

A skill is a folder containing plain-language instructions — written in a file called `SKILL.md` — that tells an agent how to approach a particular kind of task. Think of it as a briefing document you'd hand to a new team member: what the task is, what steps to follow, what questions to ask, what "good" looks like. The agent reads it and follows it, the same way a person would follow a runbook or a checklist.

This format was originally introduced by Anthropic (the makers of Claude), and it's now supported directly in GitHub Copilot. That means the skills your organization builds aren't locked into one product — they're written once, in plain English, and can work across any agent that supports the standard.

Because a skill is just structured guidance, **anyone who can write a clear process can create one.** You don't need to be a developer. You need to be an expert in your domain.

## What agent skills are *not*

It's easy to assume a "skill" is a plugin, an integration, or a piece of software. It isn't:

- **It's not code.** A skill is instructions, written in Markdown — the same lightweight text formatting used in a Slack message or a wiki page.
- **It's not a one-off prompt.** A prompt is a single question you type once. A skill is reusable guidance that shapes how the agent behaves every time that kind of task comes up, and it can bundle multiple steps, questions, and reference material together.
- **It's not tied to one vendor.** Because the format is an open standard, a skill written for one Anthropic-format agent (like GitHub Copilot) is portable to other agents that support it too.
- **It's not a replacement for your judgment.** A skill guides the agent's process — checking assumptions, asking the right questions, following your organization's standards — but you still review and own the outcome.

In short: if you can describe *how* you'd want a capable junior colleague to approach a task, you can write a skill. The agent automatically recognizes when your request matches an available skill — you don't have to select it, install it, or configure anything.

## How you actually use a skill (no setup required)

Using a skill doesn't involve installing anything or writing a line of code. If a skill is available to your Copilot agent — meaning it exists somewhere Copilot can see, such as a shared repository (a shared project folder your team keeps in GitHub) — you use it simply by describing what you want to do in plain English, in the same chat window you'd normally use to ask Copilot a question.

For example, typing something like *"Help me write a decision doc about our new vendor selection"* is enough — Copilot recognizes that this matches the doc-coauthoring skill and starts following its guidance automatically, asking you the context questions described below. You don't need to name the skill, find a file, or configure anything first; you just describe your task like you would to a colleague. You'll know it's worked because the agent starts asking the kind of structured questions described in this guide, instead of just answering in one shot.

The same is true for a triage skill or an ADR skill: you'd start by asking the agent to do the task (*"triage this new AI use case for privacy and security risk"* or *"help me write an ADR for this decision"*), and the skill takes over from there, asking its questions and guiding the work. Skills aren't limited to one repository — any project that has the relevant skill available to its Copilot agent can use it the same way.

## How cybersecurity professionals are already using this

Consider a common challenge: your organization keeps proposing new AI use cases, and each one needs a consistent cybersecurity and privacy risk triage before it goes further. Doing this by hand is slow, and it's easy for the assessment to vary depending on who's doing it.

A **triage skill** solves this by encoding your team's process directly. Instead of starting from a blank page each time, an analyst can point the agent at a new AI use case and the skill guides the agent to:

- Ask the standard set of intake questions (what data is involved, who has access, where it's hosted, what decisions it influences)
- Apply your organization's risk classification criteria consistently
- Flag the specific privacy or security concerns that matter for that category of use case
- Produce a structured triage summary that's ready for review, in the same format every time

The security expertise still comes from your team — it's captured once, in the skill, by the people who understand the risk model. From then on, every triage benefits from that expertise being applied consistently, and analysts spend their time reviewing judgment calls instead of re-deriving the checklist from scratch.

## How architects are already using this

Architects spend a lot of time on artifacts that follow a known shape but require real thought to fill in well: API specifications, architecture decision records (ADRs), design reviews. The structure is well understood; the hard part is asking the right questions and capturing the reasoning clearly.

A skill can guide the agent through that process the way an experienced architect would mentor someone through it:

- **Writing an API specification** — the skill prompts for the resources, consumers, authentication approach, and versioning strategy, then helps produce a consistent, well-structured spec instead of a blank template.
- **Documenting an architecture decision record** — the skill walks through context, the options considered, trade-offs, and the final decision and rationale, so ADRs are complete and comparable across teams instead of depending on whoever happens to write them.

As with the security triage example, the skill doesn't replace the architect's expertise — it makes sure that expertise gets applied the same rigorous way every time, and it removes the friction of starting from nothing.

## Try it yourself: the doc-coauthoring skill in this repository

This repository includes a working example you can try right now: **doc-coauthoring**. It's a skill that guides you through writing a document — a spec, a proposal, a decision doc — in three stages:

1. **Context gathering** — the agent asks you questions to understand your topic, audience, and goals
2. **Refinement & structure** — the document is built section by section, with the agent brainstorming options and you curating what to keep
3. **Reader testing** — the finished doc is tested with a fresh, context-free agent to catch anything confusing before a real reader does

In fact, this very guide was produced using that skill — the questions you were asked earlier about audience, tone, and examples were the skill's context-gathering stage in action.

To try it yourself: open a Copilot chat in this repository and simply ask for what you want, for example *"Help me write a proposal for consolidating our vendor risk assessments."* Copilot will recognize the request matches doc-coauthoring and start asking you context questions, the same way this guide came together. If you want to see exactly what's guiding that conversation, the instructions themselves live at `.github/skills/doc-coauthoring/SKILL.md` — it's plain English throughout, no code required.

## Where to go from here

This guide focused on *using* existing skills. A future guide in this catalog will cover how to *write* your own — turning a process you already know well into a skill others on your team can reuse.

For now, the best next step is to explore this repository's catalog of skills, try the doc-coauthoring skill on a real document you need to write, and start thinking about which of your own repeatable processes — a triage checklist, a review process, a documentation format — might be worth turning into a skill next.
