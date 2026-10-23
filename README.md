# checklist-smoke-2

Evidence smoke test repo for the release checklist pipeline

## Release Checklist

- [ ] Verifies repository exists under the account (public, README.md initialized)
- [ ] Confirms on-demand GitHub Actions workflow exists and was triggered once
- [ ] Adds the "## Release Checklist" section to README.md on `checklist-update`
- [ ] Confirms the branch's README contains the checklist section before opening the PR
- [ ] Opens pull request from `checklist-update` into `main` and verifies it is open
- [ ] Runs the stats step in Python with pandas (changed files, additions, deletions)
- [ ] Computes the SHA-256 file-path fingerprint and prints FINGERPRINT=<digest>
- [ ] Publishes the evidence report as a secret gist