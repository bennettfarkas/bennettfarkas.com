# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with analytics for bennettfarkas.com.

## Status

Cloudflare Web Analytics is live. Snippet added to `../index.html` before `</body>`.

## Setup

- **Provider**: Cloudflare Web Analytics (free, privacy-friendly, no cookies)
- **Dashboard**: Cloudflare Dashboard > Web Analytics > bennettfarkas.com
- **Snippet location**: `../index.html`, just before `</body>`
- **Metrics**: Page views, referrers, device/browser, geography (all automatic)

## Notes

- No cookie banner needed — Cloudflare Web Analytics doesn't use cookies
- Conversion tracking (e.g. mailing list signup) is not built into Cloudflare Web Analytics; would need a separate approach if needed later
