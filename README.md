# github_repo_health_check

A Conductor workflow that fetches GitHub repo health metrics in parallel — stars, forks, open issues, latest release, top contributors, and recent commits.

Uses only HTTP system tasks against the public GitHub API. No API key, no workers, no setup required.

## Workflow

- [`workflows/github_repo_health_check.json`](workflows/github_repo_health_check.json)

## Input

| Parameter | Type   | Default                    | Description              |
|-----------|--------|----------------------------|--------------------------|
| `repo`    | string | `vercel/next.js`           | Any public GitHub repo in `owner/name` format |

## Output

```json
{
  "summary": {
    "repo": "vercel/next.js",
    "stars": 125000,
    "forks": 26000,
    "open_issues": 2800,
    "language": "JavaScript",
    "description": "The React Framework",
    "latest_release": "v15.1.0",
    "top_contributors": ["timneutkens", "ijjk", "..."],
    "recent_commits": [
      { "message": "...", "author": "...", "date": "..." }
    ]
  }
}
```

## Deploy to Orkes Developer Edition

```bash
conductor workflow upsert --file workflows/github_repo_health_check.json
conductor workflow start --name github_repo_health_check --input '{"repo": "vercel/next.js"}'
```
