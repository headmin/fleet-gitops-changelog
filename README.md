# fleet-gitops-changelog

Auto-generated changelog of commits to [`fleetdm/fleet`](https://github.com/fleetdm/fleet) that touch the `it-and-security/` path, plus a timeline of Fleet-maintained app version updates from [fmalibrary.com](https://fmalibrary.com).

## How it works

A GitHub Action runs every 6 hours:
1. Checks out `fleetdm/fleet` with full history
2. Runs `git log -- it-and-security/` to extract commits
3. Writes `changelog.json` (raw commits), `changelog.jsonl` (enriched timeline), and `gitops-structure.json` (current tree snapshot)
4. Fetches `https://fmalibrary.com/feed.xml` and writes `fma-timeline.json` + `fma-timeline.jsonl` (FMA app updates)
5. Commits any changed JSON to this repo

## Usage

Fetch the latest artifacts:
```
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/changelog.json
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/changelog.jsonl
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/gitops-structure.json
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/fma-timeline.json
https://raw.githubusercontent.com/headmin/fleet-gitops-changelog/main/fma-timeline.jsonl
```

## Schema

`changelog.json` — raw git history:
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

`fma-timeline.json` — Fleet-maintained app version updates, sourced from <https://fmalibrary.com/feed.xml>. The matching `fma-timeline.jsonl` contains the same `items` one-record-per-line (no wrapper), for streaming consumers.
```json
{
  "generated": "2026-05-14T15:00:00Z",
  "source": "https://fmalibrary.com/feed.xml",
  "source_title": "Fleet-maintained apps",
  "count": 100,
  "items": [
    {
      "id": "brave-browser/windows-148.1.90.121-148.1.90.122",
      "title": "Brave 148.1.90.121 → 148.1.90.122 (Windows)",
      "app": "Brave",
      "platform": "windows",
      "version_from": "148.1.90.121",
      "version_to": "148.1.90.122",
      "timestamp": "2026-05-14T03:13:37+00:00",
      "download_url": "https://github.com/brave/brave-browser/releases/download/v1.90.122/BraveBrowserStandaloneSilentSetup.exe"
    }
  ]
}
```

## Manual trigger

Go to Actions → Update changelog → Run workflow.
