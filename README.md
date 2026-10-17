# Nexus Feature Store

A product concept for an **enterprise feature store**: one governed place where data scientists discover, understand, reuse and assemble ML features into training datasets, with an AI assistant (Atlas) to help along the way.

This repo holds the product spec and a clickable prototype. It is the starting point for building a working app (linked to [Lovable](https://lovable.dev)).

## What's in here

| Path | What it is |
|---|---|
| [`prototype/index.html`](prototype/index.html) | Self-contained, clickable portfolio prototype. No build step or dependencies: open it in a browser. |
| [`docs/Enterprise-Feature-Store-PRD.html`](docs/Enterprise-Feature-Store-PRD.html) | Product Requirements Document (HTML export). |

## The prototype: what's built

The prototype walks one persona (a fraud data scientist) through the full journey, using realistic sample data (Fraud Analytics repository):

1. **Home**: recent work, repositories (12 governed workspaces, e.g. Fraud Analytics, Marketing Analytics) and a three-step "how to get started".
2. **Repository → Domains**: each repository is split into domains (Customer, Transactions, Merchant, Accounts) with feature counts, plus search scoped to the repository.
3. **Search**: type-ahead suggestions and a full results page showing type, entity, freshness, and "used by N models".
4. **Domain browser**: features grouped by entity (e.g. `customer_id`), with filters for freshness, data type, tags, owner, popularity, PII policy and time travel, and datasets other teams have already built.
5. **Dataset builder**: a "cart" of features with pinned versions, an auto-detected join key, point-in-time data preview (with null handling and sampling) and regular vs. time-series datasets.
6. **Versioning**: saving stores a *definition* (features, versions, join key, filters), not a data copy; rows are rebuilt on demand. Includes version history, recipes, rebuild and compare.
7. **Feature detail**: business definition, SQL formula, producing process, refresh history, statistics, distribution, lineage (source → transformation → feature), usage, consuming models and datasets.
8. **Atlas (AI assistant)**: natural-language feature discovery with ranked matches ("96% match"), explanations and one-click add to dataset.
9. **Hand-off**: export to notebook or continue to training.

Navigation also shows the wider platform surfaces (Notebooks, Vector store, ModelOps, MCP server, Integrations) as context.

> All names, numbers and data in the prototype are illustrative sample data.

## Run the prototype

```bash
# Option 1: just open the file
open prototype/index.html

# Option 2: serve it locally
python3 -m http.server 8000   # then visit http://localhost:8000/prototype/
```

## Using this repo with Lovable

The repo is intentionally minimal (no app scaffold yet) so Lovable can generate the project in the root. Suggested first prompt:

> Build a React + TypeScript app that reproduces the clickable prototype in `prototype/index.html`, following the requirements in `docs/Enterprise-Feature-Store-PRD.html`. Use mock data first; keep screens: Home, Repository, Domain, Dataset builder, Version summary, Feature detail, Atlas panel.

Repo settings for the link:
- `.gitattributes` marks `docs/` and `prototype/` as documentation so GitHub language stats reflect the real app code once Lovable adds it.
- `.gitignore` covers Node/Vite/env/editor files that Lovable-generated code produces.
- `.editorconfig` keeps formatting consistent between Lovable edits and local edits.
- Keep `docs/` and `prototype/` as reference material; let Lovable own `src/`, `package.json` and the other root app files.

## Status

Concept and prototype stage. No backend, authentication or real data yet.
