---
name: reddit-marketing
description: Market a product on Reddit with the MediaFast MCP. Finds subreddits where the product can be promoted, drafts posts in the format each subreddit accepts, finds threads worth commenting on, checks for shadowbans and builds a growth roadmap. Use when the user wants Reddit traffic, users or sales for their app, SaaS or website.
---

# Reddit marketing with MediaFast

This skill uses the MediaFast MCP server (https://www.mediafa.st) to do Reddit marketing for the user's product.

## Setup

The MCP server lives at `https://api.mediafa.st/mcp` and uses a bearer API key.

1. Sign in at https://www.mediafa.st and create an API key in Dashboard, Settings, API keys.
2. Connect it. For Claude Code:

```bash
claude mcp add --transport http mediafast https://api.mediafa.st/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

Other MCP clients (Cursor, Windsurf, VS Code and others) take the same URL and header in their MCP config.

If the MediaFast tools are not available in the session, stop and walk the user through the setup above before doing anything else.

## Tools

| Tool | Use it to |
|------|-----------|
| `list_projects` | See the user's saved MediaFast projects |
| `find_subreddits` | Find subreddits where the product can be promoted |
| `generate_reddit_post` | Draft a post in the format a subreddit accepts |
| `find_comment_opportunities` | Find threads worth replying to and what to say |
| `get_growth_roadmap` | Get a day by day Reddit plan |
| `check_shadowban` | Check if a Reddit account is shadowbanned |

## Workflow

1. Call `list_projects`. If the product is already saved, use its project. If not, ask for the website URL and a one line description.
2. Call `check_shadowban` on the user's Reddit username before anything is posted.
3. Call `find_subreddits` and show the list with why each one fits.
4. For the subreddits the user picks, call `generate_reddit_post` and show each draft.
5. Call `find_comment_opportunities` and show which threads to reply to and how.
6. Call `get_growth_roadmap` to turn it into a daily plan.

## Rules

- Never post to Reddit on the user's behalf. Show drafts, the user posts them.
- Keep the post format each subreddit expects. Do not turn a story post into a link drop.
- In threads that do not allow promotion, the reply gives value only, no product mention.
