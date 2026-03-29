# Social media analytics workflows

## Instagram account performance analysis
**When:** User wants engagement metrics and content performance for an Instagram account.

### Pipeline
1. **Get profile** -> `apify/instagram-profile-scraper`
   - Key input: `usernames`
2. **Get recent posts** -> `apify/instagram-post-scraper`
   - Key input: `directUrls` (from profile's `latestPosts[].url`) or `usernames`

### Output fields
Step 1: `followersCount`, `followsCount`, `postsCount`, `biography`, `isVerified`
Step 2: `caption`, `likesCount`, `commentsCount`, `timestamp`, `type` (photo/video/reel), `url`

## TikTok creator analytics
**When:** User wants performance data for a TikTok creator.

### Pipeline
1. **Get profile** -> `clockworks/tiktok-profile-scraper`
   - Key input: `profiles` (handles or URLs)

### Output fields
Step 1: `nickname`, `followers`, `following`, `likes`, `videos`, `verified`, `recentVideos[]` (with views, likes, shares per video)

## Multi-platform engagement comparison
**When:** User wants to compare an account's performance across platforms.

### Pipeline (run independently, combine)
1. **Instagram** -> `apify/instagram-profile-scraper` with `usernames`
2. **TikTok** -> `clockworks/tiktok-profile-scraper` with `profiles`
3. **YouTube** -> `streamers/youtube-channel-scraper` with `channelUrls`
4. **X/Twitter** -> `apidojo/twitter-user-scraper` with `handles`

### Output fields
Instagram: `followersCount`, `postsCount`, `biography`
TikTok: `followers`, `likes`, `videos`
YouTube: `subscriberCount`, `videoCount`, `viewCount`
X/Twitter: `followers`, `tweets`, `likes`

### Gotcha
Parallel workflow - run each Actor independently. Normalize metric names for comparison (followers/subscribers, posts/videos/tweets).
