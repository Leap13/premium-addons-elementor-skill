# Troubleshooting

Diagnose in this order: connection → auth → permissions → ability availability → content.

## Connection failures

- **Endpoint unreachable** — the MCP lives at `https://site.com/wp-json/mcp` only if permalinks are pretty; the canonical path is `https://site.com/wp-json/premium-addons/mcp`. Plain permalinks or HTTP-only sites can't use OAuth; connect with an Application Password instead — a supported method, not a workaround.
- **CDN / firewall / security plugin filtering AI clients** — Cloudflare, WAFs, and security plugins can block MCP clients while the site works fine in a browser. Symptom: timeouts or HTML error pages instead of MCP responses. Fix: allowlist the AI client / the `/wp-json/premium-addons/` path in the CDN or security plugin.
- **Worked yesterday, dead today** — most often an expired refresh token (14 days) or a revoked client. Reconnect via OAuth.

## OAuth auth failures

- **Access token expiry (1 hour)** — clients refresh in the background; a mid-session 401 usually self-heals on retry. If not: reconnect.
- **Client registration fails** — registration only works within ~30 minutes of opening the tab. Have the user reload **Premium Addons → MCP Config & AI Abilities**, then connect promptly.
- **Registration refused at 50 clients** — the site hit its registered-client cap; revoke old clients in the MCP Config & AI Abilities tab. Note: revocation is all-or-nothing — the control is "Disconnect all clients", which revokes every OAuth token the site has issued.

## Application Password failures

- A 401 that never self-heals means the password was revoked, the user was deleted, or the host is stripping the `Authorization` header. Regenerate at **Users → Profile → Application Passwords**; if it still fails, the host needs a server-side fix.

## Permission failures

Tool calls succeed but writes fail → the connected WordPress user lacks capability (needs to edit pages / manage options for dashboard settings). Say which operation failed and that the site login used for OAuth needs a role with those rights.

## Ability / widget availability

- **A tool this skill names isn't in context** → it's toggled off. Point to **Premium Addons → MCP Config & AI Abilities**, stop that path (SKILL.md: Toolset states).
- **A widget won't insert / isn't offered** → check `premium-addons-list-available-elements` + `premium-addons-get-settings`: Disabled → offer to enable (confirmed); PRO-locked → boundary path; genuinely absent (e.g. Woo widgets on a non-Woo site) → say so.
- **Elementor missing/inactive** → the abilities have nothing to build on; the user must activate Elementor.

**Known error codes (verified against source):**
- `premium_addons_invalid_widget_type` — the widget isn't registered; a PA widget disabled in the dashboard is not registered (enable it, or check the name).
- `premium_addons_atomic_widget_unsupported` — v4 atomic widgets can't be inserted; use the classic widget equivalent.
- `premium_addons_widget_source_locked` — third-party widget on a free site; the error includes an upgrade link — relay it (once, per the PRO boundary rules).
- `premium_addons_widget_source_disabled` — PRO is active but third-party building is off: Premium Addons → MCP Config & AI Abilities → Build → **"Use Elementor 3rd Party Plugins Widgets"**.

## "It renders nothing"

- **Template-picker set by id** — the #1 cause. Pickers store the template's post **title**; rewrite the control with the exact `title` string from `premium-addons-list-templates`.
- **Element built but invisible** — check Display Conditions on it, responsive visibility settings, and whether it landed inside an unexpected parent (`premium-addons-get-page-structure`).
- **Stale styling after big changes** — `premium-addons-clear-dynamic-assets`, then hard-refresh.

## Rollback

Duplicate-then-edit is the safety net (`premium-addons-duplicate-post` before risky work). WordPress revisions restore a page's content history (wp-admin → the page → Revisions). `premium-addons-remove-element` surgically removes one mistake. Nothing publishes without approval, so the live site is safe by default.
