# Personal api token for github may/maynot be working in some cases , if this error happens then create a api token from github and add it in http1 under headers(value) add that link after the token and it will start working.
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

## Workflow Link -- https://lucid.app/lucidchart/7f5e4e8e-91d6-4abc-9b9b-4c3172ece84d/edit?viewport_loc=-53%2C112%2C1663%2C861%2C0_0&invitationId=inv_4782f2b8-3461-41d1-b949-0de10ef89530

Part 6—submission links

Repo link (the main link):

(https://github.com/Arup7733/lead-sniper-n8n)

Direct JSON file link:
(https://github.com/Arup7733/lead-sniper-n8n/blob/main/My%20workflow%20(3).json)

