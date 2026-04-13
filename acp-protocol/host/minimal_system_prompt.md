# ACP Minimal System Prompt

**Document ID:** `acp_minimal_system_prompt`
**Version:** `v1.0.0-public-draft`
**Status:** `Research Draft`
**Class:** `Release / Publication File`
**Authority:** `ACP-PUBLIC host attachment guidance`
**Anchors:** `acp_host_adapter_model`, `acp_host_adapter_install`, `acp_runtime_bootstrap_spec`

---

## 1. Purpose

This document defines the minimal ACP-oriented prompt append that may be added to
a host system prompt or equivalent host configuration surface.

It is intentionally small.

It exists to:

- activate ACP when `.acp/version.yaml` is present
- route hosts toward `ACP-PUBLIC` as the consumer package
- avoid re-stating the full ACP corpus inside host-local configuration

---

## 2. Minimal Prompt Append

Recommended first-pass prompt append:

```text
If `src/.acp/version.yaml` exists, ACP is active. Load `acp-protocol/acp_agent_playbook.yaml` at bootstrap before broad repository exploration. Prefer staged intake and avoid repository-wide broad scanning by default. Treat `src/.acp/` as the project-state source. Treat `acp-protocol/` as the read-only protocol consumer package — do not modify it. Do not invent Request / Plan / Change object shapes. Use `acp-protocol/templates/` for new kernel objects. Treat mutation-oriented work as governed by Request -> Plan -> Change recorded in `src/.acp/kernel/`. When support or capability data exists in `src/.acp/support/` or `src/.acp/capability/`, use it for routing before broader scanning. In local-development mode, an open Change may temporarily omit `git_refs`, but a done Change must include `git_refs`. Treat host-local guidance as activation guidance only, not as protocol authority.
```

### Variant: flat layout (`.acp/` at project root)

If the project places `.acp/` directly at the project root rather than under
`src/`, use this variant instead:

```text
If `.acp/version.yaml` exists, ACP is active. Load `acp-protocol/acp_agent_playbook.yaml` at bootstrap before broad repository exploration. Prefer staged intake and avoid repository-wide broad scanning by default. Treat `.acp/` as the project-state source. Treat `acp-protocol/` as the read-only protocol consumer package — do not modify it. Do not invent Request / Plan / Change object shapes. Use `acp-protocol/templates/` for new kernel objects. Treat mutation-oriented work as governed by Request -> Plan -> Change recorded in `.acp/kernel/`. When support or capability data exists, use it for routing before broader scanning. In local-development mode, an open Change may temporarily omit `git_refs`, but a done Change must include `git_refs`. Treat host-local guidance as activation guidance only, not as protocol authority.
```

---

## 3. Use Constraints

This prompt append SHOULD:

- be appended to an existing host system prompt
- remain activation-oriented rather than explanation-heavy
- point the host toward package-local templates and validators

This prompt append SHOULD NOT:

- replace the host's full role and tool instructions
- duplicate large portions of ACP protocol or runtime prose
- hardcode one project path or one demo project

---

## 4. Relationship to Install Guidance

`host/install.md` should reference this file when a user or host wants a
copy-ready prompt append.

This file defines the reusable prompt text.
`host/install.md` defines how and where that text should be attached.
