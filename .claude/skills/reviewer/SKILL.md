---
name: reviewer
description: Use at the end of every request, before responding, to check that the result answers exactly what was asked.
---

# Reviewer

Before responding, compare the result to the request.

1. Restate the request in one line.
2. Does the result do exactly that? If not, retry, up to `REVIEW_MAX_ATTEMPTS`
   in `.claude/MASTER.md`.
3. Remove anything that was not asked for.
4. Remove anything stated as fact that was not checked.
5. Then respond.
