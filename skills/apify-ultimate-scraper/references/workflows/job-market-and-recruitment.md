# Job market and recruitment workflows

## Job listing research
**When:** User wants to find and analyze job postings by role, company, or location.

### Pipeline
1. **Search jobs** -> `harvestapi/linkedin-job-search`
   - Key input: `keyword`, `location`, `datePosted`, `limit`
2. **Get job details** -> `apimaestro/linkedin-job-detail`
   - Pipe: `results[].jobUrl` -> `urls`
   - Key input: `urls`

### Output fields
Step 1: `title`, `company`, `location`, `jobUrl`, `postedDate`, `applicantsCount`
Step 2: `description`, `requirements`, `seniority`, `employmentType`, `salary`

### Gotcha
Both Actors are PPE. Step 1: ~$0.001/job. Step 2: ~$0.005/job. For 200 jobs, total ~$1.20. Estimate and confirm with user.

## Candidate sourcing
**When:** User wants to find potential candidates matching specific criteria.

### Pipeline
1. **Search profiles** -> `harvestapi/linkedin-profile-search`
   - Key input: `keyword`, `title`, `location`, `industry`, `limit`
2. **Enrich with details** -> `apimaestro/linkedin-profile-full-sections-scraper`
   - Pipe: `results[].profileUrl` -> `urls`
   - Key input: `urls`

### Output fields
Step 1: `fullName`, `headline`, `location`, `profileUrl`, `currentCompany`
Step 2: `experience[]`, `education[]`, `skills[]`, `certifications[]`, `languages[]`

### Gotcha
Step 2 (`apimaestro/linkedin-profile-full-sections-scraper`) costs ~$0.01/profile - the most expensive LinkedIn scraper. Use sparingly for shortlisted candidates only.

## GitHub contributor discovery
**When:** User wants to find developers who contribute to specific open-source projects.

### Pipeline
1. **Get contributors** -> `janbuchar/github-contributors-scraper`
   - Key input: `repoUrls`

### Output fields
Step 1: `username`, `contributions`, `profileUrl`, `avatarUrl`
