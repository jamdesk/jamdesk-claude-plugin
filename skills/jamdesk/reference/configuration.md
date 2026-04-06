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
| `theme` | string | Documentation theme: `jam`, `nebula`, or `pulsar` |
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
| `spellcheck` | object | — | Spelling ignore list |

---

## Theme

Three themes with distinct visual styles:

| Theme | Description |
|-------|-------------|
| `jam` | Clean, modern — default sidebar on left, tabs at left |
| `nebula` | Spacious, airy — similar to jam with different typography |
| `pulsar` | Bold, high-contrast — tabs at top by default |

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

| Field | Type | Description |
|-------|------|-------------|
| `light` | string | Logo shown in light mode — visible on light backgrounds (required) |
| `dark` | string | Logo shown in dark mode — visible on dark backgrounds (optional) |
| `href` | string | Click destination URL (optional) |

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
    }
  }
}
```

| Field | Type | Description |
|-------|------|-------------|
| `image` | string \| object | Background image path or `{ light, dark }` |
| `decoration` | string | `gradient`, `grid`, or `windows` |
| `color` | object | `{ light, dark }` background colors |

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
| `codeblocks` | string \| object | `"system"` | Syntax theme: `system` or `dark` |
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
| `asyncapi` | string \| array | AsyncAPI spec path(s) or URL(s) |
| `params.expanded` | string | `all` (expand all) or `closed` (collapsed by default) |
| `playground.display` | string | `interactive`, `simple`, or `none` |
| `playground.proxy` | boolean | Enable CORS proxy for playground requests |
| `examples.defaults` | string | Pre-fill: `all` params or `required` only |
| `examples.languages` | array | Code example languages |
| `examples.prefill` | boolean | Pre-fill example values |
| `mdx.auth.method` | string | `bearer`, `basic`, `key`, or `cobo` |
| `mdx.server` | string \| array | API base URL(s) |

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
    "indexHiddenPages": false
  }
}
```

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `metatags` | object | — | Custom meta tags (key-value pairs) |
| `indexing` | string | `"navigable"` | `navigable` (only nav pages) or `all` |
| `indexHiddenPages` | boolean | `false` | Include hidden pages in sitemap |

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

---

## hostAtDocs

Serve documentation at a subpath (e.g., `example.com/docs`) instead of the root:

```json
{
  "hostAtDocs": true
}
```

When `true`, all docs URLs are prefixed with `/docs/`. Requires a proxy (Cloudflare Worker or similar) to route traffic. Use `jamdesk deploy-proxy cloudflare` to generate one.

---

## Full Example

```json
{
  "$schema": "https://www.jamdesk.com/docs.json",
  "name": "Acme Docs",
  "description": "Documentation for the Acme platform",
  "theme": "jam",
  "colors": {
    "primary": "#635BFF",
    "light": "#7C75FF",
    "dark": "#4F46E5"
  },
  "logo": {
    "light": "/images/logo-light.webp",
    "dark": "/images/logo-dark.webp",
    "href": "https://www.acme.com"
  },
  "favicon": "/images/favicon.png",
  "fonts": {
    "heading": { "family": "Inter" },
    "body": { "family": "Inter" }
  },
  "navbar": {
    "links": [
      { "label": "Blog", "href": "https://www.acme.com/blog" }
    ],
    "primary": {
      "type": "button",
      "label": "Dashboard",
      "href": "https://dashboard.acme.com"
    }
  },
  "footer": {
    "socials": {
      "x": "https://x.com/acme",
      "github": "https://github.com/acme",
      "discord": "https://discord.gg/acme"
    }
  },
  "appearance": { "default": "system" },
  "tabsPosition": "left",
  "navigation": {
    "tabs": [
      {
        "tab": "Documentation",
        "icon": "book-open",
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["introduction", "quickstart"]
          },
          {
            "group": "Guides",
            "pages": ["guides/authentication", "guides/webhooks"]
          }
        ]
      },
      {
        "tab": "API Reference",
        "icon": "code",
        "groups": [
          {
            "group": "Endpoints",
            "openapi": "openapi.yaml"
          }
        ]
      }
    ]
  },
  "api": {
    "openapi": "openapi.yaml",
    "playground": { "display": "interactive" },
    "examples": {
      "languages": ["curl", "python", "javascript", "go"]
    }
  },
  "chat": { "enabled": true },
  "redirects": [
    { "source": "/docs/old", "destination": "/guides/new", "permanent": true }
  ],
  "integrations": {
    "ga4": { "measurementId": "G-XXXXXXXXXX" },
    "plausible": { "domain": "docs.acme.com" }
  }
}
```
