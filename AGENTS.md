# AGENTS.md — RSI lab companion

## Google Docs are the single source of truth (HARD)

- **Deliverable = live Google Docs** listed in [`docs/GDOC_IDS.json`](docs/GDOC_IDS.json). Ken reviews Docs only.
- `manuscript/*.md` is **local staging** (gitignored). Markdown edits are not shipped until published.
- After any chapter prose/outline/figure/table/heading change, publish before claiming done:
  `python scripts/publish_chapter_to_gdoc.py --ch N`
  If H2s changed: `python scripts/build_master_toc.py`
- Never create replacement chapter Docs. Never commit chapter prose to GitHub.

## Packt citation rules

Chapter prose for this title follows [`docs/CITATION_RULES.md`](docs/CITATION_RULES.md):

- No end-of-chapter References/Sources section.
- First citation of a work in a chapter: canonical URL inline once.
- Same URL must not repeat in that chapter; later mentions use prose back-reference.
- Quantitative claims must exist in [`docs/VERIFIED_FACTS.md`](docs/VERIFIED_FACTS.md).

## Contracts lock

[`CONTRACTS.md`](CONTRACTS.md) defines the locked interfaces for this running lab.

- Do **not** change schemas under `schemas/` or the glossary/surface enum without Lead approval.
- Implementations live under `rsi_core/` and lab packages that import those schemas.
- Writes to ownership-manifest `locked` paths must raise `LockedPathError`.

## Lab conventions

- Python 3.11+, type hints, stub ML only (no real GPU/LoRA training).
- Prefer envelopes, gates, and hash-chained ledgers over invented benchmark numbers.
- Run tests with `pip install -e ".[dev]"` then `pytest -q`.
