# Trend and keyword research workflows

## Google Trends analysis
**When:** User wants to analyze search demand trends for keywords or topics.

### Pipeline
1. **Get trend data** -> `apify/google-trends-scraper`
   - Key input: `searchTerms`, `timeRange`, `geo` (country code)

### Output fields
Step 1: `term`, `timelineData[]` (date, value), `relatedQueries[]`, `relatedTopics[]`

## Cross-platform hashtag research
**When:** User wants to evaluate a hashtag's reach and usage across platforms.

### Pipeline
1. **Cross-platform overview** -> `apify/social-media-hashtag-research`
   - Key input: `hashtags`, `platforms` (instagram, youtube, tiktok, facebook)

### Output fields
Step 1: `hashtag`, `platform`, `postsCount`, `topPosts[]`, `relatedHashtags[]`

## TikTok trend discovery
**When:** User wants to find trending content, sounds, or hashtags on TikTok.

### Pipeline
1. **Trending content** -> `clockworks/tiktok-trends-scraper`
   - Key input: `channel` (trending category)
2. **Explore categories** -> `clockworks/tiktok-explore-scraper`
   - Key input: `exploreCategories`

### Output fields
Step 1: `videoUrl`, `description`, `likes`, `shares`, `views`, `author`, `music`
Step 2: `category`, `posts[]`, `authors[]`, `music[]`

## Content topic validation
**When:** User wants to validate whether a topic has demand before creating content.

### Pipeline
1. **Search demand** -> `apify/google-trends-scraper`
   - Key input: `searchTerms` (topic keywords)
2. **Social reach** -> `apify/social-media-hashtag-research`
   - Key input: `hashtags` (topic hashtags)

### Output fields
Step 1: `timelineData[]` (trending up/down), `relatedQueries[]`
Step 2: `postsCount` per platform, `topPosts[]`

### Gotcha
Google Trends shows relative interest (0-100 scale), not absolute volume. Combine with hashtag post counts for a fuller picture.
