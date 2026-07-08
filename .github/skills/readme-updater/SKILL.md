---
name: readme-updater
description: Create or update a repository's README.md with an accurate, up-to-date summary of what's in the repository. Use this whenever the user asks to write, generate, refresh, or fix a README, wants the README to reflect the current state of the repo, or mentions the README is outdated, missing, or doesn't describe the project properly. Also trigger when a user asks for a "project overview," "repo summary," or documentation describing what a repository/codebase contains, even if they don't say the word "README" explicitly.
---

# README Updater

This skill produces a README.md that accurately reflects the actual contents of a repository, rather than a generic template. The core idea: read the repository first, then write about what you find — don't guess or invent details.

## Why this matters

A README is often the first thing anyone (a teammate, a future maintainer, or the repo owner six months from now) reads to understand a project. A stale or generic README is worse than no README, because it actively misleads readers about what the repo contains. The goal here is a README that a newcomer could use to orient themselves in the repository within a minute or two.

## Workflow

### 1. Survey the repository

Before writing anything, explore the repository structure to understand what's actually there:

- Look at the top-level directory layout to understand the overall shape of the project (is it a single package, a monorepo, a collection of scripts, a documentation catalog, etc.)
- Identify the primary language(s)/ecosystem(s) in use (check for `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `*.csproj`, etc.)
- Look for existing documentation: any current `README.md`, `docs/` folder, `CONTRIBUTING.md`, or inline comments that explain intent
- Identify entry points and key components: main modules, CLI commands, notable subdirectories, config files
- Check for build/test/lint tooling (scripts in `package.json`, `Makefile`, CI workflow files under `.github/workflows/`) so you can document how to build/run/test the project if relevant
- If the repo has a clear theme (e.g., "a catalog of X" or "a library for Y"), note it — this becomes the core one-line description

Don't rely on assumptions from the repo name alone. Actually open key files to confirm what they do, especially if names are ambiguous.

### 2. Decide whether to create or update

- If no `README.md` exists at the repository root, create one from scratch.
- If a `README.md` already exists, read it fully first. Preserve any parts that are still accurate and valuable (e.g., licensing notices, contribution guidelines, badges, links to external resources) unless they're clearly outdated or contradicted by what you found in the repo. Update or rewrite only the parts that are stale, incomplete, or missing — don't discard useful existing content just to start clean.

### 3. Draft the summary

Structure the README to answer, roughly in order, the questions a newcomer actually has:

1. **What is this?** A short, clear description of the project's purpose (1-3 sentences, at the top, often paired with the project title).
2. **What's inside?** A summary of the repository's structure/contents — key directories, modules, or components and what each is for. This is the heart of the "summary of what's in the repository" the reader needs. Use a short list or table for multiple components rather than one long paragraph.
3. **How do I use/run it?** Only include setup, installation, or usage instructions if the repo actually contains runnable code, scripts, or tooling that warrants it. Don't invent install steps for a repo that's just documentation or a catalog of content.
4. **Anything else relevant?** Only if it exists and is worth mentioning: contribution guidelines, license, links to related resources.

Keep the tone factual and concise. Avoid marketing language ("revolutionary", "cutting-edge") and avoid padding sections with generic filler that isn't backed by something you actually found in the repo.

### 4. Write the file

Use the `create` or `edit` tool (or equivalent) to write the final `README.md` at the repository root. If updating an existing file, make targeted edits that preserve unrelated accurate content rather than replacing the entire file unless a full rewrite is genuinely warranted (e.g., the existing README is minimal, wrong, or badly out of date).

### 5. Sanity-check before finishing

Re-read the generated README against the actual repo contents:
- Does every directory/component mentioned actually exist?
- Are any claimed features, commands, or files real (not invented)?
- Is anything major in the repo missing from the summary?

If you find a mismatch, fix it before considering the task done.
