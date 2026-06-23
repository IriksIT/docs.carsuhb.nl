# CarsHub API Docs

This directory contains the OpenAPI 3.1.0 specification for the **CarsHub Crew Website Sync API** — a read-only API that lets crew owners sync their crew data (members, cars, events, stats, and page config) to an external website.

## Interactive documentation

Visit **[docs.carshub.nl](https://docs.carshub.nl)** for the full interactive API reference, including live request examples and response schemas.

## About the API

- **Auth** — every request requires a crew API key from the Website Sync module in the crew dashboard
- **HTTPS only** — plain HTTP requests are rejected with `403`
- **Read-only** — all endpoints are `GET`; no data is written through this API

## Endpoints

| Method | Path | Description |
|--------|------|-------------|
| `GET` | `/api/crews/{crew}/members` | Crew member roster (includes `social_links`) |
| `GET` | `/api/crews/{crew}/cars` | Cars owned by crew members (includes `social_links` with owner fallback) |
| `GET` | `/api/crews/{crew}/events/upcoming` | Upcoming crew events |
| `GET` | `/api/crews/{crew}/events/past` | Past crew events |
| `GET` | `/api/crews/{crew}/events/{event}` | Single event detail (includes `attendees_by_day` with `is_passenger` for multi-day events) |
| `GET` | `/api/crews/{crew}/stats` | Crew overview statistics |
| `GET` | `/api/crews/{crew}/pages` | All website page configs |
| `GET` | `/api/crews/{crew}/pages/{pageKey}` | Single page config |

## Notable fields

### `social_links` (members and cars)
Every member and car entry includes a `social_links` object with keys `instagram`, `facebook`, `x`, `snapchat`, and `website`. All values are `null` when not set.

For **cars**, the field uses the car's own social link if set, falling back to the owner's social link for that platform.

### `attendees_by_day` (event detail)
Multi-day events include an `attendees_by_day` map keyed by date (`YYYY-MM-DD`). Each entry is a list of attendees present that day, extended with:
- `is_passenger` — `true` when attending as a passenger (no car brought)
- `car` — the car object for that day, or `null` when attending as passenger or no car selected

Single-day events return `null` for `attendees_by_day`.

## Files

- `api.json` — OpenAPI 3.1.0 spec (source of truth for docs.carshub.nl)
