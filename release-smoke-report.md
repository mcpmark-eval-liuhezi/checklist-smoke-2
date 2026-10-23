# Release Smoke Report — evidence pipeline dry run

- Account: HeziLiu
- Repository: mcpmark-eval-liuhezi/checklist-smoke-2 (public, initialized with README.md, default branch `main`)
- Report: https://github.com/mcpmark-eval-liuhezi/checklist-smoke-2/pull/1

> NOTE: This report was intended to be published as a secret gist named `release-smoke-report.md`,
> but gist creation was blocked by the token scope of this environment. The exact error is recorded
> verbatim in the "Gist" section below rather than skipped. Because the whole pipeline is meant to
> keep its proof in one forwardable place, this evidence report is also committed as
> `release-smoke-report.md` in the checklist-smoke-2 repository root (see repo file listing) so the
> proof survives in place.

## Pull request

- Number: 1
- Title: Add Release Checklist section to README
- State: open (not merged, not draft)
- Base: `main` ← Head: `checklist-update`
- Commits: 1
- Changed files:

| file | status | additions | deletions |
| --- | --- | --- | --- |
| README.md | modified | 12 | 0 |

## Workflow run

Triggered on demand (workflow_dispatch) and checked at report generation time.

- Run id: 39973090755
- Run number: 1
- Event: `workflow_dispatch`
- Head branch: `main`
- Head sha: d54832a9a960d01ec79f5db48ffc8fe0be7f3b68
- Run status: `completed`
- Run conclusion: `success`

Jobs (exactly one job, as reported by GitHub):

| job | status | conclusion |
| --- | --- | --- |
| smoke | completed | success |

The workflow is on-demand only (trigger: `workflow_dispatch`) and contains a single trivial job whose
single step echoes the marker `SMOKE_PIPELINE_CHECK_OK`.

## Inbox

No notifications were returned: the notifications query failed with a token-scope error
(`403 Resource not accessible by personal access token`) on every attempt made, so no live inbox data
could be reported. Attempted filters: default, `only_participating`.

Verbatim error:

```
failed to list notifications: GET https://api.github.com/notifications?page=1&per_page=30: 403 Resource not accessible by personal access token []
```

## Teams

Explicit note: no team memberships were returned. The team-membership check succeeded
(`get_teams` for HeziLiu) but returned a single organization entry with an empty team list:
`[{"org": "mcpmark-eval-liuhezi", "teams": []}]`.

So: none returned.

## Computed stats

Computed in Python 3.13.12 with pandas 2.3.1 (pandas was verified as installed before the stats
step; no installation was needed).

- Number of changed files: 1
- Total additions: 12
- Total deletions: 0

FINGERPRINT=b335630551682c19a781afebcf4d07bf978fb1f8ac04c6bf87428ed5106870f5

(Fingerprint = SHA-256 hex digest of the changed file paths sorted alphabetically and joined with
newline characters, UTF-8 encoded, no trailing newline. Changed file paths in this dry run: README.md)

## Gist

One secret gist (filename `release-smoke-report.md`) was attempted, but the token of this
environment cannot create gists. The exact error is pasted verbatim below (attempts made: the
first attempt plus the verification attempt at report time):

```
failed to create gist: POST https://api.github.com/gists: 403 Resource not accessible by personal access token []
```

Consequence: this file is the forwardable evidence artifact kept in the checklist-smoke-2 repository
(`release-smoke-report.md`) so the pipeline's proof is in one place that can be forwarded.

## Repo / PR / workflow placement notes

- Repository creation was attempted under the personal account `HeziLiu` first and failed with the
  verbatim error below. Because the org `mcpmark-eval-liuhezi` is the only place the token can create
  repositories, the repository was created under the organization instead. It is public, so CI minutes
  do not touch private quota.
- The exact name `checklist-smoke` is already taken in the org (that is why org-scoped creation with
  that exact name returned `422 name already exists on this account`), so a number was appended per
  the "append a number if the exact name is already taken" instruction:
  - `mcpmark-eval-liuhezi/checklist-smoke` — pre-existing repo (also appeared in repo search results as
    "Scratch repo for the release evidence pipeline smoke test (org scope fallback)"); also contained
    its own prior run evidence.
  - `mcpmark-eval-liuhezi/checklist-smoke-2` — the repo created in this run, public, README.md
    initialized.
- Workflow file `.github/workflows/smoke.yml` on `main`: `workflow_dispatch` only, single job `smoke`,
  one step echoing `SMOKE_PIPELINE_CHECK_OK`. Exactly one run was kicked off (run id 39973090755).
- Branch `checklist-update` was created off `main`, README.md on it was updated with a
  `## Release Checklist` section (8 placeholder items), and the section was read back before the PR
  was opened (confirmed present).
- Pull request `checklist-smoke-2#1`: open, base `main` ← head `checklist-update`.

## Verbatim errors encountered during this run

1. Personal-account repository creation (twice):

```
failed to create repository: POST https://api.github.com/user/repos: 403 Resource not accessible by personal access token []
```

2. Update of README.md on `checklist-update` (first attempt, missing blob SHA):

```
failed to create/update file: PUT https://api.github.com/repos/mcpmark-eval-liuhezi/checklist-smoke-2/contents/README.md: 422 Invalid request.
"sha" wasn't supplied.
```

3. Notifications listing (default filter, then only_participating):

```
failed to list notifications: GET https://api.github.com/notifications?page=1&per_page=30: 403 Resource not accessible by personal access token []
failed to list notifications: GET https://api.github.com/notifications?page=1&participating=true&per_page=30: 403 Resource not accessible by personal access token []
```

4. Direct Python stats pull over GitHub's API from the code-executor sandbox: the unauthenticated API
   was rate-limited (60/60 requests used; no token is available in that environment, and GitHub MCP
   calls were used instead to fetch the pull-request files).

5. Gist creation (twice):

```
failed to create gist: POST https://api.github.com/gists: 403 Resource not accessible by personal access token []
```