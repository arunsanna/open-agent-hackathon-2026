# Track 01 — Solving Fragmented Intelligence: Build Brief

Goal: an agent that discovers and works across fragmented data sources and proves it on a meaningful real-world problem.

## What we know (from metadata)

- Judged on real-world usefulness for clearly defined users, plus meaningful sponsor-tech use (Zetaris/Meterless integration counts — Wildcard explicitly requires it; tracks reward it).
- Impact is 30/100 with a consistency-against-challenge definition. Full rubric: confirm from Official Rules before finalizing the entry.
- Submission bar is documented: strong/weak examples, demo video guide, technical execution requirements — all in `../hackathon-metadata/resources/`.

## Proposed shape (to confirm with Arun)

Agent that takes one messy real-world question, discovers relevant sources across the Zetaris open-data catalogue (REST APIs, Parquet/CSV, semantic layers) plus live web sources, connects findings, and returns an evidence-backed answer with per-claim source links.

Why this shape: it hits the track ("discover and work across fragmented data") and borrows the evidence-review muscle (claim-level source handoff) this team already has.

## Data available day one (local)

- `../hackathon-metadata/external/zetaris-rest-api-sources.md` — e.g. PokéAPI, Open Food Facts, NASA NeoWs, data.gov.sg (verified/restricted status per source)
- `../hackathon-metadata/external/zetaris-parquet-csv-sources.md`
- `../hackathon-metadata/external/zetaris-usl-sources.md`
- Zetaris connection guides for Codex/Cursor/Claude Code + Lightning SQL reference/companion — `../hackathon-metadata/resources/zetaris-*.md`

## First steps

1. Confirm team (1–5) and register before Oct 22, 23:59 UTC.
2. Connect one Zetaris data source (PokéAPI first-dataset guide) and verify SQL connectivity.
3. Prototype the discover → query → cite loop on one question; keep every claim pinned to its source.
4. Record demo early; iterate against the strong-submission example.

## Gates (do not skip)

- Official Rules + Disqualification Checklist + AI Usage Policy read before writing code for submission.
- No submission, team join, or public post from this repo without Arun's explicit approval of the exact entry.
