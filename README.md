# AI News Reporter

A Claude skill that fetches the latest AI & tech news from the last 24 hours and turns it into ready-to-publish summaries — blog posts, social media content, or quick briefings — in your tone of voice.

## What it does

Given a format (and optionally a topic), the skill:

1. Browses a curated set of news sources
2. Picks the most relevant AI stories from the past 24 hours
3. Writes a summary in the requested format, applying the tone-of-voice guidance in `references/tone-of-voice-example.md`
4. Saves the output to `./outputs/` as a dated markdown file

## Sources

News is gathered only from:

- [TechCrunch](https://techcrunch.com/)
- [Hacker News](https://news.ycombinator.com/)
- [Product Hunt](https://www.producthunt.com/)
- [TLDR](https://tldr.tech/)

## Output formats

| Format | Length | Best for |
|---|---|---|
| `General briefing` (default) | Short, structured | Quick-read updates |
| `blog` | 800–1200 words | Longer narrative posts |
| `LinkedIn` | 350–500 words | Professional posts |
| `Twitter/X` | ≤280 chars or short thread | Punchy updates |
| `General social` | 100–200 words | Cross-platform |
| Custom | As described | Anything else |

## Usage

The skill is invoked via Claude Code:

```
/ai-news-reporter [format] [topic (optional)]
```

Examples:

```
/ai-news-reporter blog
/ai-news-reporter LinkedIn open-source models
/ai-news-reporter
```

Generated files land in `./outputs/` with names like `16-april-2026-blog.md`.

## Requirements

- [Claude Code](https://claude.com/claude-code)
- `browse` skill (used for fetching news); `browse-stealth` as a fallback for sites that block automated browsing
- Node.js (for the `@ulpi/browse` dependency)

Install dependencies:

```
npm install
```

## Project layout

```
.claude/skills/ai-news-reporter/   # The skill definition
  SKILL.md                         # Instructions Claude follows
  references/
    tone-of-voice-example.md       # Tone guide — customize to yours
outputs/                           # Generated summaries
```

## Customizing tone of voice

Edit `.claude/skills/ai-news-reporter/references/tone-of-voice-example.md` to match how you write. The skill will apply that tone to every generated piece.

## Walkthrough & troubleshooting

For a step-by-step walkthrough of how this skill was built, plus troubleshooting tips, check out **The Casual Leader Podcast**:

- YouTube: https://www.youtube.com/@TheCasualLeader
- Spotify: https://open.spotify.com/show/57e5ggqj77yVEDAwlrgHgT
