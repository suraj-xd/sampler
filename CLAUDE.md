# Sampler — AI-Curated Resource Hub

## Config

- **Timezone**: Asia/Kolkata

## What This Repo Is

A single, curated feed of everything happening in AI — tools, launches, prompts, tips, resources, and reads. Content is shared via Claude Code, formatted beautifully into markdown, committed, and pushed to GitHub.

## Directory Structure

```
sampler/
├── README.md          # Landing page — shows latest drops
├── CLAUDE.md          # This file
├── tools/             # AI tools, apps, platforms
├── launches/          # New products, releases, announcements
├── prompts/           # Prompts, techniques, workflows
├── tips/              # Quick wins, tricks, insights
├── resources/         # Courses, docs, hidden gems, websites
└── reads/             # Articles, threads, videos worth consuming
```

## How to Capture Content

When the user shares something (a link, tweet, tool, video, image, thought), follow this process:

### 1. Determine the category

| Category | When to use |
|----------|------------|
| `launches/` | New product, release, announcement, beta launch |
| `tools/` | AI tool, app, platform, extension, API |
| `prompts/` | Prompt, technique, workflow, system prompt |
| `tips/` | Quick insight, trick, hack, lesson learned |
| `resources/` | Course, doc, guide, hidden gem, website, collection |
| `reads/` | Article, thread, video, podcast, essay |

### 2. Create the file

- **Filename**: `<category>/YYYY-MM-DD_slug.md` (e.g., `tools/2026-03-29_cursor-agent-mode.md`)
- **Slug**: short, descriptive, lowercase, hyphenated
- **Date**: current date in YYYY-MM-DD format

### 3. Format based on content type

#### For a Link / Website / Article

Fetch the URL with WebFetch to understand the content, then write:

```markdown
---
date: YYYY-MM-DD
source: <URL>
tags: [relevant, tags]
---

# Title

> One-line hook — why should someone care about this?

**Link**: [Title](URL)

## What it is

<2-4 sentences explaining what this is, in plain language>

## Why it matters

<1-3 sentences on why this is interesting, useful, or worth knowing about>

## Key takeaways

- <bullet points of the most important things>
- <keep it scannable>
- <no fluff>
```

#### For a YouTube Video

Fetch the video page to get title/description, then write:

```markdown
---
date: YYYY-MM-DD
source: <YouTube URL>
tags: [relevant, tags]
---

# Title

> One-line hook

**Video**: [Title](URL)
**Channel**: <channel name>
**Length**: <duration>

## TL;DW (Too Long; Didn't Watch)

<The key points from this video distilled into a 1-2 minute read. This is the whole point — saving people from watching the full video.>

## Key takeaways

- <bullet points>
- <the actual useful bits>
```

#### For a Tweet / Thread

```markdown
---
date: YYYY-MM-DD
source: <tweet URL>
tags: [relevant, tags]
---

# <Topic of the tweet>

> One-line hook

**Thread**: [<@handle>](tweet URL)

## What they said

<Capture the core content of the tweet/thread. Format it clearly.>

## Why it matters

<1-2 sentences on context or significance>
```

#### For a Tool / Product

```markdown
---
date: YYYY-MM-DD
source: <URL>
tags: [relevant, tags]
---

# Tool Name

> One-line description

**Link**: [Tool Name](URL)
**Category**: <what kind of tool — coding, writing, design, etc.>
**Pricing**: <free / freemium / paid / open-source>

## What it does

<2-4 sentences in plain language>

## Who it's for

<1-2 sentences on the target user>

## Why it's interesting

<What makes this worth knowing about — what's unique or impressive>
```

#### For a Prompt / Technique

```markdown
---
date: YYYY-MM-DD
tags: [relevant, tags]
---

# Title

> One-line description of what this prompt/technique achieves

## The Prompt

```
<the actual prompt or technique, formatted as code>
```

## How to use it

<Brief explanation of when and how to use this>

## Why it works

<1-2 sentences on why this is effective>
```

#### For an Image

When the user sends an image:

1. **Read the image** — extract and understand what's in it
2. Create a markdown file with the extracted content
3. If it contains a tool/product/announcement, use the appropriate template above
4. If it's a screenshot of a tweet, use the tweet template
5. If it's something else, format it clearly with context

#### For a Quick Tip / Insight

```markdown
---
date: YYYY-MM-DD
tags: [relevant, tags]
---

# Title

> The tip in one line

<Expanded explanation if needed — keep it short and actionable>
```

### 4. Update the README

After creating the content file, update the README's "Latest Drops" section:

- Add the new entry between `<!-- LATEST_START -->` and `<!-- LATEST_END -->` markers
- Format: `| <emoji> | [**Title**](./<category>/filename.md) | <one-line description> | <date> |`
- Keep only the **latest 10 entries** in the README — remove older ones to keep it clean
- If it's the very first entry, replace the "*Nothing here yet*" placeholder with a table:

```markdown
| | Drop | What | Date |
|---|---|---|---|
| :emoji: | [**Title**](./path/to/file.md) | One-line description | YYYY-MM-DD |
```

Emoji guide for the table:
- :rocket: for launches
- :wrench: for tools
- :brain: for prompts
- :bulb: for tips
- :gem: for resources
- :book: for reads

### 5. Commit and Push

- **Commit message format**: `drop: <brief description>`
- **Always push** after committing so the repo stays up to date

## Formatting Principles

- **Scannable**: Someone should get the value in 30 seconds of skimming
- **No fluff**: Every sentence earns its place
- **Hooks matter**: The one-line description under the title is what makes someone keep reading
- **Links are sacred**: Always include the source link prominently
- **Tags are useful**: Add 2-4 relevant tags for future searchability
- **Keep the user's voice**: If they share with commentary, preserve their perspective

## What NOT to do

- Don't pad short content — if it's a quick tip, keep it quick
- Don't over-categorize — pick the single best category
- Don't editorialize — present what it is, not what you think about it
- Don't capture casual conversation — only capture when the user shares specific content
- Don't forget to push — the repo is the product, it needs to be live

## Getting Current Time

Use: `TZ='Asia/Kolkata' date '+%H:%M'`
