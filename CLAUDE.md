This repository contains official Apify agent skills for web scraping, data extraction, and automation.

## Structure

- `skills/apify-ultimate-scraper/` - Universal web scraper skill (55+ platforms)
- `skills/apify-actor-development/` - Actor development skill (JS/TS/Python)
- `skills/apify-actorization/` - Actorization skill (convert projects to Actors)
- `agents/AGENTS.md` - Auto-generated skill index for Codex/Gemini CLI
- `scripts/generate_agents.py` - Script to regenerate AGENTS.md

## Development

Run `uv run scripts/generate_agents.py` to regenerate `agents/AGENTS.md`.

## Committing Changes

Use conventional commit messages (feat:, fix:, docs:, chore:, etc.).

## Apify MCP

APIFY_TOKEN could be found in `.env` file

You've got also access to Apify MCP server - it could be useful if you need to search or reach for Apify Actors and it's input schemas

IMPORTANT: always use name of Apify Actors in format "author/Actor" (never "author~Actor")
