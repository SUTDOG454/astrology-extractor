# OCR / Image Discrepancy Guidance

When extracting from images, screenshots or scanned documents, apply the following confidence and discrepancy protocol.

## Confidence Scoring

- **High**: Clear printed text, high-resolution chart, unambiguous glyphs and numbers.
- **Medium**: Slight blur, partial cropping, or mixed handwriting + print.
- **Low**: Heavy blur, low resolution, overlapping labels, or ambiguous handwriting.

Always report a confidence level for each extracted position or label when the source is an image.

## Common Pitfalls

- Degree symbols (°) vs colons or periods misread by OCR.
- Sign glyphs confused (e.g. Virgo vs Scorpio, Capricorn vs Aquarius).
- Retrograde (R / Rx) markers missed or mis-attached.
- House cusp numbers read as planetary degrees.
- Timezone or DST offsets omitted or misparsed from chart headers.

## Discrepancy Protocol

1. Extract the stated positions as given.
2. Recompute from birth data using at least two ephemerides.
3. Flag any difference larger than the tolerance (typically 0.01° for modern software, up to 0.1° for older printed tables).
4. Prefer the recomputed value for further calculations while preserving the original stated value and its provenance.
5. Note OCR confidence so the user can judge reliability.

## Batch Notes

When processing multiple images of the same chart, cross-check labels across frames and prefer the clearest reading for each planet or point.
