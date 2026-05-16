# Webflow → Clean Code (Cursor Agent Skill)

A [Cursor Agent Skill](https://cursor.com/docs/context/skills) that guides AI agents through converting Webflow-exported HTML/CSS/JS into clean, self-contained static code—no `webflow.js`, no Webflow CDN assets, no `.w-*` class dependencies.

## What it does

When you import a Webflow export or migrate a page off Webflow, this skill walks the agent through:

1. **Inventory** — map structure to keep vs. simplify
2. **Strip coupling** — remove Webflow scripts, CDN links, `data-wf-*` attributes, and utility classes
3. **Styles** — rename `*.webflow.css`, reorganize into your project’s CSS
4. **JavaScript** — reimplement tabs, sliders, forms without `webflow.js`
5. **Assets** — copy images/Lottie into your project and fix paths
6. **Verify** — grep checks and manual QA before calling it done

## Install

### Option A — Clone into your skills folder (recommended)

**Personal skill** (all projects):

```bash
git clone https://github.com/morrimoz/webflow-to-clean-code.git ~/.cursor/skills/webflow-to-clean-code
```

**Project skill** (this repo only):

```bash
git clone https://github.com/morrimoz/webflow-to-clean-code.git .cursor/skills/webflow-to-clean-code
```

### Option B — Copy manually

1. Download or clone this repository.
2. Copy the folder into `~/.cursor/skills/webflow-to-clean-code/` (personal) or `.cursor/skills/webflow-to-clean-code/` (project).
3. Ensure the path ends with `webflow-to-clean-code/SKILL.md`.

Restart Cursor or start a new agent session so the skill is picked up.

## Usage

The skill applies automatically when you mention things like:

- “Webflow export”
- “leaving Webflow”
- “strip webflow.js”
- “clean up this Webflow page”

You can also invoke it explicitly: *“Use the webflow-to-clean-code skill on this export.”*

## Verification snippet

After migration, run from your project root (adjust paths as needed):

```bash
grep -rn \
  "webflow\.js\|webflow\.css\|webflow\.io\|uploads-ssl\.webflow\.com\|d3e54v103j8qbb\|w-inline-block\|w-clearfix\|w-container\|w--current\|w--tab-active\|data-wf-page\|data-wf-site\|generator.*Webflow" \
  ./public ./src ./pages ./app 2>/dev/null || echo "Clean!"
```

## License

MIT — see [LICENSE](LICENSE).

## Contributing

Issues and PRs welcome. If you have Webflow migration patterns that aren’t covered, open an issue or PR with a concrete example.
