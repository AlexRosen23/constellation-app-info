# constellation-app-info: features

Two static web pages: a public homepage and a privacy policy for the Google sign-in of The Constellation, a personal
app that runs only on its owner's Mac. Google needs a public homepage and a public privacy-policy address before it
will publish an OAuth consent screen, so they live here. The one thing this repo does best is say exactly which Google
data the app uses and how it is handled.

**This is the source-of-truth features list.** Every PR that adds, changes, removes or switches off something a person
can see or use updates this file in the same PR (see "Keeping this file true").

- **Repo:** AlexRosen23/constellation-app-info (public) · **Folder:** none locally; clone the repo
- **Status:** live on GitHub Pages · **Version:** none · **`main`:** `a62f573` (2026-11-15)
- **Last updated:** 2026-11-15, written from the pages, README and PR history in this repo.

**Status words** (a feature with no status word is live):
| Word | Means |
| --- | --- |
| *Live* | on `main` and served by GitHub Pages |
| *Planned* | named in the README as a gap, not built |

## At a glance
| | |
| --- | --- |
| Stack | plain HTML and CSS; no build step, no scripts, no trackers, no external assets |
| Pages | 2 (`index.html`, `privacy.html`) plus 1 stylesheet (`style.css`) |
| Size | 134 lines across the three files (counted 2026-11-15) |
| Hosting | GitHub Pages, legacy build from `main`, folder `/`, HTTPS enforced |
| Tests | none (the pages contain no code) |
| PRs merged | 3 (all README work) |

## Contents
1. What it is and who it's for
2. How to run it
3. Architecture at a glance
4. Features
5. Integrations
6. Data and privacy
7. Tests and evidence
8. Known limits and gaps
9. Change log

## 1. What it is and who it's for
- Readers: Google's consent-screen review, and anyone who wants to know what the app does with a connected Google
  account.
- The app itself is not offered to anyone else and has no account to create (stated on the homepage).

## 2. How to run it
- Open `index.html` in a browser. Nothing to install or build.
- To preview over HTTP: `python3 -m http.server 8000 --bind 127.0.0.1`, then open `http://127.0.0.1:8000/`.
- Live addresses: `https://alexrosen23.github.io/constellation-app-info/` and `.../privacy.html`.
- No environment variables.

## 3. Architecture at a glance
| Path | What it is |
| --- | --- |
| `index.html` | the homepage |
| `privacy.html` | the privacy policy |
| `style.css` | shared styles, light and dark |
| `.nojekyll` | tells GitHub Pages to serve the files as they are |
| `.githooks/`, `.gitleaks.toml` | secret scan before every commit and push; direct pushes to `main` are refused |
| `README.md`, `FEATURES.md` | documentation (see "Known limits and gaps" about how Pages serves them) |

## 4. Features
### Homepage
- **What the app is** *(live)*: a private dashboard for one person's projects and day, run only on the owner's Mac. `index.html`
- **What it can do with Google** *(live)*: read-only view of Gmail (unread and important counts, search, a conversation as plain text); show Google Calendar events; add, change or delete an event on a calendar the owner owns, only after a preview and a confirmation. States that it never sends, drafts, deletes or changes email. `index.html`
- **Where it runs** *(live)*: on the owner's Mac, on its own loopback address only; sign-in uses the owner's own Google Cloud project and a "Desktop app" OAuth client; credentials are kept in the macOS Keychain. `index.html`
- **Contact** *(live)*: open an issue in this repo. `index.html`

### Privacy policy (effective October 21, 2026)
- **Scope table** *(live)*: lists every permission and why: `openid` and `email`, `gmail.readonly`, `calendar.events`, `calendar.calendarlist.readonly`. `privacy.html`
- **Handling rules** *(live)*: data read live and not stored; one temporary audio file for a spoken calendar answer, deleted once played; tokens only in the Keychain; Google data stays on the Mac; not shared, sold, used for ads or used to train models; email never passed to the app's AI assistants. `privacy.html`
- **Google API Services User Data Policy statement** *(live)*, including Limited Use. `privacy.html`
- **Removing access** *(live)*: a `google:disconnect` command, or the owner's Google Account third-party apps page. `privacy.html`
- **Change promise** *(live)*: the policy is updated before the app uses any other Google data; history is the public commit log of `privacy.html`.

### Site behaviour
- **Light and dark themes** *(live)*: follows the reader's `prefers-color-scheme`. `style.css`
- **Phone-friendly layout** *(live)*: single column, viewport meta tag set. `style.css`, `index.html`
- **No tracking** *(live)*: no JavaScript, analytics, fonts or images from other servers.

## 5. Integrations
- Google OAuth consent screen: these pages are its homepage and privacy-policy addresses.
- GitHub Pages: serves the site from `main`.
- The app these pages describe lives in a private repository and is not described further here.

## 6. Data and privacy
- The site collects nothing from readers.
- The repo holds no secrets; gitleaks runs in the commit and push hooks.
- What the app does with Google data is the policy text itself (`privacy.html`).

## 7. Tests and evidence
- No test suites. Counted from source on 2026-11-15, not run.
- Recorded checks (README, 2026-11-10): both URLs returned HTTP 200 and the Pages build succeeded; the scopes listed
  in the policy were compared by hand with the app's scope list.

## 8. Known limits and gaps
- *Planned*: no automatic check that the scopes on the policy page match the app's code (README).
- The Google connection the pages describe was recorded as "built, not connected" in the README on 2026-11-10.
- No license file.
- Pages serves the repo root, so any root file, including this one and the README, is reachable at a public address
  on the same site.

## 9. Change log
| Date | PR | Change |
| --- | --- | --- |
| 2026-11-10 | #3 | README verification lines refreshed |
| 2026-11-10 | #2 | full README write-up |
| 2026-11-07 | #1 | README rewritten with overview, stack and run steps |
| 2026-10-21 | initial commit | homepage, privacy policy and stylesheet |

## Keeping this file true
- **Same PR, same change.** A change to a page, the policy or the hosting updates this file in the same PR.
- **Status moves with reality.**
- **Only what is true.** Describe only what this repo publishes.
- **Repo gate.** Changes go through a PR; the pre-push hook refuses direct pushes to `main`.
