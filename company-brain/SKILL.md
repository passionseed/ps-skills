---
name: company-brain
description: Use when a task needs facts about PassionSeed as a company: what we do, team, SHIFT and other programs, offers and prices, counts and numbers, marketing, business model, history, glossary terms, or past decisions. Also use when someone asks to record a company fact or decision. Reads the private passionseed/company-brain repo, the single source of truth for company facts.
---

# Company Brain

## Overview

`passionseed/company-brain` is a private GitHub repo of short Markdown pages that hold everything important about PassionSeed. This skill holds no company facts itself. It tells you how to read the brain and how to propose changes to it.

**Core principle:** answer from the brain, cite the page, and never fill gaps from memory, the web, or other repos.

## 1. Get the latest copy

Always read the latest `main`, never a stale copy.

```bash
BRAIN=~/company-brain
if [ -d "$BRAIN/.git" ]; then
  # Use the local clone only if it is clean and on main; otherwise use a fresh temp copy
  git -C "$BRAIN" diff --quiet && [ "$(git -C "$BRAIN" branch --show-current)" = main ] \
    && git -C "$BRAIN" -c credential.helper='!gh auth git-credential' pull -q --ff-only \
    || BRAIN=""
fi
if [ -z "$BRAIN" ] || [ ! -d "$BRAIN/.git" ]; then
  BRAIN=$(mktemp -d)/company-brain
  gh repo clone passionseed/company-brain "$BRAIN" -- -q --depth 1
fi
echo "$BRAIN"
```

To read a single page without cloning:

```bash
gh api repos/passionseed/company-brain/contents/numbers.md -H "Accept: application/vnd.github.raw"
```

If `gh` returns 404 or "Could not resolve", the user lacks access. Tell them to ask a passionseed org admin for access to `company-brain`. Don't guess the answer instead.

## 2. Find the answer

1. Read `README.md` first. Its table lists every page and what it covers.
2. Read `AGENTS.md`. Its rules apply to everything you write from the brain.
3. Open the page(s) the table points to. Use `grep -ri` across `*.md` for anything not obvious.

| Need | Page |
|---|---|
| Any count or total (students, team size, prices as numbers) | `numbers.md`, the only place numbers live, each with a source and "as of" date |
| A past decision and why | `decisions/log.md`, newest first |
| A Thai or internal term | `glossary.md` |

## 3. Answer correctly

- **Cite the page** (e.g. "per `offer.md`, updated 2026-10-11"). Include the "as of" date for numbers.
- **Unknowns stay unknown.** `(fill in)` means nobody has written it yet; `Unknown as of YYYY-MM-DD` means someone was asked and didn't know. Say so; don't fill the gap.
- **Conflicts: don't pick a side.** If the brain disagrees with another source (code, another repo's AGENTS.md, a doc, the user), show both and ask the user which is right.
- **Brain over memory.** If you remember something different from what the brain says, the brain wins; mention the difference.

## 4. Propose a change

Only when a person tells you a new fact or decision, or confirms one:

1. Follow every rule in the brain's `AGENTS.md`: page header and `updated` date, numbers only in `numbers.md`, decisions appended to `decisions/log.md`, new pages added to the README table, and no sensitive data (student personal data, logins, payment details).
2. Work in a clone on a new branch, never `main`. Open a pull request with a short summary of what changed and why.
3. Never merge it yourself unless a person has reviewed it and explicitly told you to merge.

Never edit the brain to match code or another repo without a person confirming the fact first.
