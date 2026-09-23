# Sample Extraction Templates

## Markdown Report Skeleton

```markdown
# Extraction Report — [Source Title / Birth Data]

## Source
- Type: [PDF / image / text / …]
- Provenance: …
- Confidence (if OCR): High / Medium / Low

## Birth / Event Data
| Field | Value |
|-------|-------|
| Date | … |
| Time | … |
| Place | … |
| Coordinates | … |
| House system | … |
| Zodiac / Ayanamsa | … |

## Planetary Positions (verified)
| Body | Longitude | Sign | House | Notes |
|------|-----------|------|-------|-------|
| … | … | … | … | … |

## Aspects
…

## Midpoints / Planetary Pictures (ranked)
…

## Delineations (original wording preserved)
…

## Verification Notes
- Sources used: JPL, Astro.com, …
- Discrepancies: …
```

## JSON Skeleton

See `output-schema.md` for the full schema. Minimal top-level keys:

```json
{
  "source": {},
  "birth_data": {},
  "positions": [],
  "aspects": [],
  "midpoints": [],
  "harmonic_aspects": [],
  "fixed_stars": [],
  "kp_data": {},
  "delineations": [],
  "verification": {}
}
```
