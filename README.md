# Enterprise Feature Store: Discovery UI

A product concept and clickable prototype for a **web interface that lets data scientists find, trust and reuse ML features without writing code**.

> **New here?** Start with the [prototype](prototype/index.html) (2 minutes), then skim the [PRD](docs/Enterprise-Feature-Store-PRD.pdf) (25 pages).

## The idea in plain words

- A **feature** is a ready-made data signal used to train an ML model, for example *"average spend of a customer over the last 30 days"*.
- A **feature store** keeps these features in one governed place so teams reuse them instead of rebuilding them.
- **The problem:** today the Enterprise Feature Store is only a Python library. A data scientist (the *Model Builder*) must know exact feature names, ask data engineers what exists, and wait 2 to 3 days to get a training dataset.
- **The solution:** a self-service web UI to browse, search, inspect and assemble features into a versioned training dataset, then hand it off to model training, in minutes rather than days.

**Target outcomes (from the PRD):** training dataset in under 30 minutes (from 2 to 3 days), feature reuse up from under 20% to 40%, 50% fewer "what features exist?" support tickets.

## What's in this repo

| Path | What it is |
|---|---|
| [`docs/Enterprise-Feature-Store-PRD.pdf`](docs/Enterprise-Feature-Store-PRD.pdf) | Product Requirements Document v1.0: problem, goals, personas, requirements, metrics, risks, launch plan. |
| [`prototype/index.html`](prototype/index.html) | Clickable prototype of the full user journey. One file, no install: open it in a browser. |

## The PRD at a glance

| Section | Summary |
|---|---|
| Who it's for | **Model Builder** (data scientist / ML engineer) who consumes features. Feature Engineers and Platform Admins are supporting personas, out of scope. |
| Five core surfaces | Repository Home, Domain Browser, Feature Search, Feature Detail Panel, Dataset Builder. |
| AI assistant | **Atlas**: ask in natural language, get ranked feature recommendations with reasons. Works on feature metadata only, never row-level data. |
| Priorities | P0 for alpha (navigation, search, feature detail, dataset builder, export, access control), P1 for GA (saved datasets and versions, usage analytics, Atlas, semantic search, freshness indicators), P2 after GA. |
| Out of scope | Creating features, platform admin, SDK changes, online serving, connectors to other ML platforms. |

## The prototype: what you can try

The prototype follows one persona, a fraud data scientist, through the whole journey using sample data (a *Fraud Analytics* repository).

1. **Home:** recent work and your repositories.
2. **Repository and domains:** Customer, Transactions, Merchant, Accounts, with feature counts.
3. **Search:** type-ahead and results showing data type, freshness and "used by N models".
4. **Domain browser:** features grouped by entity, with filters (freshness, type, tags, owner, popularity, PII policy), plus datasets other teams built.
5. **Dataset builder:** add features to a cart, auto-detected join key, point-in-time data preview.
6. **Versioning:** a saved version stores the *recipe* (features, versions, join key), not a copy of the data; rebuild or compare any version.
7. **Feature detail:** definition, SQL formula, lineage, refresh history, statistics, consuming models.
8. **Atlas:** ask "Which customer features detect card-testing fraud?" and add the ranked results in one click.
9. **Hand-off:** export to a notebook or continue to training.

All names, numbers and data are illustrative.

```bash
open prototype/index.html                  # option 1: open the file
python3 -m http.server 8000                # option 2: serve, then visit /prototype/
```

## Building the real app with Lovable

This repo is meant to be linked to [Lovable](https://lovable.dev). It has no app scaffold yet, so Lovable can generate the project in the repo root. Suggested first prompt:

> Build a React + TypeScript app that reproduces the clickable prototype in `prototype/index.html`, following the requirements in `docs/Enterprise-Feature-Store-PRD.pdf`. Use mock data first. Screens: Home, Repository, Domain, Dataset builder, Version summary, Feature detail, Atlas panel.

Repo settings in place for this:
- `.gitignore` covers Node, Vite, env files and editor files.
- `.gitattributes` marks `docs/` and `prototype/` as documentation, so GitHub language stats reflect the app code once it exists.
- `.editorconfig` keeps formatting consistent.
- Keep `docs/` and `prototype/` as reference material; let Lovable own `src/`, `package.json` and other root app files.

## Status

Concept and prototype stage. No backend, authentication or real data yet.

**Author:** Sachin Doddamani, Senior Product Manager · PRD v1.0, October 2026 (in review)
