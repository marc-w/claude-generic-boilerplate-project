# Code and Software Addendum

This file contains rules for writing code. This file is standalone and may be added to a project.  

If this file is in the project but not referenced in `cladude.md` or `master.md`, then ignore the contents of this file.

Use Python unless otherwise specified.  

There is no concern for backward compatibility unless declared explicitly.

All Python code should be PEP 8 compliant, including line lengths.  We most commonly use Black and PyLint for linting. 

## Coding Standards

- Name a collected-issues structure `errors`, not `report`/`results`. This is either a list or a key-value pair for any errors or problems encountered in the operation. It is either returned from the calling function, or it will be available as an attribute of the object created.
- Don't manually wrap a line just to fit under ~80 chars — reduce the
  underlying complexity if you can (e.g. bind a repeated `len()`/computed
  value with `:=` once and reuse it); only reach for `# noqa: E501` when the
  line is genuinely irreducible.
- Never issue any git command other than `git status` and `git diff`. Any and all other commands require human approval first. That means you need to ask and receive confirmation for any operations outside of `git status` and `git diff'.
- The Python version will be declared in the project, and the project has no backward-compatibility
  requirement. 
- Docstrings must describe inputs and outputs, not just what the function
  does — an `Args:` / `Returns:` section (or equivalent inline) for any
  function with non-trivial parameters or a return value. A bare one-line
  docstring is only fine for a function that takes nothing and returns
  nothing meaningful.

## Code & Standards

### Review comments (`##`)

- Humans flag a requested change or fix with an inline comment prefixed `##`,
  directly at or near the relevant line in code.
- Claude: find `##` comments, apply the fix, then call out what changed and
  wait for approval. Do not remove the `##` comment yet.
- Once approved, remove the `##` comment — not before.
- Works in any file that supports `#`-style comments (`.py`, `.yml`, shell
  scripts). Not usable in `.json` (no comment syntax) — flag those separately
  in chat instead.

### Credentials & settings (`local.sh` / `local.sh.example`)

- All credentials and settings are env vars — no config files, no hidden
  defaults, no other helper mechanism, and never, ever, for any reason, use or consider using env or .env files. `local.sh` is the contract: source it
  to set every env var the app needs, the same way locally and on an
  instance.  Secret handling beyond local will be treated accordingly and is often an external app or a process not necessarily described here.
- Each project ships `local.sh.example` — a full copy of `local.sh` with
  every credential replaced by a placeholder, committed to the repo. A new
  dev copies it to `local.sh` (gitignored) and fills in real values.
- Keep `local.sh.example` in lockstep with `local.sh`: same shell functions,
  same exported vars, same everything except real values. If `local.sh`
  changes, update `local.sh.example` in the same pass.
- Never commit `local.sh` itself, and never print or repeat its real
  values.
