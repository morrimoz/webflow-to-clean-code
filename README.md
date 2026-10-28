# Webflow to clean code

**Category: Web migration | Format: Agent skill**

A repeatable workflow for converting Webflow-exported pages into self-contained HTML, CSS and JavaScript. It guides an AI coding agent through removing Webflow runtime dependencies while preserving the page's appearance and behaviour.

This repository contains instructions for an agent. It is not a standalone converter.

## When to use it

Use it when moving an exported site to another host, taking ownership of generated code or replacing Webflow-specific interactions with maintainable JavaScript.

| Input | Work performed | Output |
| --- | --- | --- |
| Exported HTML, styles, scripts and assets | Inventory dependencies, replace interactions, reorganise styles and verify the result | Static files that can be reviewed and hosted independently |

## Install

For Cursor, clone into the personal skills directory:

```bash
mkdir -p ~/.cursor/skills
git clone https://github.com/morrimoz/webflow-to-clean-code.git ~/.cursor/skills/webflow-to-clean-code
```

For a shared project skill, use `.cursor/skills/webflow-to-clean-code` as the destination. Other agents can read [SKILL.md](SKILL.md) directly. Start a new agent session after installation.

## Example request

```text
Use webflow-to-clean-code on the exported site in site-export/.
Keep the design, replace Webflow interactions and verify navigation and forms.
```

The workflow inventories the export, removes coupling, reorganises CSS, replaces JavaScript interactions, resolves assets and checks the rendered pages.

## Verification and limits

Search the output for remaining runtime dependencies. Replace `site-output` with the actual output folder:

```bash
rg -n 'webflow\.js|webflow\.css|webflow\.io|uploads-ssl\.webflow\.com|data-wf-page|data-wf-site' site-output
```

No matches is one check, not proof that the migration works. Compare layouts at desktop and mobile sizes, exercise keyboard navigation and test every interaction. Forms, CMS behaviour, hosting rules and external services may need separate replacements.

There is no bundled before/after site or automated migration benchmark. Results depend on the export, the coding agent and verification.

## Related tools

- [Plan to execution plan](https://github.com/morrimoz/plan-to-execution-plan) - Organise a larger migration into bounded implementation steps.
- [Deploy dash normalizer](https://github.com/morrimoz/cursor-skill-normalize-deploy-dashes) - Apply a text convention before static deployment.

[MIT license](LICENSE)
