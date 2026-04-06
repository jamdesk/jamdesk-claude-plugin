# Navigation Reference

Navigation is configured in `docs.json` under the `navigation` key. Pages are referenced by file path without the `.mdx` extension.

## Page References

Pages are strings (file paths) or objects with metadata:

```json
"introduction"
"guides/quickstart"
"api/authentication"
```

**Page object** with custom title, icon, or HTTP method badge:

```json
{
  "page": "api/users-create",
  "title": "Create User",
  "method": "POST",
  "icon": "user-plus",
  "tag": "New"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `page` | string | File path without `.mdx` (required) |
| `title` | string | Custom sidebar label (overrides filename) |
| `method` | string | HTTP method badge: `GET`, `POST`, `PUT`, `PATCH`, `DELETE` |
| `icon` | string | Font Awesome icon |
| `tag` | string | Badge text (e.g., "New", "Beta", "Popular") |

Use page objects when you need:
- Proper casing for acronyms: `"title": "SEO"` instead of auto-generated "Seo"
- Proper nouns: `"title": "AWS Route 53"` instead of "Aws route 53"
- HTTP method badges for API endpoints

---

## Pattern 1: Flat Pages

Simplest structure — pages listed directly without groups:

```json
{
  "navigation": {
    "pages": ["introduction", "quickstart", "faq"]
  }
}
```

Best for: Small docs with fewer than 10 pages.

---

## Pattern 2: Grouped Pages

Pages organized into collapsible sidebar groups:

```json
{
  "navigation": {
    "groups": [
      {
        "group": "Getting Started",
        "icon": "rocket",
        "pages": ["introduction", "quickstart"]
      },
      {
        "group": "Core Concepts",
        "icon": "lightbulb",
        "pages": ["concepts/fundamentals", "concepts/architecture"]
      },
      {
        "group": "API",
        "pages": ["api/overview", "api/authentication", "api/endpoints"]
      }
    ]
  }
}
```

**Group properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `group` | string | — | Group title (required) |
| `icon` | string | — | Font Awesome icon |
| `pages` | array | — | Pages and/or nested groups |
| `expanded` | boolean | `false` | Start expanded in sidebar |
| `hidden` | boolean | `false` | Hide from sidebar |

Best for: Most documentation sites — clear organization with 10–50 pages.

---

## Pattern 3: Nested Groups

Groups containing sub-groups for deep hierarchies:

```json
{
  "navigation": {
    "groups": [
      {
        "group": "SDKs",
        "pages": [
          "sdks/overview",
          {
            "group": "JavaScript",
            "pages": ["sdks/js/install", "sdks/js/usage", "sdks/js/advanced"]
          },
          {
            "group": "Python",
            "pages": ["sdks/python/install", "sdks/python/usage"]
          },
          {
            "group": "Go",
            "pages": ["sdks/go/install", "sdks/go/usage"]
          }
        ]
      }
    ]
  }
}
```

Nesting depth is unlimited but keep it shallow (2–3 levels max) for usability.

---

## Pattern 4: Tabbed Navigation

Multiple top-level tabs for separate documentation sections:

```json
{
  "tabsPosition": "left",
  "navigation": {
    "tabs": [
      {
        "tab": "Guides",
        "icon": "book",
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["introduction", "quickstart"]
          },
          {
            "group": "Tutorials",
            "pages": ["tutorials/basic", "tutorials/advanced"]
          }
        ]
      },
      {
        "tab": "API Reference",
        "icon": "code",
        "groups": [
          {
            "group": "Authentication",
            "pages": ["api/auth/overview", "api/auth/tokens"]
          },
          {
            "group": "Endpoints",
            "pages": ["api/users", "api/posts"]
          }
        ]
      },
      {
        "tab": "Help",
        "icon": "life-ring",
        "groups": [
          {
            "group": "FAQ",
            "pages": ["help/faq", "help/troubleshooting"]
          }
        ]
      }
    ]
  }
}
```

**Tab properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `tab` | string | — | Tab title (required) |
| `icon` | string | — | Font Awesome icon |
| `groups` | array | — | Groups within this tab |
| `pages` | array | — | Direct pages (without group) |
| `href` | string | — | External link (makes tab a link) |
| `hidden` | boolean | `false` | Hide from sidebar |

**Tab position** (`tabsPosition` in root config):
- `"left"` — Tabs in sidebar (default for `jam` and `nebula` themes)
- `"top"` — Tabs in header bar (default for `pulsar` theme)

Best for: Sites with distinct audiences or content types (guides vs API vs help).

### External Tab Links

Tabs can link externally instead of containing pages:

```json
{
  "navigation": {
    "tabs": [
      {
        "tab": "Docs",
        "icon": "book",
        "groups": [{ "group": "Main", "pages": ["intro"] }]
      },
      {
        "tab": "GitHub",
        "icon": "github",
        "href": "https://github.com/example/repo"
      },
      {
        "tab": "Discord",
        "icon": "discord",
        "href": "https://discord.gg/example"
      }
    ]
  }
}
```

---

## Pattern 5: Multi-Product

Separate documentation for different products with a product switcher:

```json
{
  "navigation": {
    "products": [
      {
        "product": "web-app",
        "name": "Web Application",
        "icon": "browser",
        "color": { "light": "#3b82f6", "dark": "#60a5fa" },
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["web/intro", "web/setup"]
          }
        ]
      },
      {
        "product": "mobile-sdk",
        "name": "Mobile SDK",
        "icon": "mobile",
        "color": { "light": "#10b981", "dark": "#34d399" },
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["mobile/intro", "mobile/setup"]
          },
          {
            "group": "iOS",
            "pages": ["mobile/ios/install", "mobile/ios/usage"]
          },
          {
            "group": "Android",
            "pages": ["mobile/android/install", "mobile/android/usage"]
          }
        ]
      },
      {
        "product": "cli",
        "name": "CLI Tool",
        "icon": "terminal",
        "color": { "light": "#f59e0b", "dark": "#fbbf24" },
        "groups": [
          {
            "group": "Commands",
            "pages": ["cli/install", "cli/commands"]
          }
        ]
      }
    ]
  }
}
```

**Product properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `product` | string | — | Product ID/slug (required) |
| `name` | string | product ID | Display name |
| `icon` | string | — | Font Awesome icon |
| `color` | object | — | `{ light, dark }` colors |
| `description` | string | — | Description in product switcher |
| `groups` | array | — | Product documentation groups |

Best for: Companies with multiple distinct products sharing one docs site.

---

## Pattern 6: Versioned Documentation

Multiple API or product versions with a version switcher:

```json
{
  "navigation": {
    "versions": [
      {
        "version": "2.0",
        "default": true,
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["v2/intro", "v2/quickstart"]
          },
          {
            "group": "API",
            "pages": ["v2/api/users", "v2/api/posts"]
          }
        ]
      },
      {
        "version": "1.0",
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["v1/intro", "v1/quickstart"]
          }
        ]
      },
      {
        "version": "0.9",
        "href": "https://legacy.example.com/docs"
      }
    ]
  }
}
```

**Version properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `version` | string | — | Version identifier (required) |
| `default` | boolean | `false` | Default version shown to visitors |
| `groups` | array | — | Version-specific documentation |
| `href` | string | — | External URL for archived versions |
| `hidden` | boolean | `false` | Hide from version switcher |

Best for: APIs with breaking changes across versions.

---

## Pattern 7: Multi-Language

Documentation translated into multiple languages:

```json
{
  "navigation": {
    "languages": [
      {
        "language": "en",
        "default": true,
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["introduction", "quickstart"]
          }
        ]
      },
      {
        "language": "es",
        "groups": [
          {
            "group": "Empezando",
            "pages": ["es/introduction", "es/quickstart"]
          }
        ]
      },
      {
        "language": "ja",
        "groups": [
          {
            "group": "はじめに",
            "pages": ["ja/introduction", "ja/quickstart"]
          }
        ]
      },
      {
        "language": "fr",
        "href": "https://fr.docs.example.com"
      }
    ]
  }
}
```

**Language properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `language` | string | — | Language code (required) |
| `default` | boolean | `false` | Default language |
| `groups` | array | — | Language-specific documentation |
| `href` | string | — | External URL for language |
| `banner` | object | — | Banner message: `{ content, dismissible }` |
| `hidden` | boolean | `false` | Hide from selector |

**Supported language codes:** `en`, `es`, `fr`, `fr-CA`, `de`, `ja`, `ko`, `zh`, `zh-Hans`, `zh-Hant`, `pt`, `pt-BR`, `it`, `ru`, `ro`, `cs`, `id`, `ar`, `tr`, `hi`, `sv`, `no`, `lv`, `nl`, `uk`, `vi`, `pl`, `uz`, `he`

---

## Pattern 8: Dropdowns

Dropdown menus for switching between related documentation sections:

```json
{
  "navigation": {
    "dropdowns": [
      {
        "dropdown": "Framework Guides",
        "icon": "puzzle-piece",
        "description": "Framework-specific setup guides",
        "color": { "light": "#8b5cf6", "dark": "#a78bfa" },
        "groups": [
          {
            "group": "React",
            "pages": ["frameworks/react/setup", "frameworks/react/hooks"]
          },
          {
            "group": "Vue",
            "pages": ["frameworks/vue/setup", "frameworks/vue/composables"]
          },
          {
            "group": "Svelte",
            "pages": ["frameworks/svelte/setup"]
          }
        ]
      }
    ]
  }
}
```

**Dropdown properties:**

| Field | Type | Default | Description |
|-------|------|---------|-------------|
| `dropdown` | string | — | Dropdown title (required) |
| `icon` | string | — | Font Awesome icon |
| `description` | string | — | Shown in trigger |
| `color` | object | — | `{ light, dark }` colors |
| `groups` | array | — | Groups in dropdown |
| `pages` | array | — | Direct pages |
| `href` | string | — | External link |
| `hidden` | boolean | `false` | Hide dropdown |

---

## OpenAPI in Navigation

Auto-generate endpoint pages from OpenAPI specs:

```json
{
  "navigation": {
    "groups": [
      {
        "group": "Getting Started",
        "pages": ["introduction", "authentication"]
      },
      {
        "group": "Users API",
        "openapi": "openapi/users.yaml"
      },
      {
        "group": "Billing API",
        "openapi": "openapi/billing.yaml"
      }
    ]
  }
}
```

Pages are auto-generated from each endpoint in the spec. Mix with manual pages:

```json
{
  "group": "API Reference",
  "pages": ["api/overview"],
  "openapi": "openapi.yaml"
}
```

Multiple specs:
```json
{
  "group": "API",
  "openapi": ["openapi/auth.yaml", "openapi/users.yaml", "openapi/posts.yaml"]
}
```

---

## Combining Patterns

Tabs can contain groups, products can contain tabs, etc:

**Tabs + Groups (most common):**
```json
{
  "navigation": {
    "tabs": [
      {
        "tab": "Docs",
        "groups": [
          { "group": "Basics", "pages": ["intro"] },
          { "group": "Advanced", "pages": ["advanced/auth"] }
        ]
      },
      {
        "tab": "API",
        "groups": [
          { "group": "REST", "openapi": "openapi.yaml" },
          { "group": "Webhooks", "pages": ["api/webhooks"] }
        ]
      }
    ]
  }
}
```

**Products + Tabs:**
```json
{
  "navigation": {
    "products": [
      {
        "product": "platform",
        "name": "Platform",
        "tabs": [
          { "tab": "Guides", "groups": [{ "group": "Setup", "pages": ["intro"] }] },
          { "tab": "API", "groups": [{ "group": "Endpoints", "openapi": "openapi.yaml" }] }
        ]
      }
    ]
  }
}
```

---

## Decision Guide

| Situation | Pattern |
|-----------|---------|
| Small docs, < 10 pages | Flat pages |
| Clear topic groupings | Grouped pages |
| Multiple audiences (devs, admins, users) | Tabs |
| Multiple products/services | Products |
| Breaking API changes across versions | Versions |
| International documentation | Languages |
| Framework-specific variants | Dropdowns |
| Auto-generated API docs | OpenAPI in groups |

---

## Tips

1. **Keep navigation shallow** — 2–3 levels of nesting max. Deep hierarchies frustrate users
2. **Group by user task**, not by internal architecture
3. **Use page objects sparingly** — only when you need custom titles, icons, or method badges
4. **Put the most important pages first** in each group
5. **Use tabs to separate concerns** — don't mix API reference with getting-started guides in the same tab
6. **Test with `jamdesk validate`** — catches missing pages and invalid references
7. **Use `jamdesk rename`** — automatically updates all navigation references when moving pages
