# Premium Addons for Elementor — Agent Skill

[![skills.sh](https://skills.sh/b/Leap13/premium-addons-elementor-skill)](https://skills.sh/Leap13/premium-addons-elementor-skill)

An [Agent Skill](https://agentskills.io) that helps MCP-connected AI agents build well-designed WordPress pages through the Premium Addons for Elementor MCP.

> **Note:** This repository contains the AI Agent Skill, not the Premium Addons for Elementor plugin source code.

The MCP gives an agent **capability** — abilities it can call. This skill gives it **competence** — which ability to call, in what order, with what design judgment, and where to stop and ask.

## Requirements

| | |
|---|---|
| WordPress | with [Elementor](https://elementor.com) active |
| [Premium Addons for Elementor](https://wordpress.org/plugins/premium-addons-for-elementor/) | **required** — install from the WordPress plugin directory; the free version is enough |
| PA dashboard | **Premium Addons → MCP Config & AI Abilities** enabled |
| Your AI client | connected to `https://your-site.com/wp-json/premium-addons/mcp` — via OAuth (recommended) or an Application Password |

If you connect via OAuth, client registration only works for a short window after opening the MCP Config & AI Abilities tab — connect promptly after enabling.

## Install

**Claude.ai, Claude Desktop, or Cowork** — no terminal needed

Plugins work in chat on the web, the Chat tab in Claude Desktop, and Cowork. Add this repository as a marketplace:

1. Open **Customize → Plugins → Personal plugins**
2. Click **+**, then **Add marketplace**
3. Choose **Add from a repository** and paste `https://github.com/Leap13/premium-addons-elementor-skill`
4. Install **premium-addons-elementor** from the marketplace you just added

**Claude Code**

```
/plugin marketplace add Leap13/premium-addons-elementor-skill
/plugin install premium-addons-elementor@leap13
```

**skills.sh ecosystem**

```bash
npx skills add Leap13/premium-addons-elementor-skill
```

**Manual** — clone the repository and copy the skill folder to wherever your runtime loads skills from:

```bash
git clone https://github.com/Leap13/premium-addons-elementor-skill.git
cp -r premium-addons-elementor-skill/skills/premium-addons-elementor ~/.claude/skills/
```

`SKILL.md` and `references/` must stay together, with `references/` as a direct child. Every release also ships a packaged `.plugin` archive you can install directly.

## Usage

### Connect your site first

The skill can do nothing until your AI client is connected to your site. In WordPress admin:

1. Go to **Premium Addons → MCP Config & AI Abilities**
2. Turn on **Enable AI Abilities**
3. Open the **MCP Server** panel and choose a **Connection method** — **OAuth** (recommended; approve in the browser, nothing to copy, tokens expire on their own) or **Application Password** (paste a generated password into your client config)
4. Pick your AI client from the list and copy the configuration the dashboard generates for it. The endpoint is `https://your-site.com/wp-json/premium-addons/mcp`
5. For OAuth, approve the connection when your browser opens

Connect promptly after enabling — OAuth client registration only works for a short window after the tab is opened. To revoke later, use **Disconnect all clients** in the same panel; it revokes every token the site has issued.

### Then just ask

Describe what you want in plain language. The skill activates on its own when a request involves Elementor or Premium Addons — you do not need to name it.

```
Build a pricing section on my staging page with three plans.
Fix the spacing in my hero — it's cramped on mobile.
Copy the testimonials section from my old site to this one.
My widgets aren't showing up in the AI tools. What's wrong?
```

**What happens next.** The skill runs a five-phase workflow: it reads your site's design guide, global colours, fonts, and available widgets before generating anything; commits to a design direction and states its plan; asks before anything destructive; builds with v3 containers by default; then verifies every element landed correctly and runs a design QA pass.

**What it will not do without asking.** Publish a page, change post status, delete an element, enable a disabled widget, alter global settings or theme styles, or edit a page you did not put in scope. New work lands as a draft.

**If a widget needs PA PRO**, the skill builds the closest free alternative first and tells you plainly what it does and doesn't cover.

## What's inside

```
.claude-plugin/
├── plugin.json               plugin manifest — the version lives here
└── marketplace.json          marketplace catalog for /plugin marketplace add
skills/premium-addons-elementor/
├── SKILL.md                  core workflow, safety gates, ability index
└── references/
    ├── widget-selection.md   intent → widget map, free/PRO flags
    ├── global-addons.md      effect vocabulary → addon
    ├── page-patterns.md      section recipes
    └── troubleshooting.md    connection, auth, permissions, renders-nothing
```

`SKILL.md` loads always; references load on demand.

The plugin ships no MCP configuration, because the Premium Addons endpoint is specific to your site. Connect it yourself from the PA dashboard — the skill walks you through it.

## Posture

- **No direct network access.** The skill itself makes no outbound HTTP requests. Site operations occur through the MCP connection you explicitly configure.
- **Zero scripts.** No executables, no build step, no postinstall. Execution belongs to the MCP.
- **No bundled site data.** Nothing about your site is stored or persisted by the skill. Site information is retrieved at runtime through your authorized MCP connection.
- **Drafts by default.** The skill never publishes, deletes, or changes site-wide settings without explicit approval in-conversation.

## Design judgment

Per-page design rules are **not** in this repository. They are served by your own site via the `premium-addons-get-design-guide` ability and version-matched to your installed plugin — one rulebook, kept current by the plugin. This skill defers to it and encodes only what the MCP cannot report about itself: sequencing, selection judgment, and boundary handling.

## Versioning

Semver, independent of the Premium Addons plugin version. Releases are cut when judgment content changes, not mechanically per plugin release. The version is declared once, in `.claude-plugin/plugin.json` — the Agent Skill spec allows only `name` and `description` in `SKILL.md` frontmatter, so it cannot live there.

## Issues and contributions

Bug reports and widget-mapping corrections are welcome via GitHub issues. Include the PA plugin version and the ability name involved.

## License

MIT — see [LICENSE](LICENSE).
