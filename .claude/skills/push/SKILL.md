---
name: push
description: Commit the current game changes and push them to GitHub so the live GitHub Pages site (https://ofiryehonatan.github.io/snake-game/) updates. Use whenever the user says "push" in this repo.
---

This repo (`ofiryehonatan/snake-game`) is a static site served by GitHub
Pages from the `main` branch root. There is no build step — a push to
`main` is the entire deploy. Follow these steps whenever this skill runs:

1. Run `git status` to see what changed.
2. **Only stage the real project files** (e.g. `index.html`, `snake.html`,
   `icy-tower.html`, `manifest.json`, `server.js`, files under `.claude/`).
   Do **not** stage or touch:
   - `Snake Game/` — a separate nested git repo with its own history,
     unrelated in-progress work.
   - `snake-game/` — a stray full clone of this same repo that ended up
     nested inside the working directory. Leave it alone.
   If new untracked files show up that aren't obviously one of the above,
   ask before adding them rather than guessing.
3. Write a commit message that describes *why*, not a file-by-file list —
   summarize the user-facing effect of the change (e.g. "Add tilt controls
   to Icy Tower" not "Modify icy-tower.html"). End it with:
   ```
   Co-Authored-By: Claude Sonnet 5 <noreply@anthropic.com>
   ```
4. `git push origin main`.
5. Tell the user it's pushed and that GitHub Pages typically takes
   30-60 seconds to rebuild, then they can hard-refresh
   https://ofiryehonatan.github.io/snake-game/ to see it live.

If there's nothing staged/changed, say so instead of creating an empty
commit. If a merge/rebase is needed because `origin/main` has diverged,
stop and check with the user before doing anything that rewrites or
force-pushes history — this repo has hit unrelated-history merges before
(a stray auto-created README on the GitHub side), so don't assume a
conflict means something is wrong; just resolve it plainly and confirm
with the user only if it's destructive.
