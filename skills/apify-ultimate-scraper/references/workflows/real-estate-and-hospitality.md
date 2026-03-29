# Real estate and hospitality workflows

## Property search and analysis
**When:** User wants to find and compare property listings in a specific area.

### Pipeline
1. **Search properties** -> `tri_angle/redfin-search`
   - Key input: `location`, `propertyType`, `minPrice`, `maxPrice`
2. **Get details** -> `tri_angle/redfin-detail`
   - Pipe: `results[].url` -> `startUrls`
   - Key input: `startUrls`

### Output fields
Step 1: `address`, `price`, `beds`, `baths`, `sqft`, `url`, `status`
Step 2: `description`, `yearBuilt`, `lotSize`, `priceHistory[]`, `taxHistory[]`, `schools[]`

## Airbnb market analysis
**When:** User wants to analyze Airbnb listings, pricing, and reviews in a destination.

### Pipeline
1. **Search listings** -> `tri_angle/new-fast-airbnb-scraper`
   - Key input: `location`, `checkIn`, `checkOut`, `maxItems`
2. **Get reviews** -> `tri_angle/airbnb-reviews-scraper`
   - Pipe: `results[].url` -> `startUrls`
   - Key input: `startUrls`, `maxReviews`

### Output fields
Step 1: `name`, `price`, `rating`, `reviews`, `type`, `amenities[]`, `url`, `images[]`
Step 2: `text`, `rating`, `date`, `reviewerName`

### Gotcha
Airbnb pricing varies by date. Always set `checkIn` and `checkOut` for accurate pricing. For market analysis, run multiple date ranges to capture seasonal variation.

## Multi-source property comparison
**When:** User wants to compare listings across Zillow, Realtor, Zumper, and other US/UK sources.

### Pipeline
1. **Aggregate listings** -> `tri_angle/real-estate-aggregator`
   - Key input: `location`, `propertyType`, `sources` (Zillow, Realtor, Zumper, Apartments.com, Rightmove)

### Output fields
Step 1: `address`, `price`, `beds`, `baths`, `sqft`, `source`, `url`, `listingDate`
