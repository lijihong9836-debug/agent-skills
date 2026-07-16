# Agent Skills

A personal, public collection of reusable Skills for Codex and other compatible agents. Each Skill is self-contained, narrowly scoped, and maintained as an executable workflow rather than a prose article.

## Repository layout

```text
agent-skills/
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md
│       ├── agents/openai.yaml      # recommended UI metadata
│       ├── references/             # optional, loaded on demand
│       ├── scripts/                # optional deterministic helpers
│       └── assets/                 # optional output resources
├── docs/                           # repository-level design notes
├── .gitignore
├── LICENSE
└── README.md
```

## Available Skills

| Skill | Purpose |
| --- | --- |
| [`craft-codex-prompts`](skills/craft-codex-prompts/) | Draft, review, and optimize agent-facing prompts for Codex. |

## Install or reference a Skill

Install a single Skill with Codex's built-in installer:

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --url https://github.com/lijihong9836-debug/agent-skills/tree/main/skills/craft-codex-prompts
```

Or clone the repository and copy a Skill folder into the Codex Skills directory:

```powershell
git clone https://github.com/lijihong9836-debug/agent-skills.git
Copy-Item -Recurse .\agent-skills\skills\craft-codex-prompts "$env:USERPROFILE\.codex\skills\"
```

Start a new Codex task after installation if the Skill is not visible in the current task. Invoke it explicitly with `$craft-codex-prompts`, or let Codex select it when the description matches the request.

Agents may also reference a Skill directly from a checked-out path when testing or reviewing it.

## Directory and naming conventions

- Put distributable Skills under `skills/<skill-name>/`.
- Use lowercase hyphen-case for folder names and the `name` field.
- Keep the folder name identical to the `name` in `SKILL.md`.
- Require `SKILL.md`; include `agents/openai.yaml` when UI metadata is useful.
- Add `references/`, `scripts/`, or `assets/` only when they support the Skill at runtime.
- Keep repository-level rationale in `docs/`, not inside the distributable Skill folder.
- Do not commit credentials, private data, machine-specific absolute paths, generated secrets, or internal business artifacts.

## Maintenance rules

1. Keep each behavioral rule in one authoritative location.
2. Prefer short operational instructions and progressive disclosure over duplicated explanation.
3. Validate every Skill with Codex's `quick_validate.py` before publishing.
4. Run representative forward tests for behavior-changing revisions when practical.
5. Keep commits scoped to one Skill or one repository-maintenance concern.
6. Review staged files and scan for sensitive data before every push.

## License

Released under the [MIT License](LICENSE).
