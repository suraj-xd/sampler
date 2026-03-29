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
├── reads/             # Articles, threads, videos worth consuming
├── ideas/             # Startup ideas, project ideas, things worth building
├── mindblown/         # Mind-blowing discoveries, paradigm shifts
├── brainfuck/         # Wild, WTF moments that break your brain
└── previews/          # Screenshot previews of linked content
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
| `ideas/` | Startup idea, project idea, side project concept, "someone should build this" |
| `mindblown/` | Mind-blowing discovery, paradigm shift, "I can't believe this exists" |
| `brainfuck/` | Wild demo, WTF moment, something that breaks your brain |

### 2. Create the file

- **Filename**: `<category>/YYYY-MM-DD_slug.md` (e.g., `tools/2026-03-29_cursor-agent-mode.md`)
- **Slug**: short, descriptive, lowercase, hyphenated
- **Date**: current date in YYYY-MM-DD format

### 3. Capture a preview image

For any content with a URL, capture a visual preview so readers can see what it looks like without clicking:

**Priority order:**

1. **YouTube videos**: Use the thumbnail URL directly — `https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg`. No screenshot needed, just reference this URL in the markdown.
2. **og:image**: When fetching a URL with WebFetch, check for `og:image` or `twitter:image` meta tags. If found, use that URL directly in the markdown.
3. **Playwright screenshot** (fallback): If no og:image is available, use Playwright to navigate to the URL and take a screenshot:
   - Navigate: `mcp__playwright__browser_navigate` to the URL
   - Screenshot: `mcp__playwright__browser_take_screenshot` with type `jpeg` and filename `previews/<slug>.jpeg`
   - The slug should match the content file's slug (e.g., `openai-prism`)

**Saving previews:**
- Save screenshots to `previews/<slug>.jpeg`
- Use JPEG format to keep file sizes small
- Reference in markdown as: `![Preview](../previews/<slug>.jpeg)`

**In the content file**, place the preview image right after the title and hook line, before the link:

```markdown
# Title

> One-line hook

![Preview](../previews/<slug>.jpeg)

**Link**: [Title](URL)
```

**Skip previews for:**
- Quick tips or ideas with no URL
- Content where a visual preview adds no value (e.g., a plain text prompt)

### 4. Format based on content type

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

#### For a Startup / Project Idea

```markdown
---
date: YYYY-MM-DD
tags: [relevant, tags]
---

# Idea Title

> One-line pitch

## The idea

<What is it? 2-4 sentences describing the concept clearly.>

## Why it could work

<What makes this viable or interesting right now?>

## How to start

<Simplest first step someone could take to validate or prototype this>
```

#### For Mind Blown / Brainfuck

```markdown
---
date: YYYY-MM-DD
source: <URL if applicable>
tags: [relevant, tags]
---

# Title

> One-line hook that makes someone stop scrolling

## What happened

<Describe the thing — demo, discovery, capability, whatever blew your mind>

## Why this is wild

<Context on why this matters or what it implies for the future>
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

### 5. Update the README

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
- :dart: for ideas
- :exploding_head: for mindblown
- :zap: for brainfuck

### 6. Commit and Push

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
