# Astrology Extractor

[![CI](https://github.com/SUTDOG454/astrology-extractor/actions/workflows/ci.yml/badge.svg)](https://github.com/SUTDOG454/astrology-extractor/actions/workflows/ci.yml)

**A comprehensive Grok / agent skill for extracting, verifying, and enriching every form of astrological data.**

Extract delineations, interpretations, formulas, calculations, keywords, methods, planetary positions, aspects (major / minor / harmonic), midpoints & Cosmobiology weighting, houses, dignities, timing techniques, Arabic Parts, fixed stars, Vedic dashas/yogas, traditional techniques, KP sub-lords, cuspal sub-lords, significators and Ruling Planets — from any document or image.

Always cross-check positions against multiple independent online ephemerides and produce dual, fully-expanded **Markdown + JSON** output.

## Features

- **Universal input** — PDF, DOC/DOCX, RTF, TXT, JSON, JPEG, PNG, TIFF, BMP, screenshots, handwritten notes, user-pasted data
- **Exhaustive extraction** — positions, aspects, midpoints, harmonic aspects, fixed stars, Lots, dignities, timing techniques, KP system, Vedic & traditional methods
- **Multi-source verification** — NASA JPL Horizons, Swiss Ephemeris (Astro.com), Astro-Seek, CosmyDay
- **Cosmobiology support** — refined midpoint weighting protocol, planetary pictures, 90° dial logic, COSI-style keyword guidance
- **Harmonic astrology** — full 1–12 harmonic families with orbs and delineation notes (5th/7th/9th/11th especially)
- **KP astrology** — sub-lords, cuspal sub-lords, significators, Ruling Planets, 4-step method
- **Dual output** — richly structured Markdown report + complete machine-readable JSON

## Repository Structure

```
astrology-extractor/
├── SKILL.md                          # Core skill instructions (agent entry point)
├── README.md                         # This file
├── LICENSE                           # MIT License
├── .gitignore
├── requirements.txt                  # Optional Python dependencies for scripts
├── references/                       # Detailed reference material
│   ├── arabic-parts-lots-fixed-stars.md
│   ├── ephemeris-sources.md
│   ├── extraction-checklist.md
│   ├── house-systems-and-ayanamsas.md
│   ├── kp-astrology.md
│   ├── midpoints-aspects-harmonics-fixedstars.md
│   ├── ocr-image-discrepancy-guidance.md
│   ├── output-schema.md
│   ├── sample-extraction-templates.md
│   └── traditional-and-vedic-techniques.md
└── scripts/                          # Helper utilities
    ├── arabic_parts.py
    ├── chart_helpers.py
    ├── cosmyday_client.py
    ├── degree_utils.py
    ├── jpl_horizons.py
    ├── kp_sublord.py
    └── midpoints_aspects.py
```

## Quick Start (as a Grok Skill)

1. Place the entire folder under your skills directory (e.g. `~/.grok/skills/astrology-extractor/` or the equivalent path used by your agent).
2. The skill activates automatically on any astrological content, birth data, ephemeris tables, chart descriptions or interpretive text.
3. Output is always dual-format: fully expanded Markdown + complete JSON.

## Scripts Overview

| Script | Purpose |
|--------|---------|
| `degree_utils.py` | Longitude ↔ sign/DMS conversion, parsing, angular distance |
| `chart_helpers.py` | Julian Day, aspect detection, essential dignity, position normalization |
| `jpl_horizons.py` | NASA JPL Horizons API wrapper for precise ephemeris |
| `cosmyday_client.py` | Free CosmyDay natal + geocode client |
| `arabic_parts.py` | Part of Fortune, Spirit and other major Lots (with sect) |
| `kp_sublord.py` | KP sign / star / sub-lord calculation from absolute longitude |
| `midpoints_aspects.py` | Midpoint calculation, Cosmobiology-style weighted ranking of planetary pictures, major/minor & harmonic aspect detection |

Run any script directly for a quick demo:

```bash
python scripts/midpoints_aspects.py
python scripts/kp_sublord.py --help
```

## References Highlights

- **midpoints-aspects-harmonics-fixedstars.md** — Refined Cosmobiological weighting protocol, COSI delineation guidance, full harmonic tables (1–12), fixed-star parameters
- **kp-astrology.md** — Complete KP methods, sub-lords, CSL, significators, Ruling Planets, 4-step method
- **extraction-checklist.md** — Exhaustive checklist used by the skill
- **output-schema.md** — JSON schema for structured output
- **ephemeris-sources.md** — Preferred verification sources and query patterns

## Output Philosophy

- **Fully expanded** — never collapse rich delineations into short summaries unless explicitly requested
- **Provenance preserved** — every extracted interpretation keeps its source wording and reference
- **Verified** — every planetary position is recomputed from at least two independent ephemerides
- **Enriched** — original data is augmented with calculated midpoints, weighted pictures, harmonic aspects, dignities, etc. when useful

## CI / CD (GitHub Actions)

Workflows live in `.github/workflows/`:

| Workflow | Trigger | What it does |
|----------|---------|--------------|
| **CI** (`ci.yml`) | Push / PR to `main` | Validates repo structure, Python syntax on 3.11 & 3.12, runs script demos, optional Ruff lint |
| **Release** (`release.yml`) | Tag `v*` or manual | Creates a GitHub Release with auto-generated notes |

After the first successful push of these workflows, the CI badge at the top of this README will turn green.

To cut a release:

```bash
git tag v0.1.0
git push origin v0.1.0
```

## License

MIT License — see [LICENSE](LICENSE).

## Contributing

Issues and pull requests are welcome. When adding new techniques or scripts, please:

1. Update the relevant reference file(s)
2. Keep `SKILL.md` description and workflow in sync
3. Add or extend tests / demos in the script’s `__main__` block
4. Prefer pure-Python helpers with minimal external dependencies

---

*Built for rigorous, multi-tradition astrological extraction and verification.*
