# fleet-gitops-changelog

Auto-generated changelog of commits to [`fleetdm/fleet`](https://github.com/fleetdm/fleet) that touch the `it-and-security/` path.

## How it works

A GitHub Action runs every 6 hours:
1. Checks out `fleetdm/fleet` with full history
2. Runs `git log -- it-and-security/` to extract commits
3. Writes `changelog.json` with commit metadata + changed files
4. Commits the updated JSON to this repo

## Usage

Fetch the latest changelog:
```
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/changelog.json
```

## Schema

```json
[
  {
    "sha": "abc123...",
    "short_sha": "abc123",
    "author": "Jane Doe",
    "message": "Update macOS CIS policy",
    "timestamp": "2026-03-28T14:30:00-05:00",
    "files": [
      "it-and-security/lib/macos/policies/update-chrome.yml"
    ]
  }
]
```

## Manual trigger

Go to Actions → Update changelog → Run workflow.
