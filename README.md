# AI News Digest Automation

## Project Title
Automated Daily AI News Digest using n8n and LLM

## Objective
To automatically collect the latest AI news every morning, summarize the most important stories with a Large Language Model, and deliver them as a clean HTML email at 7 AM, with no manual work.

## Workflow

```
Schedule Trigger -> RSS Read -> Limit -> Aggregate -> Basic LLM Chain -> Gmail
```

| Node | Purpose |
|------|---------|
| Schedule Trigger | Starts the workflow daily at 7 AM |
| RSS Read | Fetches the last 24 hours of AI news from Google News RSS |
| Limit | Keeps the latest 10 items |
| Aggregate | Combines all items into one `data` array |
| Basic LLM Chain | Sends the news to the LLM with the prompt in `prompt.txt` |
| Gmail (Send a message) | Emails the generated HTML digest |

## Features

- Fully automated daily delivery
- Picks the 5 most important, distinct stories
- Headline, short summary, key takeaway, and source link for each story
- Strict prompt rules: use only facts from the news data, never invent links
- Fixed HTML template for a consistent, readable email

## Technologies Used

- n8n (workflow automation)
- Large Language Model (via Basic LLM Chain)
- Google News RSS
- Gmail
- HTML and CSS (email layout)
- Prompt Engineering

## Project Files

| File | Description |
|------|-------------|
| `workflow.json` | Exported n8n workflow (credentials removed) |
| `prompt.txt` | Final prompt used in the Basic LLM Chain |
| `screenshots/` | Workflow and email output screenshots |
| `README.md` | Project documentation |

## Run Project

1. Open n8n and import `workflow.json` (Workflows -> Import from file).
2. Add a chat model node (for example Gemini or OpenAI) and connect it to the Basic LLM Chain node with your own API credentials.
3. In the Gmail node, connect your Gmail account and replace `your-email@example.com` with your address.
4. Set the Schedule Trigger to 7:00 AM in your timezone.
5. Click "Execute workflow" to test, then switch the workflow to Active.

## Future Improvements

- Remove stray code fences from the model output with a Code node
- Summaries in Telugu or other languages
- Multiple subscribers
- Telegram or WhatsApp delivery
- Store past digests in a database

## Note
News content belongs to the original publishers. This project only summarizes headlines and links back to the sources.

## Author
Marpudi Manasa
