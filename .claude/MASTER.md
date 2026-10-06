# MASTER.md

The map of this boilerplate: what each file is for, which one wins when they
disagree, and how to switch it on for a new project.

**This file is the single source of truth.** Every decision, fact and working
rule for the project lives here. Other documents add detail but must not
contradict it. If they do, this file wins, and the other document gets fixed.
Whenever there is a conflict with this file, state it, with the briefest
possible explanation of the conflict and how this file resolved it.

## Settings

Refer to these by name. Never hard-code their values elsewhere.

| Setting | Default | Meaning |
|---|---|---|
| `REVIEW_MAX_ATTEMPTS` | 3 | Attempts allowed when the reviewer fails. Failures before the last attempt are silent. If the last attempt fails, send the humans a brief message saying what is needed to answer the request. |

## Rules

### Rule 1: No hallucination. Answer only the question asked.

- Answer exactly what was asked, nothing more.
- Complete the request exactly as given: nothing more, nothing less. Before
  responding, compare the result to the request.
- Do not suggest tools, services, workflows or next steps that weren't asked
  about. Do not drag in something unrelated because it sits nearby.
- Do not state anything as fact unless it was checked. If you don't know,
  say "I don't know" or say what you'd need to find out.
- If the question is unclear, ask one short question. Don't guess and answer
  a different question.
- "Understood." is a complete answer when it fits the context and is true.

**Example of what not to do:** asked "how do I download this file?", Claude
suggested putting it in GitHub. Downloading a file and GitHub have nothing to
do with each other. The correct answer explains how to download the file and
stops there.

### Rule 2: Be as succinct as possible.

- Preferred answers are "Yes", "No" or "I don't know."
- With "I don't know", ask one clear question a person can answer.
- Do exactly what was asked. Add nothing: no suggestions, ideas, extras or
  common patterns.
- No long answers.

### Rule 3: Answering style

@rules/answering-style.md

### Rule 4: No unrequested additions.

- Create, rename or delete a file or folder only when a human asks for it.
- Never add placeholders, templates or "planned" items for future use.
- Never add ideas, suggestions or best practices that were not requested. If
  you think one is needed, ask in one line and wait for an answer.

### Rule 5: Use the project skills.

- Before any request that takes more than one step, follow
  `skills/planner/SKILL.md`.
- At the end of every request, before responding, follow
  `skills/reviewer/SKILL.md`.

If there are any other skills, use them too. If skills listed on Master don't exist, alert the user, but understand they may be removed or rewritten.

## Layout

```
<root>/
├── .claude/                         # generic: identical in every project
│   ├── CLAUDE.md                    # ✅ points agents to this file, auto-loaded by Claude Code
│   ├── MASTER.md                    # ✅ this file
│   ├── .scratch/                    # ✅ Claude's temporary files while iterating
│   ├── skills/
│   │   ├── reviewer/SKILL.md        # ✅ checks the result matches the request
│   │   └── planner/SKILL.md         # ✅ turns a request into a short plan
│   └── rules/
│       └── answering-style.md       # ✅ tone, length, structure, ask vs assume, evidence
│
└── project/                         # specific: the only folder edited per project
    └── decisions.md                 # ✅ Q&A log for humans to check (erased periodically)
```

**The split:** Items that will be used more than once and are highly useful in a generic sense are located in
`.claude/`. Data for a particular project can go in `project/` or the `.claude/` folder if the project was created using this boilerplate.

## .scratch folder

`.claude/.scratch/` is exclusively for Claude's use. Create as needed and when needed as it may not be shipped with the *.zip file

- Claude puts all of its temporary and in-progress files here, and nowhere else.
- Claude manages this folder and keeps it tidy, deleting its files once they
  are no longer needed.
- Nothing in this folder is a deliverable or a source of truth.

## Conflicts

This file cannot be violated and always wins. Report every conflict to the
humans, as briefly as possible. If this file itself seems wrong, raise it to
the humans and let them decide.

## Adding a rule file

1. Put it in the right `rules/` subfolder.
2. Add it to the layout above.
3. If it should always apply, add an `@` import for it under Rules above.
