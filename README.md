# Band Hub Workflow (step-by-setp)

### FEEL FREE TO EDIT THIS GUIDE AS YOU SEE FIT !!!!

Workflow for using:
- GitHub (Band-Hub-MERN org)
- VS Code + Copilot/Codex chat
- Obsidian vault repo (planning/docs)
- BandHub code repo (implementation)

## Repos used
1. `Band-Hub-MERN/BandHub` (app code)
2. `Band-Hub-MERN/BandHub-Vault` (Obsidian planning/docs)
3. Later we will use `Band-Hub-MERN/BandHub-Testing` (unit testing)

---

## 1) First-time local setup
1. Create a local folder for both repos (example: `Band_Hub_Workspace`).
2. Clone both repos into that folder.
3. Open VS Code.
4. Open the workspace folder (or add both repo folders to one VS Code workspace).
5. Sign in to GitHub in VS Code.
6. Confirm both repos are visible in Source Control.

---

## 2) Start work on a task (always use a branch)
1. In `BandHub` repo, pull latest `main`.
2. Create a new branch from `main`.
3. Branch naming example: `feature/task-2-invite-ui`.
4. Keep one branch focused on one task only.

Best practice:
- Never code directly on `main`.

---

## 3) Plan first in the vault (before coding)
1. Open `BandHub-Valut` notes.
2. Add/update task notes in:
   - `product/Task Backlog.md`
   - `engineering design/Task 2 Build Sheet (Final).md`
   - `Other Notes/Questions to Resolve.md`
3. Record scope, acceptance criteria, and done criteria.
4. Ask Copilot/Codex to clarify open questions before coding.

Best practice:
- If requirement changes, update vault notes RIGHT AWAY.

---

## 4) Build with Copilot/Codex in small chunks
1. Tell Copilot exactly which task/subtask you are implementing.
2. Implement in small slices (backend first, then frontend, then tests).
3. Reuse components/utilities to keep code modular.
4. Keep commits small and meaningful.

Best practice:
- Do not mix unrelated features in one commit.

---

## 5) Test before pushing
Minimum checks before push:
1. Backend runs without errors.
2. Frontend build succeeds.
3. Feature flow works manually end-to-end.
4. No new lint/compile errors.

If tests exist:
- Run unit/integration/E2E tests for changed areas.

Best practice:
- If local build fails, do not push yet.

---

## 6) Commit and push (code repo)
1. Stage only relevant files.
2. Write clear commit message (include task ID/name).
3. Push branch to `origin` (Band-Hub-MERN/BandHub).

Commit style example:
- `Task 2.3: add org invite accept API`

---

## 7) Commit and push (vault repo)
If planning/docs changed:
1. Switch to `BandHub-Valut` repo.
2. Commit updated markdown notes.
3. Push to the matching branch name (or a docs branch).

Best practice:
- Keep code changes and vault updates in sync.

---

## 8) Open Pull Request (PR)
Where:
- GitHub org repo page -> `BandHub` -> Pull requests -> New pull request.

How:
1. Base branch: `main`
2. Compare branch: your feature branch
3. Fill PR template clearly:
   - what changed
   - why
   - how tested
   - screenshots (if UI changed)
4. Request review from teammates.

Best practices:
- Keep PR small enough to review quickly.
- Link related vault note(s) in PR description.
- Do not merge your own PR without review (team rule).

---

## 9) Merge and clean up branch
After approval and green checks:
1. Merge PR to `main` (usually Squash or Merge Commit by team choice).
2. Delete remote feature branch from GitHub.
3. On local machine:
   - switch to `main`
   - pull latest `main`
   - delete local feature branch

---

## 10) Deployment + auto server reboot
Current setup:
- Push/merge to `main` triggers GitHub Actions deploy.
- Workflow deploys frontend + backend, then restarts PM2 and reloads Nginx.

After merge:
1. Open Actions tab in `BandHub`.
2. Confirm deploy workflow is green.
3. Test live site quickly (login + core feature path).
4. If deploy fails, read logs and fix in a new branch.

Best practice:
- Never ignore failed deploy logs.

---

## 11) Daily team rhythm (recommended)
1. Pick task from backlog.
2. Clarify in vault.
3. Branch.
4. Build + test.
5. Push + PR.
6. Merge when approved.
7. Verify production.
8. Update vault "Built Today / Decisions / Next Step".

---

## Team rules summary
- `main` stays stable and deployable.
- Branch for every task.
- Test before push.
- Keep docs in `BandHub-Valut` updated.
- Use modular, reusable code.
- Review PRs before merge.
