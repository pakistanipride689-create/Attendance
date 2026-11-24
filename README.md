# EnrollSync - Code repo (Email No.1 / Attendance)

This repo hosts the **real code**: `enroll_sync.py`. The exe built from
the Email No.2 repo has no business logic in it - it just downloads this
file over HTTPS every time it starts (and every few hours while running)
and runs it in memory.

## The switch

- **Disable every install everywhere**: delete `enroll_sync.py` (or make
  this repo private). Any exe that notices - next launch, or next
  periodic check - refuses to run.
- **Push an update to everyone**: edit `enroll_sync.py` here and commit -
  every site picks up the change on its next check/launch, no need to
  touch or rebuild the exe.
- A PC with no internet for a short while is not instantly locked out -
  it runs on the last successfully downloaded copy for a few days (set in
  the Email No.2 loader), so a bad connection doesn't stop production.

`licenses.json` in this repo is no longer used - you can delete it or
leave it, it has no effect either way.

Keep this repo **public**, otherwise the raw link below won't work
without adding a GitHub token to the loader:

```
https://raw.githubusercontent.com/pakistanipride689-create/Attendance/main/enroll_sync.py
```
