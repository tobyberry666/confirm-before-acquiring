---
name: confirm-before-acquiring
description: Use when about to download, install, fetch, or create any tool/utility/helper/config file — requires pausing to ask the user for explicit confirmation before proceeding; no silent additions to the project
---

# Confirm Before Acquiring

## Overview

**Core principle:** Nothing enters the project without the user knowing.

You are a guest in someone else's codebase. Downloading a package, fetching a remote file, or creating a utility script are all acts of adding complexity to their world. Always pause. Always ask.

**Violating the letter of this rule is violating the spirit of this rule.**

## The Iron Law

```
NO DOWNLOAD, NO INSTALL, NO NEW TOOL FILE — WITHOUT EXPLICIT USER CONFIRMATION FIRST
```

If you haven't asked and received a "yes" in this conversation turn, you cannot proceed.

## Scope

**This rule covers:**

- Package installs: `npm install`, `pip install`, `cargo add`, `apt install`, `brew install`, any package manager
- Remote fetches: `curl`, `wget`, `fetch()`, downloading assets/fonts/images/binaries
- Creating tool/utility files: scripts, helpers, generators, configs, wrappers, shims — any file whose purpose is "infrastructure" rather than "the actual deliverable"
- Adding dependencies to manifest files (package.json, requirements.txt, go.mod, etc.)

**This rule does NOT cover:**

- Creating the actual deliverable the user asked for (the report, the component, the page)
- Reading files, running read-only commands (`ls`, `cat`, `git log`)
- Editing existing files the user already told you to modify
- Temporary scratch files inside your own workspace that the user will never see

**Grey area?** Ask. That's what this skill is for.

## The Gate Function

```
BEFORE acquiring or creating:

1. STOP — Do not run the command or write the file yet.
2. STATE — Tell the user exactly what you intend to do:
   - What: [package name / file name / URL]
   - Why: [one sentence — what problem it solves]
   - Impact: [what changes in their project — new dep? new file? where?]
   - Alternative: [is there a way to avoid it?]
3. WAIT — Do not proceed until the user says yes.
4. ONLY THEN — Execute.
```

## Confirmation Template

Use this exact shape when asking:

```
I'd like to [download / install / create]:
  What: <name or path>
  Why: <one sentence>
  Impact: <what gets added/changed>
  Alternative: <how to avoid it, or "none — this is necessary">

OK to proceed?
```

Keep it short. One block. Don't bury the ask in a paragraph.

## Red Flags — STOP and Ask

- You're about to type `npm install` / `pip install` / `curl` / `wget`
- You're creating a file the user didn't explicitly name
- You think "this helper script would make things cleaner"
- You're adding a "small" config file "just to make it work"
- You're fetching a font/asset/library "because the design needs it"
- You're about to modify package.json / requirements.txt / any manifest
- You think "they'll thank me later"
- You're doing it "temporarily" but it'll persist on disk

**Any of these → STOP. Use the template. Ask.**

## Rationalization Prevention

| Excuse | Reality |
|--------|---------|
| "It's just a tiny utility script" | Tiny files accumulate. Ask. |
| "They obviously need this package" | Obvious to you ≠ obvious to them. Ask. |
| "I'll mention it after" | After ≠ before. The whole point is BEFORE. |
| "It's standard practice" | Their project, their rules. Ask. |
| "Asking every time is annoying" | Silent surprises are more annoying. Ask. |
| "I'll just create it and they can delete it" | You don't get to decide that. Ask. |
| "It's only a dev dependency" | Still their project. Still ask. |
| "The task can't be done without it" | Then say so in the Why field. They'll appreciate the honesty. Ask. |
| "I already asked about something similar" | Each acquisition is its own ask. Don't batch-assume. |

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Asking mid-execution (command already running) | Ask BEFORE typing the command |
| Burying the ask inside a long explanation | Template first, explanation after if needed |
| Asking "is it OK if I install X and also create Y and fetch Z?" | One ask per acquisition. Batch only if tightly coupled. |
| Proceeding because user said "sure, do whatever" earlier | Stale permission ≠ current permission for new items |
| Creating the file "as a draft" before asking | Creating IS the action. Ask first. |

## When In Doubt

Ask. The worst outcome of asking is a 5-second delay. The worst outcome of not asking is the user discovering unwanted files, broken dependencies, or bloated node_modules they never agreed to.
