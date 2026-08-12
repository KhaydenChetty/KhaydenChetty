# Redesign — Remaining Work

The profile README rewrite (Phases 1, 4, 5, 6) is done. What's left is the part that can't be
written for you: the actual evidence of what you build.

Ordered by impact.

---

## P0 — The credibility gap

### 1. Publish Kotlin work

Your profile says Kotlin is your primary language. **You have no public Kotlin repository.**
Every public repo is C#, Java, JavaScript or HTML.

This is the single biggest weakness in the profile. A recruiter who reads "Kotlin" and then
scrolls your repo list sees a contradiction. Either:

- push a Kotlin/Android project (even a small one), **or**
- change the "Primary" row in the stack table to reflect what you can actually show.

Rule 6 from your plan: *demonstrated skills > claimed skills.*

### 2. Fill in the two unfinished project cards

`README.md` has `<!-- TODO -->` comments marking these:

- **`02` Azure Functions** — replace the generic description with what the service actually does:
  the trigger type, what it processes, why serverless suited it.
- **`03` SnapClappedApp** — this repo has no description on GitHub at all. Write one line on what
  it does, then update both the repo description and the card.

### 3. Add screenshots

Create `assets/projects/` and add at least one image per featured project. Then uncomment the
`<img>` block in each card.

| Project type | What to show |
| --- | --- |
| dynacon-finance | the mobile UI — 2–3 screens side by side |
| Azure Functions | architecture sketch, or a request/response pair |
| SnapClappedApp | the interface |

This is the highest-impact visual change left. Badges say you can build; screenshots prove it.

### 4. Write real READMEs for the three featured repos

Use this structure in each:

```text
# Project Name
One-line explanation.

## What it does
## Why I built it
## Features
## Technology
## Screenshots
## What I learned
## Future improvements
## Running it
```

---

## P1 — Repository hygiene

### 5. Add descriptions and topics

Several repos have no description. `SnapClappedApp` and `ST10448657-PROG5121-POE` especially.
Add a one-line description and 3–5 topics to each repo you're keeping public.

### 6. Rename academic repos

`ST10448657-PROG5121-POE` reads as a student number, not software. Consider a name describing
what it *is* — the academic detail belongs in the README, not the URL.

> Renaming is safe: GitHub redirects the old URL. Update the link in `README.md` afterwards.

### 7. Archive or clean up

- `KAPKiRiGi` — described as "Config files for my GitHub profile" but contains Java. Either fix
  the description or archive it.
- `PRACTTEST` — archive.
- The two forks (`TutorConnect`, `weather-api-multiendpoint`) — forks show on your profile with a
  fork badge. Fine to leave, but they don't add portfolio value.

### 8. Pin the right repos

Profile → Customize your pins. Pin the three featured projects **in the same order** as the
README so the page and the pin grid agree.

---

## P2 — Cleanup from the redesign

- [ ] Delete the `METRICS_TOKEN` repo secret (nothing uses it)
- [ ] Revoke the classic PAT at github.com/settings/tokens
- [ ] Delete the `output` branch (old snake artifacts, now unreferenced)
- [ ] Update the "Last reviewed" date in the `currently --building` block when you next edit it

---

## Definition of done

Check the profile **logged out**, in a private window, on a phone:

- [ ] A recruiter understands what you do in 10 seconds
- [ ] A developer sees evidence you can actually build things
- [ ] Every featured project has a screenshot
- [ ] The stack table matches what's demonstrably in your repos
- [ ] Coursework is visually separated from portfolio work
- [ ] No broken images
