# Premium Addons for Elementor — Agent Skill

[![skills.sh](https://skills.sh/b/leap13/premium-addons-elementor-skill)](https://skills.sh/leap13/premium-addons-elementor-skill)

An [Agent Skill](https://agentskills.io) that teaches any MCP-connected AI agent to build well-designed WordPress pages through the Premium Addons for Elementor MCP.

> **Note:** This repository contains the AI Agent Skill, not the Premium Addons for Elementor plugin source code.

The MCP gives an agent **capability** — abilities it can call. This skill gives it **competence** — which ability to call, in what order, with what design judgment, and where to stop and ask.

## Requirements

| | |
|---|---|
| WordPress | with [Elementor](https://elementor.com) active |
| [Premium Addons for Elementor](https://premiumaddons.com) | free version is enough |
| PA dashboard | **Premium Addons → AI Abilities** enabled |
| Your AI client | connected to `https://your-site.com/wp-json/premium-addons/mcp` via OAuth |

Client registration only works for a short window after opening the AI Abilities tab — connect promptly after enabling.

## Install

**Claude Code / Cowork**

```bash
git clone https://github.com/leap13/premium-addons-elementor-skill.git \
  ~/.claude/skills/premium-addons-elementor
```

**skills.sh ecosystem**

```bash
npx skills add leap13/premium-addons-elementor-skill
```

**Any other runtime** — copy this folder into wherever that runtime loads skills from. `SKILL.md` and `references/` must stay together, with `references/` as a direct child.

## What's inside

```
SKILL.md                      core workflow, safety gates, ability index
references/
├── widget-selection.md       intent → widget map, free/PRO flags
├── global-addons.md          effect vocabulary → addon
├── page-patterns.md          section recipes
└── troubleshooting.md        connection, auth, permissions, renders-nothing
```

`SKILL.md` loads always; references load on demand.

## Posture

- **Zero network.** The skill makes no outbound requests. Everything it needs comes from the MCP connection you already authorized.
- **Zero scripts.** No executables, no build step, no postinstall. Execution belongs to the MCP.
- **Zero site data.** Nothing about your site is stored in these files. Site tokens, widget schemas, and design rules are fetched live from your own installation each session.
- **Drafts by default.** The skill never publishes, deletes, or changes site-wide settings without explicit approval in-conversation.

## Design judgment

Per-page design rules are **not** in this repository. They are served by your own site via the `premium-addons-get-design-guide` ability and version-matched to your installed plugin — one rulebook, kept current by the plugin. This skill defers to it and encodes only what the MCP cannot report about itself: sequencing, selection judgment, and boundary handling.

## Versioning

Semver, independent of the Premium Addons plugin version. Releases are cut when judgment content changes, not mechanically per plugin release.

## Issues and contributions

Bug reports and widget-mapping corrections are welcome via GitHub issues. Include the PA plugin version and the ability name involved.

## License

MIT — see [LICENSE](LICENSE).
