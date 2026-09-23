---
name: astrology-extractor
description: Extract all astrological data — delineations, interpretations, formulas, calculations, keywords, methods, positions, aspects (major minor harmonic), midpoints and midpoint weighting, houses, dignities, timing techniques, tables, charts, Arabic Parts, fixed stars, Vedic dashas/yogas, traditional techniques, KP sub-lords cuspal sub-lords significators and Ruling Planets — from any document or image (PDF, DOC, RTF, TXT, JSON, JPEG, PNG, TIFF, BMP, user data). Verify every planetary position and recalculate natal, transit, progression, secondary progression, draconic and related charts using multiple online ephemerides (JPL Horizons, Astro.com Swiss Ephemeris, Astro-Seek, CosmyDay). Always output fully expanded, enriched Markdown plus complete JSON. Trigger on any astrological content, birth data, ephemeris tables, chart descriptions or interpretive text.
---

# Astrology Extractor

Extract, structure, verify and enrich every piece of astrological data found in documents, datasets or images. Always cross-check positions against multiple independent online ephemerides and produce dual fully-expanded Markdown + JSON output.

## When to Activate

Activate on any input containing or requesting:
- Planetary positions, signs, degrees, houses, aspects, orbs, dignities
- Natal, transit, progressed, secondary progressed, draconic, solar/lunar return, profection, direction, dasha or other chart/timing data
- Delineations, interpretations, keywords, formulas, calculation methods, Arabic Parts, fixed stars
- Ephemeris tables, birth data, event times, chart wheels, screenshots or scanned pages
- Any document or image type listed in the description

## Core Workflow

1. **Ingest & classify**
   - Text / RTF / plain / JSON → parse directly.
   - PDF → pdf skill (text + tables; OCR if scanned).
   - DOC / DOCX → docx skill.
   - Images (JPEG, PNG, TIFF, BMP) → view_image + OCR / vision; extract all numbers, glyphs, labels, handwritten notes.
   - Mixed or user-pasted data → free-form source.
   - See references/ocr-image-discrepancy-guidance.md for confidence scoring and pitfalls.

2. **Extract exhaustively** (use references/extraction-checklist.md + traditional-and-vedic-techniques.md)
   - Birth/event data (date, time, timezone, place, coordinates, house system, zodiac, ayanamsa, calendar)
   - All planetary & point positions (longitude, latitude, speed, retrograde, sign, degree, house)
   - Aspects (major/minor, orb, applying/separating, patterns: T-square, grand trine, yod, etc.)
   - House cusps & angles (ASC, MC, DSC, IC)
   - Arabic Parts / Lots, fixed stars, asteroids, nodes, Lilith, Chiron, Vertex, etc.
   - Essential & accidental dignities, scores, dispositors, reception, almuten
   - Timing: transits, secondary/tertiary/minor progressions, solar arc, primary directions, profections, zodiacal releasing, firdaria, returns, dashas, etc.
   - Formulas, orb tables, keyword lists, full delineations (preserve original wording + provenance)
   - Tables, example charts, ephemeris excerpts, Vedic yogas/vargas/nakshatras when present

3. **Structure**
   Hierarchical sections. Keep original delineation text intact while adding structured fields.

4. **Verify & recalculate** (minimum two independent sources)
   - NASA JPL Horizons (scripts/jpl_horizons.py or direct API) — astronomical ground truth
   - Astro.com / Swiss Ephemeris (browser_tab / open_page)
   - Astro-Seek free calculators
   - CosmyDay free API (scripts/cosmyday_client.py)
   - Recalculate natal, transit, secondary progressed, draconic and any other chart present
   - Use scripts/degree_utils.py, chart_helpers.py, arabic_parts.py for normalization, aspects, Lots, dignities
   - Side-by-side comparison; flag discrepancies (see ocr-image-discrepancy-guidance.md tolerances)

5. **Enrich**
   - Compute missing midpoints and rank planetary pictures with Cosmobiology weighting (scripts/midpoints_aspects.py)
   - Detect major, minor and harmonic aspects
   - Apply KP sub-lord / cuspal sub-lord logic when KP data is present (scripts/kp_sublord.py)
   - Expand keywords and cross-reference COSI-style delineations when relevant

6. **Output**
   - Fully expanded Markdown report (tables, hierarchical sections, provenance)
   - Complete JSON matching references/output-schema.md
   - Never collapse rich text unless the user explicitly asks for a summary

## Resources

**References**
- extraction-checklist.md — exhaustive extraction checklist
- ephemeris-sources.md — preferred verification sources and query patterns
- output-schema.md — JSON schema for structured output
- house-systems-and-ayanamsas.md — house systems and ayanamsa list
- sample-extraction-templates.md — Markdown + JSON templates
- arabic-parts-lots-fixed-stars.md — Lots formulas, fixed-star guidance
- traditional-and-vedic-techniques.md — Hellenistic, traditional & Vedic checklist
- ocr-image-discrepancy-guidance.md — image/OCR confidence, discrepancy protocol, batch notes
- kp-astrology.md — full KP methods, sub-lords, CSL, significators, Ruling Planets, 4-step method, horary
- midpoints-aspects-harmonics-fixedstars.md — midpoints, refined Cosmobiological weighting protocol, refined COSI delineation, expanded harmonic aspects (full 1–12 table, orbs, 5/7/9/11 delineation notes), fixed-star parameters

**Scripts**
- jpl_horizons.py — JPL Horizons API helper
- cosmyday_client.py — free CosmyDay natal + geocode client
- degree_utils.py — longitude/sign/DMS conversion, parsing, angular distance
- chart_helpers.py — Julian Day, aspects, essential dignity, position normalization
- arabic_parts.py — Part of Fortune, Spirit and other major Lots
- kp_sublord.py — compute KP sign/star/sub lords from any absolute longitude
- midpoints_aspects.py — midpoint calculation, occupied pictures, refined Cosmobiology weighting + cluster weight-of-evidence, major/minor aspects, harmonic aspect detection with conventional names (Quintile, Septile, etc.)

## Anti-patterns

- Do not invent positions or interpretations absent from source or verified calculation.
- Do not rely on a single ephemeris.
- Do not omit the JSON output or collapse rich delineations into short summaries (unless user explicitly asks).
- Do not drop provenance or confidence information for OCR/image data.
