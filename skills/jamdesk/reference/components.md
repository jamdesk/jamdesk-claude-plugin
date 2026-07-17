# Components Reference

All components are available in any `.mdx` file without imports.

## Callouts

Six preset callout types plus custom callouts.

### Preset Callouts

```mdx
<Note>General information or guidance.</Note>
<Info>Important detail the reader should know.</Info>
<Warning>Caution — potential issues ahead.</Warning>
<Tip>Helpful suggestion or best practice.</Tip>
<Check>Success or completion confirmation.</Check>
<Danger>Critical warning — data loss or breaking change.</Danger>
```

### Custom Callout

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `icon` | string | — | Font Awesome icon name |
| `color` | string | — | Hex color or CSS color name |

```mdx
<Callout icon="lightbulb" color="#FF5733">
  Custom callout with any icon and color.
</Callout>
```

---

## Card

Clickable card with icon, image, and optional call-to-action.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Card title |
| `icon` | string \| ReactElement | — | Font Awesome icon name or SVG |
| `img` | string | — | Image URL |
| `href` | string | — | Link destination (internal or external) |
| `horizontal` | boolean | `false` | Horizontal layout |
| `arrow` | boolean \| string | — | Show arrow (auto for external links) |
| `cta` | string | — | Call-to-action text |

```mdx
<Card title="Quick Start" icon="rocket" href="/quickstart" cta="Get started">
  Set up your project in minutes.
</Card>

<Card title="Demo" img="/images/demo.png" href="/demo" horizontal>
  See Jamdesk in action.
</Card>
```

---

## Columns

Responsive grid layout for cards.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `cols` | number | `2` | Column count (1–4) |

```mdx
<Columns cols={3}>
  <Card title="Card 1" icon="star">Content</Card>
  <Card title="Card 2" icon="heart">Content</Card>
  <Card title="Card 3" icon="bolt">Content</Card>
</Columns>
```

---

## Steps & Step

Numbered step-by-step instructions.

**Steps Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `titleSize` | string | `"p"` | Title size: `p`, `h2`, or `h3` |

**Step Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Step title |
| `icon` | string | — | Custom icon (Font Awesome name or URL) |
| `iconType` | string | — | Icon style: `regular`, `solid`, `light`, `thin`, `sharp-solid`, `duotone`, `brands` |

```mdx
<Steps titleSize="h3">
  <Step title="Install" icon="download">
    ```bash
    npm install -g jamdesk
    ```
  </Step>
  <Step title="Initialize" icon="folder-plus">
    ```bash
    jamdesk init my-docs
    ```
  </Step>
  <Step title="Preview" icon="eye">
    ```bash
    jamdesk dev
    ```
  </Step>
</Steps>
```

---

## Tabs & Tab

Switchable tabbed content.

**Tab Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Tab label (required) |
| `icon` | string | — | Font Awesome icon name |
| `iconType` | string | — | Icon style |

```mdx
<Tabs>
  <Tab title="JavaScript" icon="js">
    ```js
    const sdk = require("my-sdk");
    ```
  </Tab>
  <Tab title="Python" icon="python">
    ```python
    import my_sdk
    ```
  </Tab>
  <Tab title="Go">
    ```go
    import "github.com/example/sdk"
    ```
  </Tab>
</Tabs>
```

---

## CodeGroup

Tabbed code blocks — syntactic sugar for language switching.

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

The first line of each code block (`bash npm`) sets the language and tab label.

---

## Accordion & AccordionGroup

Collapsible sections for FAQs or optional detail.

**Accordion Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Visible label (required) |
| `description` | string | — | Subtitle below title |
| `defaultOpen` | boolean | `false` | Start expanded |
| `icon` | string | — | Font Awesome icon |
| `iconType` | string | — | Icon style |

```mdx
<AccordionGroup>
  <Accordion title="What formats are supported?" icon="file">
    MDX (Markdown + JSX), OpenAPI 3.x, and AsyncAPI specs.
  </Accordion>
  <Accordion title="Can I use custom components?" defaultOpen>
    Yes — add React components to a `snippets/` directory.
  </Accordion>
</AccordionGroup>
```

---

## Expandable

Lightweight show/hide toggle — simpler than Accordion.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Toggle label (required) |
| `defaultOpen` | boolean | `false` | Start expanded |

```mdx
<Expandable title="Show advanced options">
  Configure rate limiting, caching, and retry behavior.
</Expandable>
```

---

## Badge

Inline status label.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `color` | string | `"gray"` | `gray`, `blue`, `green`, `yellow`, `orange`, `red`, `purple`, `white`, `surface` |
| `size` | string | `"md"` | `xs`, `sm`, `md`, `lg` |
| `shape` | string | `"rounded"` | `rounded`, `pill` |
| `icon` | string | — | Font Awesome icon |
| `iconType` | string | — | Icon style: `regular`, `solid`, `light`, `thin`, `sharp-solid`, `duotone`, `brands` |
| `stroke` | boolean | — | Outline style |
| `disabled` | boolean | — | Disabled appearance |

```mdx
<Badge color="green" icon="check">Stable</Badge>
<Badge color="yellow" size="sm" shape="pill">Beta</Badge>
<Badge color="red" stroke>Deprecated</Badge>
```

---

## Tooltip

Hover text with optional headline and CTA.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `tip` | string | — | Tooltip text (required) |
| `headline` | string | — | Bold text above tip |
| `cta` | string | — | Call-to-action link text |
| `href` | string | — | CTA link URL |

```mdx
<Tooltip tip="Application Programming Interface" headline="API">
  API
</Tooltip>

<Tooltip tip="Learn about rate limits" cta="Read more" href="/api/rate-limits">
  rate-limited
</Tooltip>
```

---

## Icon

Inline icon display.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `icon` | string \| ReactElement | — | Font Awesome name, URL, or SVG (required) |
| `iconType` | string | — | Style: `regular`, `solid`, `light`, `thin`, `sharp-solid`, `duotone`, `brands` |
| `color` | string | — | Hex color or CSS name |
| `size` | number | `16` | Size in pixels |

```mdx
<Icon icon="star" color="#FFD700" size={24} />
<Icon icon="github" iconType="brands" size={20} />
```

---

## Frame

Image container with optional caption.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `caption` | string | — | Figure caption text |

```mdx
<Frame caption="The Jamdesk dashboard">
  ![Dashboard screenshot](/images/dashboard.png)
</Frame>
```

---

## Panel

Content rendered in the right sidebar panel (sticky on scroll).

```mdx
<Panel>
  <Note>This appears in the sidebar panel.</Note>
</Panel>
```

---

## Prompt

Reusable AI instructions that readers can copy or open in a supported tool. Prompt supports Fern-style `title`, `actions`, `singleLine`, `hidePrompt`, and custom URL actions, plus Mintlify-compatible `description`, `icon`, `iconType`, and an explicit `"copy"` action.

Copy is always available, so a copy-only prompt needs no props:

```mdx
<Prompt>
Explain how API key rotation works for a developer using our REST API for the first time.
</Prompt>
```

Add `cursor`, `claude`, `chatgpt`, `perplexity`, or `gemini` to offer open-in actions, each rendered with its brand icon. Built-in action labels localize automatically to the page's language (fr, es, de, it, pt, nl, ja, ko, zh); custom-action labels render exactly as authored. The first valid action appears beside Copy; additional actions appear in the More menu.

```mdx
<Prompt
  title="Compare authentication flows"
  actions={["cursor", "claude", "chatgpt", "perplexity", "gemini"]}
>
Compare the session-token and API-key authentication flows in this repository.
List their security tradeoffs and recommend which flow each client type should use.
</Prompt>
```

Custom actions accept a label, a credential-free HTTP(S) URL, and an optional icon. Put `{prompt}` in a path segment, query value, or fragment to insert the URL-encoded prompt. Without the placeholder, Jamdesk adds a `prompt` query parameter.

```mdx
<Prompt
  title="Research this migration"
  actions={[
    {
      label: "Search the web",
      url: "https://www.google.com/search?q={prompt}",
      icon: "magnifying-glass",
    },
    "claude",
  ]}
>
Compare this migration plan with the current public API contract.
Identify breaking changes, missing rollback steps, and tests needed before release.
</Prompt>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `children` | ReactNode | — | Prompt content between the tags. It is rendered as the preview unless `description` replaces the preview or `hidePrompt` hides it. |
| `title` | string | — | Label displayed in the card header. |
| `description` | string | — | Mintlify-compatible inline-Markdown preview. It changes only the preview; `children` remain the copied or sent prompt. |
| `icon` | string \| ReactElement | `sparkles` | Font Awesome name, image URL/path, or inline SVG element. |
| `iconType` | string | — | Font Awesome style for an unprefixed string icon: `regular`, `solid`, `light`, `thin`, `sharp-solid`, `duotone`, or `brands`. |
| `actions` | (`copy` \| `cursor` \| `claude` \| `chatgpt` \| `perplexity` \| `gemini` \| CustomAction)[] | `[]` | Actions in display order. `CustomAction` is `{ label: string; url: string; icon?: string }`. Explicit `copy` is accepted and de-duplicated. |
| `singleLine` | boolean \| string | `false` | Clip the preview to one line when `true` or `"true"`; `"false"` remains disabled. Actions still use the complete prompt. |
| `hidePrompt` | boolean \| string | `false` | Hide the preview when a title is present and the value is `true` or `"true"`. Without a title, the preview remains visible. |
| `className` | string | — | Additional classes on the card root. |

Prompt actions use the exact human-visible authored Markdown between the tags, rather than reconstructing text from the rendered preview. Internal formatting is preserved; only whitespace outside the first and last authored content nodes is discarded. Within a Prompt, `<Visibility for="humans">` wrapper tags are omitted while their contents remain. Agent-only Visibility subtrees are excluded, as are subtrees whose audience is obscured by an expression-valued `for={...}` prop or a later spread attribute. Missing `for`, shorthand `for`, and invalid literal audiences remain visible. A Prompt inside agent-only or expression- or spread-obscured Visibility has no copyable source.

Custom URLs reject non-HTTP(S) schemes, credentials, `{prompt}` in the origin or query keys, and final URLs longer than 8,000 characters. Invalid, duplicate, or oversized open-in actions are omitted; Copy remains available as the lossless fallback.

> **Privacy:** Clicking an open-in action sends the complete copyable prompt to the selected third party. Do not include secrets, personal data, or proprietary content unless you intend to share it under that provider's privacy policy. Copy does not open a third-party service.

---

## Tile

Preview card with image and link — used for showcasing examples.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `href` | string | — | Link destination (required) |
| `title` | string | — | Title below preview |
| `description` | string | — | Description text |

```mdx
<Tile href="/templates/api-docs" title="API Docs Template">
  ![Template preview](/images/api-template.png)
</Tile>
```

---

## Tree, TreeFolder, TreeFile

File tree visualization with keyboard navigation.

**TreeFolder Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | string | — | Folder name (required) |
| `defaultOpen` | boolean | `false` | Start expanded |
| `openable` | boolean | `true` | Can be toggled |

**TreeFile Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | string | — | File name (required) |

```mdx
<Tree>
  <TreeFolder name="src" defaultOpen>
    <TreeFile name="index.ts" />
    <TreeFolder name="components">
      <TreeFile name="Button.tsx" />
      <TreeFile name="Card.tsx" />
    </TreeFolder>
  </TreeFolder>
  <TreeFile name="package.json" />
  <TreeFile name="docs.json" />
</Tree>
```

---

## Table, Row, Cell

Rich data tables with sorting, striping, and highlighting.

**Table Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `striped` | boolean | — | Alternating row colors |
| `compact` | boolean | — | Reduced padding |
| `bordered` | boolean | — | Full borders |
| `fullWidth` | boolean | `true` | 100% width |
| `caption` | string | — | Table caption |
| `captionVisible` | boolean | `false` | Show caption visually (otherwise screen-reader only) |
| `stickyHeader` | boolean | — | Sticky header on scroll |
| `sortable` | boolean | — | Enable column sorting |

**Row Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `header` | boolean | — | Header row |
| `highlight` | boolean | — | Highlight row |
| `highlightColor` | string | — | `primary`, `success`, `warning`, `error`, `info` |

**Cell Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `align` | string | `"left"` | `left`, `center`, `right` |
| `colSpan` | number | — | Column span |
| `rowSpan` | number | — | Row span |
| `header` | boolean | — | Render as `<th>` header cell |
| `highlight` | boolean | — | Highlight cell |
| `highlightColor` | string | — | `primary`, `success`, `warning`, `error`, `info` |

```mdx
<Table striped sortable>
  <Row header>
    <Cell>Parameter</Cell>
    <Cell>Type</Cell>
    <Cell>Description</Cell>
  </Row>
  <Row>
    <Cell>`apiKey`</Cell>
    <Cell>string</Cell>
    <Cell>Your API key</Cell>
  </Row>
  <Row highlight highlightColor="warning">
    <Cell>`secret`</Cell>
    <Cell>string</Cell>
    <Cell>Keep this private</Cell>
  </Row>
</Table>
```

Standard markdown tables also work:

```md
| Parameter | Type   | Description    |
|-----------|--------|----------------|
| `apiKey`  | string | Your API key   |
| `limit`   | number | Max results    |
```

---

## ParamField

API parameter documentation with type badges.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `body` | string | — | Body parameter name |
| `header` | string | — | Header parameter name |
| `query` | string | — | Query parameter name |
| `path` | string | — | URL path parameter name |
| `type` | string | — | Parameter type (string, number, boolean, etc.) |
| `required` | boolean | — | Required badge |
| `default` | string \| number \| boolean | — | Default value |

Only one of `body`, `header`, `query`, `path` should be set.

```mdx
<ParamField path="userId" type="string" required>
  The unique identifier of the user.
</ParamField>

<ParamField query="limit" type="number" default={25}>
  Maximum number of results to return (1–100).
</ParamField>

<ParamField body="email" type="string" required>
  The user's email address.
</ParamField>

<ParamField header="X-Api-Key" type="string" required>
  Your API key for authentication.
</ParamField>
```

---

## ResponseField

API response field documentation.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | string | — | Field name (required) |
| `type` | string | — | Field type |
| `required` | boolean | — | Required field |
| `deprecated` | boolean | — | Deprecated badge |
| `default` | string \| number \| boolean | — | Default value |

```mdx
<ResponseField name="id" type="string" required>
  Unique identifier for the resource.
</ResponseField>

<ResponseField name="created_at" type="string">
  ISO 8601 timestamp of creation.
</ResponseField>

<ResponseField name="legacy_id" type="number" deprecated>
  Use `id` instead.
</ResponseField>
```

---

## RequestExample & ResponseExample

Code blocks that render in the right sidebar panel on `api:` and `openapi:` pages.

> **Important:** On API pages, fenced code blocks (` ``` `) only move into the right-side code panel when wrapped in `<RequestExample>` or `<ResponseExample>` (or auto-rendered from an OpenAPI spec's `responses`). Bare fences stay inline in the prose column. The build emits an `inline_code_on_api_page` warning when an `api:` page has unwrapped code blocks — fix it by wrapping each example.

````mdx
<RequestExample>
```bash cURL
curl -X GET https://api.example.com/users \
  -H "Authorization: Bearer YOUR_KEY"
```
```javascript Node.js
const res = await fetch("https://api.example.com/users", {
  headers: { Authorization: "Bearer YOUR_KEY" }
});
```
</RequestExample>

<ResponseExample>
```json 200
{
  "users": [
    { "id": "usr_1", "name": "Alice" }
  ]
}
```
```json 401
{
  "error": "Invalid API key"
}
```
</ResponseExample>
````

**Wrong** — bare fences render inline in the prose column on an API page:

````mdx
---
title: Get Batch Status
api: 'GET /v1/calls/batch/{id}/status'
---

```bash
curl https://api.example.com/v1/calls/batch/abc/status
```

```json
{ "ok": true }
```
````

**Right** — wrapped fences render in the right-side code panel:

````mdx
---
title: Get Batch Status
api: 'GET /v1/calls/batch/{id}/status'
---

<RequestExample>

```bash
curl https://api.example.com/v1/calls/batch/abc/status
```

</RequestExample>

<ResponseExample>

```json
{ "ok": true }
```

</ResponseExample>
````

---

## ApiEndpoint

HTTP method badge with endpoint path.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `method` | string | — | `GET`, `POST`, `PUT`, `PATCH`, `DELETE`, `HEAD`, `OPTIONS` (required) |
| `path` | string | — | API path (required) |
| `baseUrl` | string | — | Base URL prefix |

```mdx
<ApiEndpoint method="GET" path="/users/:id" />
<ApiEndpoint method="POST" path="/users" baseUrl="https://api.example.com" />
```

---

## HttpMethodBadge

Standalone HTTP method badge — useful outside of ApiEndpoint.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `method` | string | — | `GET`, `POST`, `PUT`, `PATCH`, `DELETE` (required) |

```mdx
<HttpMethodBadge method="GET" /> `/users/:id`
<HttpMethodBadge method="POST" /> `/users`
```

---

## Images & Sizing

Standard markdown images auto-zoom on click:

```mdx
![Dashboard screenshot](/images/dashboard.png)
```

**Sized images** — append `=WIDTHxHEIGHT` to control dimensions:

```mdx
![Logo](/images/logo.png =200x50)
![Icon](/images/icon.png =32x32)
![Wide banner](/images/banner.png =800x)
```

Images are automatically wrapped in a zoomable container. Click to expand. Wrap in `<Frame>` to disable zoom.

---

## View, ViewProvider, ViewSelector, ViewWrapper

Framework/language switcher — persists selection across page.

**View Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | View identifier (required) |
| `icon` | string | — | Font Awesome icon or URL |
| `iconType` | string | — | Icon style |

**ViewProvider Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `defaultView` | string | — | Default view by title |

**ViewSelector** — renders the view toggle buttons. No props — placement determines position.

**ViewWrapper** — wraps content that should only appear when any view is active (hides when no view context exists).

```mdx
<ViewProvider defaultView="React">
  <ViewSelector />

  <View title="React" icon="react">
    ```jsx
    import { useEffect } from "react";
    ```
  </View>

  <View title="Vue" icon="vuejs">
    ```vue
    <script setup>
    import { onMounted } from "vue";
    </script>
    ```
  </View>

  <View title="Svelte">
    ```svelte
    <script>
    import { onMount } from "svelte";
    </script>
    ```
  </View>

  <ViewWrapper>
    This content appears when any view is selected.
  </ViewWrapper>
</ViewProvider>
```

---

## Color

Color palette display with two variants.

**Color Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | string | `"compact"` | `compact` or `table` |

**Color.Row Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `title` | string | — | Row heading text |

**Color.Item Props:**

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `name` | string | — | Color name |
| `value` | string \| object | — | Hex color or `{ light, dark }` (required) |

```mdx
<Color variant="table">
  <Color.Row title="Brand Colors">
    <Color.Item name="Primary" value="#635BFF" />
    <Color.Item name="Light" value="#7C75FF" />
    <Color.Item name="Dark" value="#4F46E5" />
  </Color.Row>
  <Color.Row title="Semantic">
    <Color.Item name="Success" value={{ light: "#16a34a", dark: "#22c55e" }} />
    <Color.Item name="Warning" value={{ light: "#d97706", dark: "#f59e0b" }} />
  </Color.Row>
</Color>
```

---

## Mermaid

Diagrams using Mermaid syntax.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `minWidth` | string | — | Minimum SVG width (e.g., `"700px"`) |

```mdx
<Mermaid>
graph LR
  A[User] --> B[Jamdesk CLI]
  B --> C[Build Service]
  C --> D[CDN]
  D --> E[Docs Site]
</Mermaid>
```

```mdx
<Mermaid>
sequenceDiagram
  Client->>API: POST /deploy
  API->>Builder: Queue build
  Builder->>CDN: Upload assets
  CDN-->>Client: Site live
</Mermaid>
```

---

## Update

Changelog entry with version label and tags.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `label` | string | — | Version or date label |
| `description` | string | — | Brief one-line summary |
| `tags` | string[] | — | Tags: `breaking`, `feature`, `fix`, `deprecation` |
| `date` | string | — | ISO date for RSS feed (e.g., `2025-03-15`) |

```mdx
<Update label="v2.0.0" date="2025-06-01" tags={["breaking", "feature"]} description="Major release">
  - **Breaking:** Removed legacy `v1` API endpoints
  - **Feature:** Added real-time webhooks
  - **Feature:** New dashboard analytics
</Update>

<Update label="v1.9.2" date="2025-05-15" tags={["fix"]} description="Bug fixes">
  - Fixed pagination offset in search results
  - Fixed dark mode rendering on code blocks
</Update>
```

---

## Widget

Drops a live "What's New" trigger into a docs page. Renders a button that opens your Jamdesk changelog (or any docs page) in a modal — the same widget customers embed in their own app, but as one MDX tag instead of a `<script>`. Resolves the canonical `*.jamdesk.app` origin automatically, so it works on subdomains and custom domains alike.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `page` | string | `/changelog` | Docs path the modal opens (a wrong path 404s the modal) |
| `label` | string | `What's new` | Trigger button text |
| `theme` | `auto` \| `light` \| `dark` | `auto` | Modal color scheme |
| `trigger` | CSS selector | — | Bind to your own element instead of rendering a button |
| `width` / `height` | CSS length | `560px` / `680px` | Modal size |
| `radius` | CSS length | `12px` | Modal corner radius |
| `unread` | boolean | `true` | Show the unread dot; set `false` for a demo button |
| `unreadColor` | hex / CSS color | `#e5484d` | Unread dot color |
| `project` | string | derived | Override the stored per-origin "seen" key |
| `className` | string | — | Extra classes for the rendered button |

```mdx
<Widget />

<Widget page="/reference/changelog" label="See what's new" unread={false} />

<Widget trigger="#whats-new" page="/changelog" />
```

The modal always loads from the `*.jamdesk.app` subdomain (the only origin that can render the embedded view). The unread "seen" state is per-browser and per-origin. To embed the widget in your own product with a `<script>` tag instead, see the Embed a Page guide.

---

## EmailSubscribe

Inline newsletter/changelog signup form. Native capture for seven providers (Jamdesk writes the subscriber to your connected audience); embed-only fallback for the rest. Connect the provider in the dashboard first (Settings → Email Signups).

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `provider` | string | — | `resend`, `mailchimp`, `kit`, `loops`, `beehiiv`, `brevo`, `sendgrid` (native) or `buttondown`, `substack` (embed-only) |
| `title` | string | — | Heading above the form |
| `description` | string | — | Supporting line under the heading |
| `collapsed` | boolean | `false` | Native only. Start as a compact Subscribe button that expands to the full field on click |
| `username` | string | — | Buttondown / Substack account username (embed-only providers) |
| `snippet` | string | — | Raw embed markup from any other provider (escape hatch) |
| `className` | string | — | Extra class on the wrapper |

```mdx
<EmailSubscribe provider="resend" />

<EmailSubscribe
  provider="resend"
  title="Get release notes"
  description="One email when we ship something new. No spam."
/>

<EmailSubscribe provider="resend" collapsed title="Subscribe to updates" />

<EmailSubscribe provider="substack" username="acme" />
```

**Native vs. embed:** native providers (`resend`, `mailchimp`, `kit`, `loops`, `beehiiv`, `brevo`, `sendgrid`) render a Jamdesk-hosted form and need a connected key. Embed-only providers (`buttondown`, `substack`) render that service's own form from a `username` — no key. A native provider named without a dashboard connection won't capture anything.

**Returning subscribers:** after a reader subscribes through a native form, the browser remembers it (in `localStorage`) and shows *You're subscribed to the newsletter.* on the next visit, with a "Use a different email?" control to reopen the form. Automatic — nothing to configure.

To mount the form on every changelog page automatically instead of per-page, set `integrations.newsletter.placement: "changelog"` in `docs.json` (see configuration reference).

---

## YouTube

Embedded YouTube video with lazy loading.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `id` | string | — | YouTube video ID (required) |
| `title` | string | — | Accessibility label |
| `start` | number | — | Start time in seconds |

```mdx
<YouTube id="dQw4w9WgXcQ" title="Getting Started Tutorial" start={30} />
```

---

## Video

Self-hosted video player.

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `src` | string | — | Video URL — `.mp4` or `.webm` (required) |
| `title` | string | — | Accessibility label |
| `controls` | boolean | `true` | Show player controls |
| `autoPlay` | boolean | — | Auto-play (pair with `muted`) |
| `muted` | boolean | — | Mute audio |
| `loop` | boolean | — | Loop playback |
| `width` | string | — | Video width |
| `height` | string | — | Video height |

```mdx
<Video src="/videos/demo.mp4" autoPlay muted loop />
<Video src="https://cdn.example.com/tutorial.mp4" title="Setup walkthrough" />
```

---

## Latex

Mathematical expressions via MathJax.

```mdx
Inline math: <Latex>E = mc^2</Latex>

Block math:
<Latex>
\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
</Latex>
```

Requires `styling.latex: true` in `docs.json` if not auto-detected.

---

## Reusable Snippets

Create reusable MDX fragments in `snippets/` directory:

**`snippets/install-tabs.mdx`:**
````mdx
<CodeGroup>
```bash npm
npm install my-sdk
```
```bash yarn
yarn add my-sdk
```
</CodeGroup>
````

**Usage in any page:**
```mdx
import InstallTabs from '/snippets/install-tabs.mdx';

<InstallTabs />
```

For client-side components (with hooks or state), add `'use client'` at the top of the snippet file.
