# Apify Agent Skills

A collection of AI agent skills for web scraping, data extraction, and Actor development on the Apify platform.

> Looking for more specialized skills? Check out [apify/awesome-skills](https://github.com/apify/awesome-skills) — a community collection of domain-specific skills for lead generation, brand monitoring, competitor intelligence, and more.
>
> Using Cursor? See [apify/cursor-plugins](https://github.com/apify/cursor-plugins) for ready-to-install Cursor marketplace plugins.

## Skills

### `apify-ultimate-scraper`

Universal AI-powered web scraper for 55+ platforms. Scrape data from Instagram, Facebook, TikTok, YouTube, Google Maps, Amazon, Walmart, eBay, Booking.com, TripAdvisor, and more.

**Use cases**: lead generation, brand monitoring, competitor analysis, influencer discovery, trend research, content analytics, audience analysis, e-commerce pricing, reviews.

### `apify-actor-development`

Create, debug, and deploy Apify Actors from scratch in JavaScript, TypeScript, or Python.

### `apify-actorization`

Convert existing projects into Apify Actors — supports JS/TS (SDK), Python (async context manager), and any language (CLI wrapper).

## Usage

Any AI tool that supports Markdown context can use these skills by pointing to the SKILL.md files:

- `skills/apify-ultimate-scraper/SKILL.md`
- `skills/apify-actor-development/SKILL.md`
- `skills/apify-actorization/SKILL.md`

For Codex and Gemini CLI, use the auto-generated index at `agents/AGENTS.md`.

## Prerequisites

1. **Apify account** — [apify.com](https://apify.com)
2. **API token** — get from [Apify Console](https://console.apify.com/account/integrations), add `APIFY_TOKEN=your_token` to `.env`
3. **Node.js 20.6+** (for the scraper skill)

## Pricing

Apify Actors use pay-per-result pricing. Check individual Actor pricing on the [Apify platform](https://apify.com).

## Support

- [Apify Documentation](https://docs.apify.com)
- [Apify Discord](https://discord.gg/jyEM2PRvMU)

## License

[Apache-2.0](LICENSE)
