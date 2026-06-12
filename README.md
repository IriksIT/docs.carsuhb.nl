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
| `GET` | `/api/crews/{crew}/members` | Crew member roster |
| `GET` | `/api/crews/{crew}/cars` | Cars owned by crew members |
| `GET` | `/api/crews/{crew}/events/upcoming` | Upcoming crew events |
| `GET` | `/api/crews/{crew}/events/past` | Past crew events |
| `GET` | `/api/crews/{crew}/events/{event}` | Single event detail |
| `GET` | `/api/crews/{crew}/stats` | Crew overview statistics |
| `GET` | `/api/crews/{crew}/pages` | All website page configs |
| `GET` | `/api/crews/{crew}/pages/{pageKey}` | Single page config |

## Files

- `api.json` — OpenAPI 3.1.0 spec (source of truth for docs.carshub.nl)
