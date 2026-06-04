# Agent Registry

This registry documents the packaged GodMode agents installed by `./scripts/apply-global-codex-setup.sh`.

Source files live under `templates/global-codex/agents/` so this bootstrap repository does not expose duplicate project-local agents after the same runtime is installed globally.

Packaged agents pin their model and reasoning effort in the source TOML manifests. Classification and implementation run on `gpt-5.5` / `high`; most governance, utility, validation, and advisory roles run on `gpt-5.4` or `gpt-5.4-mini` with `medium` reasoning.

## Phase 1 agents

| Step | Route | Source | Model pin | Purpose |
| --- | --- | --- | --- | --- |
| 1 | `workspace_governance` | `templates/global-codex/agents/workspace_governance.toml` | `gpt-5.4` / `medium` | workspace shape and governance-surface inspection |
| 2 | `$greenfield-bootstrap` | `templates/global-codex/skills/greenfield-bootstrap/SKILL.md` | Tier 3 behavior | missing repo-local governance bootstrap |
| 3 | `task_classifier` | `templates/global-codex/agents/task_classifier.toml` | `gpt-5.5` / `high` | task classification and smallest-viable-team routing |
| 4 | `preflight_runner` | `templates/global-codex/agents/preflight_runner.toml` | `gpt-5.4-mini` / `medium` | deterministic preflight checks and workflow-state initialization |
| 5 | `researcher` | `templates/global-codex/agents/researcher.toml` | `gpt-5.4-mini` / `medium` | source verification and repo discovery when more evidence is needed |

## Core agents

| Agent | Source | Model pin | Purpose |
| --- | --- | --- | --- |
| `researcher` | `templates/global-codex/agents/researcher.toml` | `gpt-5.4-mini` / `medium` | read-only source verification, repo discovery, and problem framing |
| `architect` | `templates/global-codex/agents/architect.toml` | `gpt-5.5` / `high` | read-only design, interfaces, risks, and smallest viable change plan |
| `api_guardian` | `templates/global-codex/agents/api_guardian.toml` | `gpt-5.4` / `medium` | read-only API, schema, CLI, config, and contract-surface review |
| `builder` | `templates/global-codex/agents/builder.toml` | `gpt-5.5` / `high` | implementation-focused writer for the smallest safe change |
| `validator` | `templates/global-codex/agents/validator.toml` | `gpt-5.4` / `medium` | read-heavy structural, static, and consistency validation |
| `tester` | `templates/global-codex/agents/tester.toml` | `gpt-5.4` / `medium` | focused executable checks and runtime verification |
| `scribe` | `templates/global-codex/agents/scribe.toml` | `gpt-5.4-mini` / `medium` | docs, changelog, and release-note work after quality gates pass |
| `github_manager` | `templates/global-codex/agents/github_manager.toml` | `gpt-5.4-mini` / `medium` | branch, PR, release, and repository-governance framing |

## Department agents

| Agent | Source | Model pin | Purpose |
| --- | --- | --- | --- |
| `runtime_platform` | `templates/global-codex/agents/runtime_platform.toml` | `gpt-5.4` / `medium` | runtime defaults, toolchains, sandboxing, and environment behavior |
| `workflow_design` | `templates/global-codex/agents/workflow_design.toml` | `gpt-5.4` / `medium` | workflow procedures, skill boundaries, and handoff artifacts |
| `workspace_governance` | `templates/global-codex/agents/workspace_governance.toml` | `gpt-5.4` / `medium` | workspace shape, AGENTS layering, release law, branch policy, and repo rules |
| `quality_operations` | `templates/global-codex/agents/quality_operations.toml` | `gpt-5.4` / `medium` | validation plans, install checks, smoke paths, and eval-oriented checks |
| `docs_dx` | `templates/global-codex/agents/docs_dx.toml` | `gpt-5.4-mini` / `medium` | README, setup docs, prompts, and contributor-facing clarity |
| `ci_security_guardian` | `templates/global-codex/agents/ci_security_guardian.toml` | `gpt-5.4` / `medium` | GitHub Actions, CODEOWNERS, pinned actions, and repository security posture |

## Installed count

- Core agents: 8
- Department agents: 6
- Phase 1-only agents: 2
- Total packaged agents: 16

Run `./scripts/check-local-env.sh` to verify the package sources and `./scripts/apply-global-codex-setup.sh --check` to verify the installed global runtime.
