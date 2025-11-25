# Happiness Dashboard Template

Build interactive data dashboards using Evidence framework - write SQL queries in markdown to create visualizations.

## Tech Stack

- Evidence
- DuckDB
- PostgreSQL
- Svelte

---

# Skills

Skills are specialized instruction files that guide code agents through specific workflows. They are located in `.claude/skills/` directory.

## Available Skills

| Skill | Path | Description |
|-------|------|-------------|
| build-and-deploy | `.claude/skills/build-and-deploy/SKILL.md` | Build and deploy this Evidence framework project. Use when building, deploying, or setting up the happiness dashboard project. |

## For Claude Code Users

Skills are automatically available in Claude Code. Simply describe what you want to do (e.g., "deploy this app") and Claude Code will use the appropriate skill.

## For Other Code Agents

If you're using a different code agent (Cursor, Windsurf, Cline, etc.), you can still benefit from skills:

1. **Read the skill file directly** - Open the SKILL.md file at the path listed above
2. **Follow the instructions** - The skill file contains step-by-step workflow instructions
3. **Use as context** - Copy the skill content into your agent's context when performing that task

Example: To deploy this app, read `.claude/skills/build-and-deploy/SKILL.md` and follow the workflow steps.
