# EnrollSync - Code + License repo (Email No.1)

This repo hosts the **real code**. The exe built from the Email No.2 repo
has no business logic in it at all - it's just a small loader that, every
time it starts (and every few hours while running), downloads `enroll_sync.py`
from here over HTTPS and runs it in memory.

## Files

- **`enroll_sync.py`** - the actual, full EnrollSync program (unchanged from
  what you gave me). This is the file whose presence/absence controls
  whether installs can run at all.
- **`licenses.json`** - per-site switch list. Even if `enroll_sync.py` is
  present, a site not listed here still won't run.

## The kill-switch, in plain terms

- **Disable one site**: remove its Site ID from `licenses.json`'s `active`
  list, commit.
- **Disable every install everywhere at once**: delete `enroll_sync.py`
  (or the whole repo / make it private). Any exe that notices (next
  launch, or next periodic re-check) refuses to run.
- **Push an update to everyone**: just edit `enroll_sync.py` here and
  commit - every site picks up the new version on its next check/launch,
  no need to rebuild or redistribute the exe.
- A site with no internet for a short while is **not** instantly locked
  out - it runs on the last successfully downloaded copy for a grace
  period (set in the Email No.2 loader), so a bad connection doesn't stop
  production.

## What I need from you next

Push this repo to GitHub (keep it **public**, otherwise the raw links
below won't work without adding a token to the loader), then send me the
two raw URLs, e.g.:

```
https://raw.githubusercontent.com/<EMAIL1_USERNAME>/<EMAIL1_REPO>/main/enroll_sync.py
https://raw.githubusercontent.com/<EMAIL1_USERNAME>/<EMAIL1_REPO>/main/licenses.json
```

I'll drop those into the Email No.2 loader so the exe knows where to fetch
from, and build that repo next.

## Adding a new site

The exe asks for a Site ID on first run at a new location and shows it on
screen. Add that exact ID to `active` in `licenses.json` here to activate
that install.
