---
name: jamdesk
description: Comprehensive reference for building Jamdesk documentation sites. Use when creating MDX pages, configuring docs.json, adding components, setting up navigation, working with Jamdesk CLI commands, or writing documentation content. Routes to detailed reference files for components, configuration, and navigation patterns.
---

## Reference Files

Read these **only when your task requires them** — the quick reference below covers most needs:

| File | When to read |
|------|-------------|
| `reference/components.md` | Adding or modifying MDX components (Cards, Steps, Tabs, Callouts, etc.) — full props and examples |
| `reference/configuration.md` | Changing docs.json settings (theme, colors, navbar, footer, integrations) — complete schema |
| `reference/navigation.md` | Modifying site navigation (tabs, groups, products, versions, languages) — 8 patterns |

## Before You Start

1. Read the project's `docs.json` to understand current configuration
2. Search existing pages before creating new ones — avoid duplicates
3. Read 2-3 similar pages to match the project's voice and conventions
4. Run `jamdesk validate` before deploying to catch config errors

## Project Structure

```
my-docs/
├── docs.json              # Configuration (required)
├── introduction.mdx       # Pages (at least one required)
├── guides/
│   ├── quickstart.mdx
│   └── advanced.mdx
├── api/
│   ├── overview.mdx
│   └── openapi.yaml       # OpenAPI spec (optional)
├── images/
│   ├── logo.webp
│   └── favicon.png
└── snippets/              # Reusable MDX fragments
    └── install-tabs.mdx
```

## Page Frontmatter

```yaml
---
title: Page Title           # Required — used as H1 and browser tab title
description: SEO summary    # Recommended — meta description for search engines
sidebarTitle: Short Name    # Optional — override the sidebar label
icon: rocket                # Optional — Font Awesome icon in sidebar
---
```

All frontmatter fields:

| Field | Type | Description |
|-------|------|-------------|
| `title` | string | Page title (required) |
| `description` | string | Meta description for SEO |
| `sidebarTitle` | string | Override sidebar label |
| `icon` | string | Font Awesome icon name |
| `mode` | string | Layout: `default`, `wide`, `custom`, `frame`, `center` |
| `openapi` | string | OpenAPI operation (e.g., `GET /users`) |
| `asyncapi` | string | AsyncAPI operation |
| `keywords` | string[] | SEO keywords for search indexing |
| `canonical` | string | Canonical URL for the page, overriding the auto-generated one |
| `og:*` / `twitter:*` | string | Per-page Open Graph and Twitter/X social-preview tags (e.g. `og:title`, `og:image`, `twitter:card`). Set flat (Mintlify style) or under a nested `seo:` block |
| `seo` | object | Nested block holding any social/SEO meta keys plus arbitrary custom meta tags |
| `noindex` | boolean | Exclude page from search engines and sitemap |
| `tag` | string | Badge label in sidebar (e.g., `"New"`, `"Beta"`) |

## Quick Component Reference

### Callouts (6 Presets)

```mdx
<Note>General information or guidance.</Note>
<Info>Important detail the reader should know.</Info>
<Warning>Caution — potential issues ahead.</Warning>
<Tip>Helpful suggestion or best practice.</Tip>
<Check>Success or completion confirmation.</Check>
<Danger>Critical warning — data loss or breaking change.</Danger>
```

Custom callout with icon and color:
```mdx
<Callout icon="lightbulb" color="#FF5733">
  Custom callout with any icon and color.
</Callout>
```

### Steps

```mdx
<Steps>
  <Step title="Install the CLI">
    ```bash
    npm install -g jamdesk
    ```
  </Step>
  <Step title="Create a project">
    ```bash
    jamdesk init my-docs
    ```
  </Step>
  <Step title="Start the dev server">
    ```bash
    jamdesk dev
    ```
  </Step>
</Steps>
```

### Tabs

```mdx
<Tabs>
  <Tab title="JavaScript">
    ```js
    const client = new Jamdesk({ apiKey: "..." });
    ```
  </Tab>
  <Tab title="Python">
    ```python
    client = Jamdesk(api_key="...")
    ```
  </Tab>
</Tabs>
```

### Cards & Columns

```mdx
<Columns cols={3}>
  <Card title="Quick Start" icon="rocket" href="/quickstart">
    Get up and running in 5 minutes.
  </Card>
  <Card title="API Reference" icon="code" href="/api">
    Full endpoint documentation.
  </Card>
  <Card title="Examples" icon="flask" href="/examples">
    Sample projects and recipes.
  </Card>
</Columns>
```

### Code Groups

````mdx
<CodeGroup>
```bash npm
npm install my-package
```
```bash yarn
yarn add my-package
```
```bash pnpm
pnpm add my-package
```
</CodeGroup>
````

### Accordion

```mdx
<AccordionGroup>
  <Accordion title="How do I get started?">
    Follow our [quickstart guide](/quickstart).
  </Accordion>
  <Accordion title="What languages are supported?">
    We support JavaScript, Python, Go, Ruby, and more.
  </Accordion>
</AccordionGroup>
```

## CLI Commands

### Development

| Command | Description |
|---------|-------------|
| `jamdesk init [name]` | Create new docs project from starter template |
| `jamdesk dev` | Start local dev server with hot reload (Turbopack) |
| `jamdesk dev --port <port>` | Start on custom port (default: 3000) |
| `jamdesk dev --clean` | Clear build cache before starting |
| `jamdesk dev --webpack` | Use Webpack instead of Turbopack |
| `jamdesk dev --no-open` | Don't auto-open the browser (default: opens the docs URL while compiling; also disable with `"open": false` in `~/.jamdeskrc` or `JAMDESK_NO_OPEN=1` / `CI`) |

### Quality Checks

| Command | Description |
|---------|-------------|
| `jamdesk validate` | Validate docs.json, MDX syntax, OpenAPI specs, and branding |
| `jamdesk broken-links` | Find broken internal links and missing anchors |
| `jamdesk spellcheck` | Check spelling (150+ built-in tech terms) |
| `jamdesk spellcheck --fix` | Interactive mode — fix or add words to ignore list |
| `jamdesk openapi-check <spec>` | Validate a single OpenAPI spec (local file or URL) |
| `jamdesk rename <from> <to>` | Rename file and update all references in docs.json + MDX |

### Deployment

| Command | Description |
|---------|-------------|
| `jamdesk deploy` | Upload docs and trigger build (shows live progress) |
| `jamdesk deploy --detach` | Deploy without waiting for build to finish |
| `jamdesk deploy --full-rebuild` | Force full rebuild (no cache) |
| `jamdesk deploy-proxy cloudflare` | Generate Cloudflare Worker for hosting at custom domain |

### Authentication

| Command | Description |
|---------|-------------|
| `jamdesk login` | Authenticate via browser |
| `jamdesk logout` | Clear stored credentials |
| `jamdesk whoami` | Show current authenticated user |

### Maintenance

| Command | Description |
|---------|-------------|
| `jamdesk doctor` | Diagnose environment issues (Node.js, npm, docs.json) |
| `jamdesk clean` | Clear ~/.jamdesk cache |
| `jamdesk update` | Update CLI to latest version |
| `jamdesk update --check` | Check for updates without installing |
| `jamdesk migrate` | Migrate from Mintlify (interactive wizard) |

## Images

Standard markdown images auto-zoom on click:

```mdx
![Dashboard screenshot](/images/dashboard.png)
```

**Sized images** — set width and height with `=WIDTHxHEIGHT`:

```mdx
![Logo](/images/logo.png =200x50)
![Icon](/images/icon.png =32x32)
```

**Disable zoom** on an image by wrapping in a `<Frame>`:

```mdx
<Frame>
  ![Small icon](/images/icon.png =24x24)
</Frame>
```

Store images in the `images/` directory. Use `.webp` format when possible for smaller file sizes.

## Writing Standards

**Voice & Tone:**
- Write in **second person** — "you" and "your", not "the user" or "one"
- Use **active voice** — "Configure the API key" not "The API key should be configured"
- Use **present tense** — "This command creates" not "This command will create"
- Be **direct and concise** — lead with the action, not the explanation

**Formatting:**
- **Frontmatter**: Every page needs `title`. Add `description` for SEO
- **Headings**: Sentence case — capitalize first word only. H2 for major sections, H3 for subsections — never skip levels
- **Code blocks**: Always specify language for syntax highlighting
- **Links**: Relative paths without `.mdx` extension: `[guide](/guides/quickstart)`
- **Images**: Store in `images/` directory. Use `.webp` format when possible. Always include descriptive alt text
- **Paragraphs**: Keep concise — 2-3 sentences max for readability
- **Lists**: Use bullet lists for 3+ items. Use numbered lists only for ordered steps
- **No emoji** in documentation content — use icons via `<Icon>` component instead

## Common Mistakes

1. **Missing `title` in frontmatter** — every page needs a `title` field
2. **Using `.mdx` in links** — write `/guides/setup`, not `/guides/setup.mdx`
3. **Unescaped `<` in prose** — use `&lt;` or wrap in backticks: `` `<div>` ``
4. **Wrong icon names** — use Font Awesome names (e.g., `rocket`, not `fa-rocket`)
5. **Forgetting to validate** — run `jamdesk validate` before every deploy
6. **Code blocks without language** — always specify for syntax highlighting
7. **Deeply nested navigation** — prefer flat groups; nest only when structure demands it
