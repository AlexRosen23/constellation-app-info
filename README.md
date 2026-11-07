# constellation-app-info

The public homepage and privacy policy for Constellation's Google sign-in, which Google requires before an OAuth app can be published.

**Status:** Live (static pages on GitHub Pages) · **Stack:** HTML, CSS · Built with [Claude Code](https://claude.com/claude-code)

## What it does

Constellation is Alex's personal 3D command center for his own projects. It runs only on his own Mac. To connect his Google account it needs a public page that describes the app and a public privacy policy; this repository is those two pages.

- **Homepage:** https://alexrosen23.github.io/constellation-app-info/
- **Privacy policy:** https://alexrosen23.github.io/constellation-app-info/privacy.html

## What the pages say

- The homepage explains what the app is, what it can do with a connected Google account, and where it runs.
- The privacy policy lists each Google permission the app requests and why, how data is handled, and how to remove access.
- The policy states that mail and calendar content is read live and not stored, is not shared or sold, and that email is never sent, drafted, deleted or changed.

## How it works

```
index.html     homepage
privacy.html   privacy policy
style.css      shared styles
```

The pages are plain HTML and CSS with no build step and no scripts. GitHub Pages serves them from `main`.

## Built with

Static HTML and CSS, written with Claude Code as an AI pair programmer under Alex's direction and review.

## Run it locally

Open `index.html` in a browser.

## Maintenance

Update `privacy.html` before Constellation uses any new Google data. The scopes it lists must always match the Google integration in the private Constellation project.

## Project stats

| | |
|---|---|
| Timeline | 2026-10-21 → 2026-10-21 (first to last commit) |
| Commits | 1 |
| Active Claude Code time | 0.2 hours across 5 sessions (2026-11-02 → 2026-11-07) |
| Claude tokens (new work) | 130 thousand: 72 input, 105 thousand written to cache, 24 thousand output |
| Claude tokens (cache reads) | 7.8 million, counted separately (see below) |
| Models (share of responses) | Claude Opus 5.5 91%, Claude Sonnet 5.5 9% |

<details>
<summary>How these numbers were measured</summary>

Measured from Claude Code session transcripts (the `.jsonl` files Claude Code writes for every session and subagent) with a small read-only script. Each Claude response's `usage` record is counted once. A response counts toward this repo when its working directory is inside the repo (or a git worktree of it); for sessions started from a general folder, when its tool calls point into the repo, or else the project that session was last working on.

- **New-work tokens** = input tokens + tokens written to the prompt cache + output tokens.
- **Cache reads** are the conversation context that Claude re-reads from Anthropic's prompt cache on every turn. They are far larger than new work and are billed at about a tenth of the input price, so they are listed separately rather than added to the total.
- **Active time** joins transcript events that are at most 15 minutes apart into working intervals, then merges overlapping intervals so parallel sessions and subagents are not double counted. Idle gaps longer than 15 minutes are not counted.

All figures are approximate.

</details>

## Part of The Constellation

These pages belong to [The Constellation](https://github.com/AlexRosen23/constellation), Alex's 3D command center for every project.
