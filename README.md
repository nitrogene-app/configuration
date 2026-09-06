# Announcements

A dismissible banner across the top of the app, driven by a JSON file in a
separate repo. Publishing an announcement needs no deploy and no admin UI.

## Where the config lives

https://github.com/nitrogene-app/configuration → `announcements.json` on `main`

Fetched by the app from:
`https://raw.githubusercontent.com/nitrogene-app/configuration/main/announcements.json`

## File format

A bare array. The first entry with `"active": true` wins; everything else is
ignored, so retired entries stay in the file as a changelog and `git log`
becomes the announcement history.

```json
[
  {
    "id": "2026-09-scheduled-maintenance",
    "active": true,
    "severity": "warning",
    "message": "Scheduled maintenance Sunday 14 Sep, 2–4am AEST. See [status](https://status.nitrogene.com.au) for updates."
  }
]

## Severity Options

| Value | Colour | Use for |
|-------|--------|---------|
| `info` | blue | Neutral news, new features |
| `success` | green | Resolved incidents, completed migrations |
| `warning` | amber | Upcoming maintenance, deprecations |
| `error` | red | Active outages, urgent action needed |

