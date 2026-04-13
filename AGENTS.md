# AGENTS.md

**Document ID:** `acp_project_workspace_agents_template`
**Version:** `v1.0.0`
**Status:** `Working Draft`
**Class:** `Distribution Template`
**Authority:** `ACP compilation layer — distributable workspace template`

---

## Purpose

This file is a **distributable template** for the `AGENTS.md` that should be
placed at the root of an ACP-managed application project workspace.

When distributing ACP to a new project, copy this file to:

```
project/AGENTS.md
```

Then fill in the `[placeholders]` with project-specific values.

---

## Template

---

# AGENTS.md

This workspace contains an ACP-managed application.

```
project/
├── AGENTS.md                  ← this file
├── acp-protocol/              ← ACP consumer package (read-only)
│   ├── acp_agent_playbook.yaml
│   ├── ACP_PUBLIC_DRAFT.md
│   ├── templates/
│   └── host/
└── src/                       ← application source
    ├── .acp/                  ← application ACP state
    │   ├── version.yaml
    │   ├── kernel/
    │   ├── support/
    │   └── capability/
    └── (source code)
```

## Protocol

ACP behavioral instructions are in `acp-protocol/acp_agent_playbook.yaml`.

Load this file at bootstrap before broad repository exploration.

`acp-protocol/` is read-only. Do not modify its contents.
Do not treat `acp-protocol/` as project state — it is the protocol consumer package.

## Application ACP State

The application's ACP state is in `src/.acp/`.

Entry point: `src/.acp/version.yaml`

When ACP is active:

1. Read `src/.acp/version.yaml`
2. If support is enabled, read `src/.acp/support/AGENT.md`
3. Follow staged intake — do not begin with broad `src/` scanning
4. Use `Request → Plan → Change` for all mutation-oriented work

## Working Rules

- `acp-protocol/` is protocol authority for this workspace. Treat it as read-only.
- `src/.acp/` is project state. It describes the application, not the protocol.
- Do not conflate protocol rules with project-local support guidance.
- Do not scan `src/` broadly before ACP intake is established.
- Do not create host-specific adapter directories (`.opencode/`, `.codex/`) inside
  `src/` unless explicitly requested.

## Constraints

- Protocol authority: `acp-protocol/acp_agent_playbook.yaml`
- Project state authority: `src/.acp/version.yaml`
- Mutation work: governed by `Request → Plan → Change` in `src/.acp/kernel/`
- Broad scanning: deferred until ACP intake and capability routing are established
