# PawPal GitHub Team Workflow

**Repo:** https://github.com/vincentlee001804/PawPal
**Maintainer:** Vincent (reviews and merges all Pull Requests)
**Last updated:** 20 November 2026

This guide covers the full workflow for the PawPal team: how to set up, how each member pushes their part, and how merging works. Read it once, keep it bookmarked.

---

## 1. Maintainer setup (Vincent — do this once)

1. **Add teammates as collaborators**
   - Repo page → **Settings** → **Collaborators** → **Add people**
   - Enter each member's GitHub username → **Add to this repository**
   - Each member must **accept the invite** (they get an email or see a notification bell on GitHub). They cannot push until accepted.
2. **Protect the `main` branch** (recommended)
   - **Settings** → **Branches** → **Add branch ruleset** (or "Add classic protection rule")
   - Branch name pattern: `main`
   - Tick **Require a pull request before merging** (leave approvals at 0 — you merge everything yourself)
   - This stops anyone (including you, accidentally) from pushing straight to `main`.
3. **Make the repo public before submission** — the assignment requires a public repository. Plan when as a team; everything in the repo becomes visible once public.

---

## 2. First-time setup (each member — do this once)

1. Install Git: https://git-scm.com/download/win (accept the defaults).
2. Open a terminal (Git Bash or PowerShell) and introduce yourself to Git:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your-github-email@example.com"
   ```

   Use the **same email as your GitHub account** so your commits link to you.
3. Clone the repo (this downloads a full working copy):

   ```bash
   git clone https://github.com/vincentlee001804/PawPal.git
   cd PawPal
   ```

4. Windows tip: when Git asks for credentials, sign in through the GitHub popup that appears — it saves your login so you never type it again.

---

## 3. The daily loop (each member)

Do this every time you sit down to work. It keeps your copy of `main` fresh and your changes isolated.

### Step 1 — Get the latest code

```bash
git checkout main
git pull
```

### Step 2 — Create your own branch for the work you're about to do

Name it after yourself and the feature, e.g.:

```bash
git checkout -b feature/alice-pet-profiles
```

A branch is your private parallel copy. Changing it does not affect `main` or anyone else.

### Step 3 — Work and save progress

Edit files normally in VS Code / Android Studio. Whenever you finish a small piece of work:

```bash
git status                          # see what changed
git add .                           # stage all changes (or: git add lib/pets/)
git commit -m "Add pet profile form UI (FR-PET-01)"
```

Commit message rules:

- One short sentence, present tense: what this commit does.
- Reference the requirement ID when relevant: `(FR-EXP-03)`, `(FR-SCH-12)` — our AGENTS.md conventions.
- Commit **little and often** (every 30–60 minutes of working code), not one giant commit at midnight.

### Step 4 — Push your branch to GitHub

```bash
git push -u origin feature/alice-pet-profiles
```

(The first push of a new branch needs `-u origin <branch-name>`; after that, just `git push`.)

### Step 5 — Open a Pull Request (PR)

1. On the repo page, GitHub will show a yellow banner: *"branch had recent pushes"* → click **Compare & pull request**. (Or: **Pull requests** tab → **New pull request** → set base = `main`, compare = your branch.)
2. Fill in the title and a short description of what you built and what to check.
3. Click **Create pull request**.
4. Post the PR link in the group chat and wait for Vincent to review and merge.

**Never merge your own PR.** Vincent handles all merges so `main` always stays in a working state.

---

## 4. Maintainer guide (Vincent — reviewing and merging)

1. Open **Pull requests** tab on the repo.
2. For each PR: read the description → **Files changed** tab to review the diff → check it builds/doesn't break others.
3. If something needs fixing: leave a comment on the offending line (click the `+` beside the line) and ask the member to update. They push more commits to the same branch and the PR updates automatically — no new PR needed.
4. When it looks good: **Merge pull request** → use **Squash and merge** (squashes all their commits into one clean commit on `main`) → **Delete branch** (GitHub offers this button — click it; the branch has served its purpose).
5. After merging, tell the team: "main updated, everyone `git pull`."

### If GitHub says "This branch has conflicts"

It means another PR touched the same lines of the same file first. Ask the **member** (not you) to resolve it on their laptop:

```bash
git checkout feature/alice-pet-profiles
git merge main          # pulls the new main into their branch
# Git will list conflicted files; open each one and look for <<<<<<< markers
# keep the correct lines, delete the markers, save
git add .
git commit -m "Resolve merge conflicts with main"
git push
```

The PR updates automatically and becomes mergeable again. For Flutter projects the most common conflict zone is `pubspec.yaml` (dependency list) — if two members add packages, combine **both** entries in the file rather than picking one side.

---

## 5. Team rules (everyone)

1. **Never push directly to `main`.** Always branch → PR.
2. **Never commit secrets.** No `.env` files, no Supabase service-role key, no API keys — ever. The service-role key stays out of both clients per our SRS (NFR-SEC-03). If you accidentally commit one, tell Vincent immediately so it can be revoked and removed.
3. **Own your area.** To minimise conflicts, each member works mainly in their own folders:
   - e.g. `lib/features/pets/` → Alice, `lib/features/scheduler/` → Bob, `lib/features/explore/` → Carol, admin panel `admin/` → David. Shared files (`pubspec.yaml`, `main.dart`, router) → small careful changes, PR early.
4. **Pull before you start, push when you finish a piece.** Small frequent merges beat giant weekly ones.
5. **Commit messages** follow Step 3 conventions; include the FR/NFR ID where it applies.
6. **Don't commit build junk.** The `.gitignore` already excludes common Flutter/Android artifacts. If your IDE suggests committing `build/`, `.dart_tool/`, or `.idea/`, say no.
7. Each member keeps their branch alive **only for days, not weeks** — open the PR as soon as the feature works, even if small.

---

## 6. Cheatsheet (print me)

```bash
# Start of work session
git checkout main && git pull
git checkout -b feature/<yourname>-<feature>

# During work (little and often)
git add .
git commit -m "what you did (FR-XXX-NN)"

# Share your work
git push -u origin feature/<yourname>-<feature>
# → open Pull Request on GitHub → wait for Vincent to merge

# After your PR is merged / before next session
git checkout main && git pull
git branch -d feature/<yourname>-<feature>   # clean up locally
```

---

## 7. FAQ

**Q: I forgot to pull and now my push is rejected ("non-fast-forward").**
A: Run `git pull`, let it merge, fix any conflicts, then `git push` again. Rejected push = the remote has newer code you don't have yet; Git is protecting you from overwriting it.

**Q: I committed to `main` by accident and can't push.**
A: Good — the branch protection blocked you. Move the commit to a branch: `git checkout -b feature/my-fix`, then reset main: `git checkout main && git reset --hard origin/main`.

**Q: Can I work on two features at once?**
A: Yes — one branch per feature, switch with `git checkout <branch-name>`. Finish and PR one before starting the next if you can; it keeps life simple.

**Q: Where do I see what the team is doing?**
A: Repo **Insights** → **Network** (commit graph), the **Issues** tab (use it for the task list), and the **Pull requests** tab for anything waiting to merge.
