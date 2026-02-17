# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with analytics for bennettfarkas.com.

## Status

Cloudflare Web Analytics is live. Snippet added to `../index.html` before `</body>`.

## Setup

- **Provider**: Cloudflare Web Analytics (free, privacy-friendly, no cookies)
- **Dashboard**: Cloudflare Dashboard > Web Analytics > bennettfarkas.com
- **Snippet location**: `../index.html`, just before `</body>`
- **Metrics**: Page views, referrers, device/browser, geography (all automatic)

## API Access

Credentials stored in `analytics/.env` (gitignored):
- `CF_API_TOKEN` — Cloudflare API token with Account Analytics: Read
- `CF_ACCOUNT_ID` — Cloudflare account ID

Query analytics via GraphQL:
```bash
curl -s "https://api.cloudflare.com/client/v4/graphql" \
  -H "Authorization: Bearer $CF_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"query": "{ viewer { accounts(filter: {accountTag: \"$CF_ACCOUNT_ID\"}) { rumPageloadEventsAdaptiveGroups(filter: {datetime_geq: \"...\", datetime_leq: \"...\"}, limit: 10, orderBy: [date_DESC]) { count dimensions { date } } } } }"}'
```

Max query range is ~93 days. Use `rumPageloadEventsAdaptiveGroups` for page views.

## Notes

- No cookie banner needed — Cloudflare Web Analytics doesn't use cookies
- Conversion tracking (e.g. mailing list signup) is not built into Cloudflare Web Analytics; would need a separate approach if needed later
