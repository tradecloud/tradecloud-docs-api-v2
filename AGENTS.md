# tradecloud-docs-api-v2

## Purpose

External-facing API v2 documentation for the TC1 platform. Covers
order, shipment, forecast, connectors, security, support, plus
guides and a checklist.

## Module / Stack

Markdown (likely GitBook-rendered -- see `SUMMARY.md`).

## Build

No build. Authoring is direct in `.md` files. Render via the
hosting tool (GitBook or equivalent).

## Entry Points

- `SUMMARY.md` -- navigation tree
- `api/`, `connectors/`, `forecast/`, `order/`, `shipment/`,
  `security/`, `guide/` -- topic dirs
- `checklist.md`, `support.md` -- standalone refs

## Notes

- Public-facing -- review changes for clarity and accuracy.
- Align with `tradecloud-sdk-dotnet` and the API surface in
  `tradecloud-microservices`.
