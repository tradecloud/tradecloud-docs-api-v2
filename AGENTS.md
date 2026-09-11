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

## Pull requests

- The description follows `.github/PULL_REQUEST_TEMPLATE.md`: Intent (why,
  and what is different afterwards), AI assistance (what the tool did, what
  the human did), optional Verification (only what CI cannot tell), then the
  repository's own checklists. Keep it proportional to the change; do not
  list files, the diff shows where.
- The first line is the Jira ticket. Ask for it when it is not known and
  never invent or assume a number.
- Open the pull request as a draft, let the AI reviewers run, disposition
  every finding (fix it, resolve it with a reason, or record it under
  Rejected Findings), then mark it ready for review. The full flow:
  <https://github.com/tradecloud/tradecloud-docs-devops/blob/master/development/cd-process/reviewing/ai-assisted-contributions.md>

## Rejected Findings

None yet.
