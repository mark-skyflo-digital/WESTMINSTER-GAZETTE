# Agent Branch + Worktree Strategy (Westminster Gazette)

This guide defines how multiple Codex agents can work independently without merge collisions.

## 1. Branch Naming Standard
Use:
- `codex/<bead-id>-<short-topic>`

Examples:
- `codex/westminstergazette-4ox-2-pss-inventory`
- `codex/westminstergazette-p36-1-uprn-model`

## 2. One Story Per Branch
- Exactly one Beads story per branch.
- Do not mix stories in one PR.
- Keep commits scoped to story acceptance criteria.

## 3. Parallel Work with Git Worktrees
Create a sibling folder per story:

```bash
cd /Users/markscott/Desktop/WestminsterGazette

# Story A
git worktree add ../WG-4ox-2 -b codex/wg-4ox-2-pss-inventory main

# Story B
git worktree add ../WG-p36-1 -b codex/wg-p36-1-uprn-model main

# Story C
git worktree add ../WG-2no-1 -b codex/wg-2no-1-fullcrud-permset main
```

Remove worktree after merge:

```bash
git worktree remove ../WG-4ox-2
```

## 4. Pre-Work Sync (Mandatory)
In each worktree before coding:

```bash
git fetch origin
git rebase origin/main
```

## 5. Change Scope Rules
Allowed:
- Files required by the story only.

Not allowed:
- Unrelated metadata edits
- Formatting-only mass changes
- Refactors outside acceptance criteria

## 6. Story Execution Sequence
For each story:
1. Move Bead to in progress.
2. Implement metadata/code.
3. Validate deploy (`sf project deploy start --dry-run ...`).
4. Commit with Bead ID in message.
5. Push branch and open PR.
6. Link PR in Bead notes.
7. Merge after checks pass.

## 7. Merge Order for Salesforce Metadata
To reduce dependency failures:
1. Object model and fields
2. Permission sets/profiles
3. Tabs/apps/layouts/flexipages
4. Flows/triggers/classes
5. Reports/dashboards

## 8. Commit Message Template
Use:
- `<bead-id>: <action>`

Examples:
- `WestminsterGazette-4ox.3: add agent branch/worktree strategy guide`
- `WestminsterGazette-2no.1: add Westminster_MVP_FullCRUD permission set`

## 9. PR Checklist
- [ ] Story acceptance criteria met
- [ ] Dry-run deploy result included
- [ ] No unrelated files changed
- [ ] Rollback note included
- [ ] Bead updated with implementation notes

## 10. Hotfix Rule
Urgent fixes use:
- `codex/hotfix-<short-topic>`

After hotfix merge:
- Rebase all active branches on updated `main` before continuing.
