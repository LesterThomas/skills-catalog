# skills-catalog

A catalog of reusable [Agent Skills](https://docs.github.com/en/copilot) for GitHub Copilot. Each skill lives under `.github/skills/` as a self-contained folder with a `SKILL.md` that describes when and how it should be used, plus any bundled scripts, references, or assets it needs.

## What's inside

| Skill | Description |
| --- | --- |
| [`skill-creator`](.github/skills/skill-creator) | Meta-skill for creating new skills and iteratively improving them: drafting a `SKILL.md`, writing test prompts, running evaluations, reviewing results, and optimizing the skill's triggering description. Includes helper scripts (`scripts/`), subagent instructions (`agents/`), reference docs (`references/`), and an HTML eval viewer (`eval-viewer/`). |
| [`doc-coauthoring`](.github/skills/doc-coauthoring) | Guides users through a structured, three-stage workflow (Context Gathering, Refinement & Structure, Reader Testing) for co-authoring documentation such as proposals, technical specs, and decision docs. |
| [`readme-updater`](.github/skills/readme-updater) | Creates or updates a repository's `README.md` with an accurate summary of the repository's actual contents, based on exploring the repo rather than using a generic template. Includes example test prompts under `evals/`. |

## Structure

```
.github/skills/
├── skill-creator/      # Create and iterate on new skills
├── doc-coauthoring/    # Structured documentation co-authoring workflow
└── readme-updater/     # Keep a repo's README in sync with its contents
```

## Contributing a new skill

Use the `skill-creator` skill to draft, test, and refine a new skill, then add it to `.github/skills/` following the same layout as the existing skills (a `SKILL.md` at minimum, with optional `scripts/`, `references/`, and `assets/` subfolders).
