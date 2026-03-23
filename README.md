# Atypica.AI Development Skills

A collection of AI agent skills for common software development tasks. Built for developers and technical founders who want AI coding agents to handle repetitive, error-prone engineering workflows — database management, schema tooling, and more. Works with Claude Code, OpenAI Codex, Cursor, Windsurf, and any agent that supports the [Agent Skills spec](https://agentskills.io).

Built by the [Atypica.AI](https://atypica.ai) team. Atypica.AI is a consumer intelligence platform powered by the same stack these skills were born from — these workflows come directly from building and maintaining production systems at scale. [Try Atypica.AI →](https://atypica.ai)

**Contributions welcome!** Have a dev workflow that would make a good skill? [Open a PR](#contributing).

Run into a problem or have a question? [Open an issue](https://github.com/atypica-ai/development-skills/issues) — we're happy to help.

## What are Skills?

Skills are markdown files that give AI agents specialized knowledge and workflows for specific tasks. When you add these to your project, your agent can recognize when you're working on a known engineering task and apply the right steps, commands, and safeguards automatically — without you having to explain the process every time.

## Available Skills

<!-- SKILLS:START -->
| Skill | Description |
|-------|-------------|
| [prisma-migrate-squash](skills/prisma-migrate-squash/) | Squash all Prisma migrations into a single clean init migration. Use when the migration folder is cluttered, onboarding new devs, or preparing a major release. Handles the full workflow: detecting your schema, generating a timestamp, running `migrate diff`, flagging manual fixes needed (e.g. pgvector HNSW indexes), and marking the migration as applied across environments. |
<!-- SKILLS:END -->

## Installation

### Option 1: Clone and Copy (Recommended)

```bash
git clone https://github.com/atypica-ai/development-skills.git
cp -r development-skills/skills/* .agents/skills/
```

For Claude Code, also copy into `.claude/skills/`:

```bash
mkdir -p .claude/skills
cp -r development-skills/skills/* .claude/skills/
```

### Option 2: Git Submodule

Add as a submodule for easy updates:

```bash
git submodule add https://github.com/atypica-ai/development-skills.git .agents/development-skills
```

Then reference skills from `.agents/development-skills/skills/`.

### Option 3: Fork and Customize

1. Fork this repository
2. Customize skills for your stack or team conventions
3. Clone your fork into your projects

### Option 4: npx skills (if using Agent Skills CLI)

```bash
# Install all skills
npx skills add atypica-ai/development-skills

# Install a specific skill
npx skills add atypica-ai/development-skills --skill prisma-migrate-squash

# List available skills
npx skills add atypica-ai/development-skills --list
```

## Usage

Once installed, just describe what you need — your agent will recognize the task and apply the right skill:

```
"My prisma/migrations folder has 60 migrations, squash them"
→ Uses prisma-migrate-squash skill

"Clean up migration history before the v2 release"
→ Uses prisma-migrate-squash skill

"Reset migration files and create a fresh init"
→ Uses prisma-migrate-squash skill
```

You can also invoke skills directly:

```
/prisma-migrate-squash
```

## Contributing

Have a dev workflow that your agent handles repeatedly? Turn it into a skill and share it.

### Adding a new skill

1. Create a folder under `skills/` using kebab-case
2. Add a `SKILL.md` with YAML frontmatter:
   ```yaml
   ---
   name: your-skill-name
   description: One sentence describing when this skill should trigger.
   ---
   ```
3. Write clear trigger conditions, step-by-step workflow, common pitfalls, and a verification step
4. Update the skills table in this README
5. Open a PR with a brief description of the workflow and why it's useful to automate

### Improving an existing skill

- Fix outdated commands or flags
- Add edge cases and troubleshooting entries
- Improve the trigger description for better agent detection
- Open a PR with your change and rationale

## License

[MIT](LICENSE) — Use these however you want.
