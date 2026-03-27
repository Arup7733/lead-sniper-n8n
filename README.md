# lead-sniper-n8n
Automated GitHub high-value lead tracker using n8n(Tested
# Lead Sniper — n8n Workflow

An automated "High-Value Lead" tracker that monitors GitHub repository 
stargazers and sends enriched lead info to Discord using AI-generated pitches.

## Workflow Overview
- Polls GitHub every 15 minutes for new stargazers
- Enriches each user profile via GitHub /users/{username} API
- Filters users with followers > 100 OR public_repos > 50
- Uses GPT-4o-mini to generate a 1-sentence sales pitch
- Posts formatted message to Discord webhook

## Files
`My workflow(3).json` — n8n workflow (import this directly into n8n)
`screenshot(44).png` — successful Discord output

## Logic Log — GitHub API Rate Limit Handling

- Used a Personal Access Token in the `Authorization` header  
  → bumps limit from 60 to 5,000 requests/hour
- Schedule trigger set to every 15 minutes (~96 calls/hour max)
- Used `Accept: application/vnd.github.v3.star+json` header  
  → returns `starred_at` timestamp to detect only NEW stars
- Added a Limit node in n8n during testing to cap OpenAI calls
- If rate limit is hit, n8n returns a 403 — handled by checking  
  `X-RateLimit-Remaining` header before proceeding

## Tools Used
- n8n (workflow automation)
- GitHub REST API
- OpenAI GPT-4o-mini
- Discord Webhook
```

Step 4— Click Commit changes

Part 6—submission links

After all uploads, you'll have these two links to submit:

Repo link (the main link):

(https://github.com/Arup7733/lead-sniper-n8n)

Direct JSON file link:
(https://github.com/Arup7733/lead-sniper-n8n/blob/main/My%20workflow%20(3).json)

