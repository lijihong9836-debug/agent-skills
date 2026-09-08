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
| [`ask-matt`](skills/ask-matt/) | Navigate Matt Pocock's engineering and productivity workflows. |
| [`code-review`](skills/code-review/) | Review changes against repository standards and the originating spec. |
| [`craft-codex-prompts`](skills/craft-codex-prompts/) | Draft, review, and optimize agent-facing prompts for Codex. |
| [`credit-negative-monitoring`](skills/credit-negative-monitoring/) | Apply evidence, listing, writeback, and workbook quality rules for credit monitoring. |
| [`credit-negative-search-flow`](skills/credit-negative-search-flow/) | Search or match DM evidence by subject and month, reconcile sources, and hand off verified updates. |
| [`domain-modeling`](skills/domain-modeling/) | Maintain shared domain language, CONTEXT.md, and architecture decisions. |
| [`handoff`](skills/handoff/) | Write a portable handoff for another agent session. |
| [`implement`](skills/implement/) | Implement a scoped ticket or spec through a complete vertical slice. |
| [`karpathy-guidelines`](skills/karpathy-guidelines/) | Keep coding work simple, surgical, and verifiable. |
| [`pdf`](skills/pdf/) | Read, create, and review PDFs with rendering and visual checks. |
| [`setup-matt-pocock-skills`](skills/setup-matt-pocock-skills/) | Configure issue tracking and domain documentation for engineering workflows. |
| [`storage-analyzer`](skills/storage-analyzer/) | Produce a safe, read-only storage analysis with recoverable cleanup options. |
| [`to-spec`](skills/to-spec/) | Turn an agreed conversation into a project specification. |
| [`to-tickets`](skills/to-tickets/) | Split a plan or spec into dependency-aware implementation tickets. |
| [`wayfinder`](skills/wayfinder/) | Resolve a large effort through a shared map of decision tickets. |
| [`writing-for-agents`](skills/writing-for-agents/) | Write predictable agent instructions, skills, and referenced documents. |
| [`磨刀石`](skills/磨刀石/) | Challenge and refine ideas while preserving the user's judgment and cognitive friction. |

Selected high-frequency third-party mirrors and their source/license status are documented in [docs/third-party-skills.md](docs/third-party-skills.md).

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

Install `credit-negative-monitoring` and `credit-negative-search-flow` together for the complete credit evidence workflow. Their `tools/` references describe optional integrations in the target business project; the Skills include the rules and reference documents.

The Matt Pocock entries are selected mirrors. Their workflow references may require additional Skills from the [upstream collection](https://github.com/mattpocock/skills); this repository does not bundle the entire upstream suite.

Agents may also reference a Skill directly from a checked-out path when testing or reviewing it.

## Directory and naming conventions

- Put distributable Skills under `skills/<skill-name>/`.
- Use lowercase hyphen-case for new English folder names and the `name` field; preserve the upstream name `磨刀石` for that existing mirror.
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
