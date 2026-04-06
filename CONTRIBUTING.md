# Contributing

This plugin evolves with Jamdesk. If you notice outdated component docs, missing CLI commands, or new configuration options:

1. Check the latest Jamdesk docs at [jamdesk.com/docs](https://www.jamdesk.com/docs)
2. Open an issue describing the gap
3. Submit a PR updating the relevant reference file

## Reference File Guidelines

- **components.md** — One section per component. Include all props with types, defaults, and a working example
- **configuration.md** — Mirror the docs.json schema. Show JSON examples for every option
- **navigation.md** — One section per pattern. Include a complete JSON example and a "Best for" note

## Style

- Use tables for props (columns: Prop, Type, Default, Description)
- Always include a code example — never document a component without one
- Keep descriptions concise — one sentence per prop
- Test examples against the current Jamdesk CLI before submitting
