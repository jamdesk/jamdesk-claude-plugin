# Configuration Reference

All configuration lives in `docs.json` at the project root.

## Minimal Configuration

```json
{
  "$schema": "https://www.jamdesk.com/docs.json",
  "name": "My Docs",
  "theme": "jam",
  "colors": {
    "primary": "#635BFF"
  },
  "navigation": {
    "groups": [
      {
        "group": "Getting Started",
        "pages": ["introduction"]
      }
    ]
  }
}
```

## Required Fields

| Field | Type | Description |
|-------|------|-------------|
| `name` | string | Project/organization name displayed throughout the site |
| `theme` | string | Documentation theme: `jam`, `nebula`, `pulsar`, or `halo` |
| `colors` | object | Brand colors (at minimum `colors.primary`) |
| `navigation` | object | Site navigation structure |

## Optional Top-Level Fields

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `$schema` | string | — | Schema URL for IDE validation: `https://www.jamdesk.com/docs.json` |
| `description` | string | — | Site description for SEO and AI indexing |
| `logo` | string \| object | — | Logo image path(s) |
| `favicon` | string \| object | — | Favicon path(s) |
| `fonts` | string \| object | — | Typography configuration |
| `navbar` | object | — | Top navigation bar |
| `footer` | object | — | Footer with social links and link columns |
| `anchors` | array | — | External links at sidebar top |
| `appearance` | object | — | Theme mode (light/dark/system) |
| `background` | object | — | Background images and decoration |
| `styling` | object | — | Code block themes, eyebrows, typography |
| `tabsPosition` | string | theme default | Tab placement: `left` or `top` |
| `api` | object | — | OpenAPI/AsyncAPI configuration |
| `seo` | object | — | Meta tags and indexing behavior |
| `search` | object | — | Search customization |
| `chat` | object | — | AI chat configuration |
| `redirects` | array | — | URL redirects |
| `errors` | object | — | Custom error pages |
| `contextual` | object | — | Code block context menu actions |
| `thumbnails` | object | — | Social share preview images |
| `icons` | object | — | Icon library selection |
| `metadata` | object | — | Timestamp display |
| `interaction` | object | — | Drilldown navigation behavior |
| `integrations` | object | — | Analytics and support tools |
| `analytics` | object | — | Jamdesk built-in analytics |
| `auth` | object | — | Access control (password protection) |
| `spellcheck` | object | — | Spelling ignore list |

---

## Theme

Four themes with distinct visual styles:

| Theme | Description |
|-------|-------------|
| `jam` | Clean, modern — default sidebar on left, tabs at left |
| `nebula` | Spacious, airy — similar to jam with different typography |
| `pulsar` | Bold, high-contrast — tabs at top by default |
| `halo` | Warm and soft — sand background, content on a raised card, heavily rounded, Figtree |

```json
{
  "theme": "jam"
}
```

---

## Colors

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `colors.primary` | string | Yes | Primary brand color (hex) |
| `colors.light` | string | No | Light theme variant |
| `colors.dark` | string | No | Dark theme variant |

```json
{
  "colors": {
    "primary": "#635BFF",
    "light": "#7C75FF",
    "dark": "#4F46E5"
  }
}
```

---

## Logo

Single path or light/dark variants:

```json
{
  "logo": "/images/logo.webp"
}
```

```json
{
  "logo": {
    "light": "/images/logo-light.webp",
    "dark": "/images/logo-dark.webp",
    "href": "https://www.example.com"
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `light` | string | — | Logo shown in light mode — visible on light backgrounds |
| `dark` | string | — | Logo shown in dark mode — visible on dark backgrounds |
| `href` | string | — | Click destination URL |

---

## Favicon

```json
{
  "favicon": "/images/favicon.png"
}
```

```json
{
  "favicon": {
    "light": "/images/favicon.png",
    "dark": "/images/favicon-dark.png"
  }
}
```

---

## Fonts

**Simple — Google Font family name:**
```json
{
  "fonts": "Inter"
}
```

**Custom font file:**
```json
{
  "fonts": {
    "family": "Custom Font",
    "source": "/fonts/custom.woff2",
    "format": "woff2",
    "weight": 400
  }
}
```

**Separate heading and body fonts:**
```json
{
  "fonts": {
    "heading": { "family": "Playfair Display" },
    "body": { "family": "Inter" }
  }
}
```

---

## Navbar

```json
{
  "navbar": {
    "style": "default",
    "links": [
      { "label": "Blog", "href": "https://blog.example.com" },
      { "label": "GitHub", "href": "https://github.com/example", "icon": "github" }
    ],
    "primary": {
      "type": "button",
      "label": "Get Started",
      "href": "/quickstart"
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `style` | string | `default` or `topOfContent` |
| `links` | array | Navigation links with `label`, `href`, optional `icon` |
| `primary` | object | CTA button: `type` (`button` \| `github`), `label`, `href` |

---

## Footer

```json
{
  "footer": {
    "socials": {
      "x": "https://x.com/example",
      "github": "https://github.com/example",
      "linkedin": "https://linkedin.com/company/example",
      "discord": "https://discord.gg/example"
    },
    "links": [
      {
        "header": "Product",
        "items": [
          { "label": "Features", "href": "https://example.com/features" },
          { "label": "Pricing", "href": "https://example.com/pricing" }
        ]
      },
      {
        "header": "Resources",
        "items": [
          { "label": "Blog", "href": "https://example.com/blog" },
          { "label": "Changelog", "href": "/changelog" }
        ]
      }
    ]
  }
}
```

**Supported social keys:** `x`, `github`, `linkedin`, `discord`, `website`, `facebook`, `youtube`, `slack`, `instagram`, `hacker-news`, `medium`, `telegram`, `bluesky`, `threads`, `reddit`, `podcast`

---

## Anchors

External links at the top of the sidebar, visible on every page:

```json
{
  "anchors": [
    { "name": "API Reference", "href": "https://api.example.com", "icon": "code" },
    { "name": "Status", "href": "https://status.example.com", "icon": "signal" },
    { "name": "GitHub", "href": "https://github.com/example", "icon": "github" }
  ]
}
```

---

## Appearance

```json
{
  "appearance": {
    "default": "system",
    "strict": false
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `default` | string | `"system"` | Initial theme: `system`, `light`, or `dark` |
| `strict` | boolean | `false` | Hide theme toggle when `true` |

---

## Background

```json
{
  "background": {
    "image": "/images/bg-pattern.png",
    "decoration": "gradient",
    "color": {
      "light": "#ffffff",
      "dark": "#0a0a0a"
    },
    "gradient": {
      "color": "#7c3aed",
      "size": "800px",
      "position": "top center",
      "opacity": 0.25
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `image` | string \| object | Background image path or `{ light, dark }` |
| `decoration` | string | `gradient`, `grid`, `windows`, or `none` (disables jam light-mode gradient) |
| `color` | object | `{ light, dark }` background color overrides for any theme |
| `gradient.color` | string | Override jam gradient hue (default: `colors.primary`) |
| `gradient.size` | string | Gradient radius — CSS length (default: `500px`) |
| `gradient.position` | string | Gradient center — CSS background-position (default: `top center`) |
| `gradient.opacity` | number | Overall gradient intensity multiplier `0–1` (default: `1`) |

Gradient tuning requires `color-mix()` (Chrome 111+, Firefox 113+, Safari 16.2+). Older browsers fall back to the static jam gradient.

---

## Styling

```json
{
  "styling": {
    "eyebrows": "section",
    "latex": false,
    "typography": false,
    "codeblocks": "system",
    "js": "scripts/custom.js"
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `eyebrows` | string | `"section"` | Above-title label: `section` or `breadcrumbs` |
| `latex` | boolean | `false` | Force LaTeX/MathJax rendering |
| `typography` | boolean | `false` | Smart typography (curly quotes, em dashes) |
| `codeblocks` | string \| object | `"system"` | Syntax theme: `system`, `dark`, or a Shiki theme name (e.g., `github-light`, `github-dark`) |
| `js` | string \| array | — | Custom JavaScript file(s) relative to docs root |

---

## Icons

```json
{
  "icons": {
    "library": "fontawesome"
  }
}
```

| Value | Description |
|-------|-------------|
| `fontawesome` | Font Awesome 6 (6000+ icons) — default |
| `lucide` | Lucide icons (400+ icons) |

**Icon object format** (used anywhere icons are accepted):
```json
{
  "icon": {
    "name": "book",
    "style": "solid",
    "library": "fontawesome"
  }
}
```

Font Awesome styles: `solid`, `regular`, `light`, `thin`, `duotone`, `brands`, `sharp-solid`, `sharp-light`, `sharp-regular`, `sharp-thin`

---

## API Configuration

```json
{
  "api": {
    "openapi": "openapi.yaml",
    "asyncapi": "asyncapi.yaml",
    "params": {
      "expanded": "closed"
    },
    "playground": {
      "display": "interactive",
      "proxy": true
    },
    "examples": {
      "defaults": "required",
      "languages": ["curl", "python", "javascript", "go"],
      "prefill": true
    },
    "mdx": {
      "auth": {
        "method": "bearer",
        "name": "Authorization"
      },
      "server": ["https://api.example.com"]
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `openapi` | string \| array | OpenAPI spec path(s) or URL(s) |
| `asyncapi` | string \| array | AsyncAPI spec path(s) — **accepted but not rendered**; `jamdesk validate` warns |
| `params.expanded` | string | `all` (expand all) or `closed` (collapsed by default) |
| `playground.display` | string | `interactive`, `simple`, or `none` |
| `playground.proxy` | boolean | Enable CORS proxy for playground requests |
| `examples.defaults` | string | Pre-fill: `all` params or `required` only |
| `examples.languages` | array | Code example languages |
| `examples.prefill` | boolean | Pre-fill example values |
| `mdx.auth.method` | string | `bearer`, `basic`, `key`, or `cobo` |
| `mdx.server` | string \| array | API base URL for `api:` pages. An array is accepted but only `[0]` is used — `jamdesk validate` warns on the rest |

**Supported example languages:** `curl`, `bash`, `python`, `javascript`, `go`, `ruby`, `csharp`, `java`, `rust`, `php`

---

## SEO

```json
{
  "seo": {
    "metatags": {
      "og:image": "https://example.com/og.png",
      "twitter:card": "summary_large_image"
    },
    "indexing": "navigable",
    "indexHiddenPages": false,
    "ai": {
      "llmsTxt": true
    }
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `metatags` | object | — | Custom meta tags (key-value pairs) |
| `indexing` | string | `"navigable"` | `navigable` (only nav pages) or `all` |
| `indexHiddenPages` | boolean | `false` | Include hidden pages in sitemap |
| `ai.llmsTxt` | boolean | `true` | Generate `llms.txt` and `llms-full.txt` for AI tools. Set `false` to stop publishing them. Independent of search indexing — a page can be indexed by search engines while excluded from AI ingestion, or vice versa. |

---

## Search

```json
{
  "search": {
    "prompt": "Search documentation...",
    "popularPages": [
      { "title": "Getting Started", "slug": "quickstart", "icon": "rocket" },
      { "title": "API Reference", "slug": "api/overview", "icon": "code" }
    ]
  }
}
```

---

## Chat (AI)

```json
{
  "chat": {
    "enabled": true,
    "starterQuestions": [
      "How do I get started?",
      "What components are available?",
      "How do I deploy my docs?"
    ]
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `enabled` | boolean | `true` | Enable AI chat |
| `starterQuestions` | array | auto-generated | Suggested questions. Set to `[]` to disable |

---

## Redirects

```json
{
  "redirects": [
    { "source": "/old-page", "destination": "/new-page", "permanent": true },
    { "source": "/docs/v1", "destination": "https://v1.example.com" }
  ]
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `source` | string | — | Old path (required) |
| `destination` | string | — | New path or URL (required) |
| `permanent` | boolean | `false` | `true` = 301, `false` = 302 |

---

## Error Pages

```json
{
  "errors": {
    "404": {
      "redirect": true,
      "title": "Page Not Found",
      "description": "The page you're looking for doesn't exist. [Go home](/)"
    }
  }
}
```

---

## Contextual Menu

Code block right-click actions:

```json
{
  "contextual": {
    "enabled": true,
    "options": [
      "copy",
      "chatgpt",
      "claude",
      "cursor",
      "vscode"
    ]
  }
}
```

**Built-in options:** `copy`, `view`, `chatgpt`, `claude`, `gemini`, `perplexity`, `mcp`, `cursor`, `vscode`

**Custom option:**
```json
{
  "title": "Open in Playground",
  "description": "Test this code",
  "icon": "flask",
  "href": "https://playground.example.com"
}
```

With dynamic content:
```json
{
  "title": "Search",
  "icon": "search",
  "href": {
    "base": "https://example.com/search",
    "query": [{ "key": "q", "value": "{{CONTENT}}" }]
  }
}
```

---

## Thumbnails

Social share preview images:

```json
{
  "thumbnails": {
    "appearance": "dark",
    "background": "https://example.com/og-bg.png",
    "fonts": { "family": "Inter" }
  }
}
```

---

## Metadata

```json
{
  "metadata": {
    "timestamp": true
  }
}
```

When `true`, pages show last-modified date.

---

## Interaction

```json
{
  "interaction": {
    "drilldown": true
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `drilldown` | boolean | — | Enable click-through navigation on groups |

---

## Analytics

```json
{
  "analytics": {
    "enabled": true
  }
}
```

Jamdesk's built-in analytics dashboard. Separate from third-party `integrations`.

---

## Spellcheck

```json
{
  "spellcheck": {
    "ignore": ["Jamdesk", "kubectl", "OAuth2", "GraphQL"]
  }
}
```

Over 150 tech terms are built-in (API, SDK, TypeScript, JavaScript, etc.).

---

## Auth (Password Protection)

Restrict access to your docs site with a shared password. Two modes: **whole-site** (all pages gated) and **specific pages** (only marked pages gated).

The password itself is set in the Jamdesk dashboard, not in `docs.json`. The config below controls which pages are protected and how.

### Mode 1: Whole Site

Gate every page behind a password. Optionally allow specific pages to remain public.

```json
{
  "auth": {
    "password": {
      "enabled": true,
      "hint": "Ask your account manager",
      "public": ["/changelog", "/status/*"]
    }
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `enabled` | boolean | `false` | Gate the entire site behind a password |
| `hint` | string | — | Hint shown on the unlock page (plain text, max 200 chars) |
| `public` | array | — | Paths or globs that bypass the password. Supports `*` (one segment) and `**` (recursive). Max 100 entries |

**Public exceptions** can also be declared via:
- **Frontmatter**: `public: true` in a page's MDX frontmatter
- **Navigation groups**: `"public": true` on a group in `docs.json`

All three sources are merged. A page marked both public and private is treated as **public**.

### Mode 2: Specific Pages

Gate only certain pages. Every other page stays public. This mode activates automatically when private markers exist but `enabled` is not `true`.

**Option A — Frontmatter (recommended for per-page control):**

```mdx
---
title: Internal API Guide
private: true
---

This page requires a password.
```

**Option B — Config array:**

```json
{
  "auth": {
    "password": {
      "private": ["/internal/roadmap", "/internal/api-keys"],
      "hint": "Use the team password"
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `private` | array | Exact paths (starting with `/`) that require the password |

Both sources are merged — frontmatter `private: true` and `auth.password.private[]` entries combine into the private set.

### Mode Detection

| Condition | Mode | Behavior |
|-----------|------|----------|
| `auth.password.enabled: true` | Whole site | All pages gated; `public` paths are exceptions |
| `private: true` markers exist (no `enabled`) | Specific pages | Only marked pages are gated |
| Neither | Off | No password protection |

Whole-site mode takes precedence: if `enabled: true` is set, `private` markers are ignored.

### Dashboard

The dashboard shows the current mode ("Whole site" or "Specific pages"), lists private/public pages, and provides the interface for setting or changing the password.

---

## Auth (JWT Authentication)

Gate docs access from your own login system instead of a shared password. Your backend signs a short-lived JWT per visitor; Jamdesk verifies it and mints a per-user session. Requires a paid plan. Mutually exclusive with `auth.password` — a build with both `enabled: true` fails validation.

```json
{
  "auth": {
    "jwt": {
      "enabled": true,
      "loginUrl": "https://app.example.com/docs-login",
      "public": ["/changelog/*"]
    }
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `enabled` | boolean | `false` | Gate the entire site behind JWT auth |
| `loginUrl` | string | — | Absolute `https://` URL of your login flow. Required when `enabled: true`. Unauthenticated visitors are redirected here with `?redirect=<path>` |
| `public` | array | — | Paths or globs that bypass authentication. Supports `*` (one segment) and `**` (recursive). Max 100 entries |

The signing key (Ed25519) is generated in the Jamdesk dashboard, not in `docs.json` — the private key is shown once and never stored by Jamdesk.

**Token payload**, signed with `EdDSA` and a short `exp` (recommend ≤10s — this is a handshake window, not the session length):

| Field | Required | Description |
|-------|----------|-------------|
| `host` | Yes | Must exactly match the request host (case-insensitive) |
| `expiresAt` | No | Unix seconds; controls session length. Capped at 30 days, defaults to 7 days |
| `groups` | No | Session group names, up to 32 entries of 64 chars each |
| `apiPlaygroundInputs` | No | Pre-fill for the API playground (`header`, `query`, `path`); serialized size capped at 2KB |

**Group-based page access**: frontmatter `groups: ["admin"]` restricts a page to sessions carrying an intersecting group; others get a 404. Group-restricted pages are excluded from the sitemap, search, AI chat, and MCP — even for users in the group. An empty `groups: []` means no restriction (remove the field, don't leave it empty); to block a page from everyone, unpublish it instead. Localized copies inherit the base page's groups unless the translation declares its own.

**Redirect flow**: unauthenticated request → 302 to `{loginUrl}?redirect=<path>` → your backend signs a JWT and redirects to `https://<docs-host>/_jd/auth/callback?redirect=<path>#<jwt>` (token in the URL fragment, never sent to the server) → Jamdesk verifies and mints a session cookie → browser lands on the original `redirect` path.

Full guide: [JWT authentication](https://jamdesk.com/docs/setup/jwt-authentication).

---

## Integrations

Analytics and support tool integrations:

```json
{
  "integrations": {
    "ga4": { "measurementId": "G-XXXXXXXXXX" },
    "gtm": { "tagId": "GTM-XXXXXXX" },
    "plausible": { "domain": "docs.example.com" },
    "posthog": { "apiKey": "...", "apiHost": "..." },
    "amplitude": { "apiKey": "..." },
    "segment": { "key": "..." },
    "mixpanel": { "projectToken": "..." },
    "hotjar": { "hjid": "...", "hjsv": "..." },
    "clarity": { "projectId": "..." },
    "fathom": { "siteId": "..." },
    "pirsch": { "id": "..." },
    "heap": { "appId": "..." },
    "logrocket": { "appId": "..." },
    "koala": { "publicApiKey": "..." },
    "hightouch": { "writeKey": "...", "apiHost": "..." },
    "intercom": { "appId": "..." },
    "crisp": { "websiteId": "..." },
    "frontchat": { "snippetId": "..." },
    "clearbit": { "publicApiKey": "..." },
    "osano": { "scriptSource": "..." }
  }
}
```

**Plausible self-hosted / proxy:**
```json
{
  "integrations": {
    "plausible": {
      "scriptUrl": "https://plausible.io/js/pa-XXXXX.js",
      "server": "https://plausible.example.com"
    }
  }
}
```

### Newsletter (Email Signups)

Configures the `<EmailSubscribe>` component and, with `placement: "changelog"`, auto-mounts a signup form on every changelog page (any page with `rss: true`):

```json
{
  "integrations": {
    "newsletter": {
      "provider": "resend",
      "title": "Get release notes",
      "placement": "changelog"
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `provider` | string | `resend`, `mailchimp`, `kit`, `loops`, `beehiiv`, `brevo`, `sendgrid`, `buttondown`, or `substack` |
| `title` | string | Form heading (falls back to the dashboard's Form title) |
| `description` | string | Form supporting line (falls back to the dashboard's Form subtitle) |
| `collapsed` | boolean | Native only — start as a compact Subscribe button |
| `username` | string | Buttondown / Substack username (embed-only providers) |
| `snippet` | string | Raw embed markup (escape hatch) |
| `height` | string | Embed iframe height |
| `placement` | `none` \| `changelog` | `none` (default) or `changelog` to auto-mount on changelog pages |

Native providers (`resend`, `mailchimp`, `kit`, `loops`, `beehiiv`, `brevo`, `sendgrid`) need an API key connected in the dashboard (Settings → Email Signups); the key is stored backend-only, never in `docs.json`. To skip auto-placement on one changelog page, set `newsletter: false` in that page's frontmatter. Leave `title`/`description` out to inherit the dashboard copy.

---

## hostAtDocs

Serve documentation at a subpath (e.g., `example.com/docs`) instead of the root:

```json
{
  "hostAtDocs": true
}
```

When `true`, all docs URLs are prefixed with `/docs/`. Requires a proxy (Cloudflare Worker or similar) to route traffic. Use `jamdesk deploy-proxy cloudflare` to generate one.

The subpath itself is **not** a `docs.json` field — it's set in the dashboard, under Project Settings → Custom Domain → "Host docs at a subpath". It defaults to `/docs` and must be a single lowercase segment (letters, digits, hyphens); a handful of segments are reserved and rejected (e.g. `api`, `jd`, `wp-admin`, and locale codes like `fr`). Renaming it is safe for indexed URLs — the previous subpath keeps 308-redirecting to the new one (one level of history), and `/docs/*` itself always keeps serving no matter what the subpath is set to.

If the proxy is a generated Cloudflare Worker, pass the same value to `--path` so its `PROXY_PATHS` list matches the dashboard setting, e.g. for a subpath of `/help`:

```bash
jamdesk deploy-proxy cloudflare --path /help
```

`PROXY_PATHS` needs both the chosen subpath and `/_jd/*` (Jamdesk's shared assets) — the generated template already covers both. If a customer hand-modified their worker (extra proxied paths, custom logic), edit the subpath entry in place after a rename rather than regenerating the whole file — `--path` regeneration is safe only for an unmodified template; on a customized one it drops the custom entries.

Regenerating into a directory that already exists takes `--force`; without it the command asks first, and under `--yes` it stops rather than overwrite. `--yes` also never deploys — it writes the files and leaves `npx wrangler deploy` to you.

A stale worker doesn't misroute traffic to the wrong prefix — it fails closed: requests under the new subpath never reach Jamdesk at all (they fall through to the customer's own origin, which normally 404s them), while the old subpath keeps working indefinitely thanks to the serve-both behavior above. "New subpath 404s, old one still works" points at the customer's proxy config, not a Jamdesk bug.

Vercel-proxied custom domains carry the identical risk: the dashboard's `vercel.json` rewrite snippet is only regenerated for the *next copy-paste* — a customer who already pasted it into their own repo must update and redeploy their `vercel.json` after renaming the subpath, or they hit the same fail-closed 404 on the new subpath.

---

## Full Example

```json
{
  "$schema": "https://www.jamdesk.com/docs.json",
  "name": "Acme Docs",
  "theme": "jam",
  "colors": { "primary": "#635BFF" },
  "logo": { "light": "/images/logo-light.webp", "dark": "/images/logo-dark.webp" },
  "favicon": "/images/favicon.png",
  "navbar": {
    "links": [{ "label": "Blog", "href": "https://www.acme.com/blog" }],
    "primary": { "type": "button", "label": "Dashboard", "href": "https://dashboard.acme.com" }
  },
  "footer": {
    "socials": { "x": "https://x.com/acme", "github": "https://github.com/acme" }
  },
  "tabsPosition": "left",
  "navigation": {
    "tabs": [
      {
        "tab": "Documentation",
        "groups": [
          { "group": "Getting Started", "pages": ["introduction", "quickstart"] }
        ]
      },
      {
        "tab": "API Reference",
        "groups": [{ "group": "Endpoints", "openapi": "openapi.yaml" }]
      }
    ]
  },
  "auth": { "password": { "enabled": true, "hint": "Ask your account manager", "public": ["/changelog"] } },
  "api": { "openapi": "openapi.yaml", "playground": { "display": "interactive" } },
  "integrations": { "plausible": { "domain": "docs.acme.com" } }
}
```
