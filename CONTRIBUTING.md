# Contributing to Astrology Extractor

Thank you for your interest in improving this skill.

## Development Guidelines

1. **Keep the skill self-contained**  
   All core logic should live in `SKILL.md` + `references/` + `scripts/`. Avoid external runtime dependencies unless strictly necessary.

2. **Update documentation in lock-step**  
   - New technique → update the relevant file under `references/`  
   - New script capability → update the Scripts table in `README.md` and the Resources section of `SKILL.md`  
   - Schema changes → update `references/output-schema.md`

3. **Scripts**  
   - Prefer pure Python + standard library  
   - Include a usable `__main__` demo  
   - Document expected input/output in the module docstring

4. **Extraction fidelity**  
   Never invent positions or delineations. Always preserve original wording and provenance.

5. **Testing**  
   Run the script demos and, when possible, validate against known charts from JPL Horizons or Astro.com.

## Pull Request Checklist

- [ ] `SKILL.md` description and workflow still accurate  
- [ ] Relevant reference file(s) updated  
- [ ] README Scripts / References sections updated if needed  
- [ ] No `__pycache__` or local secrets committed  
- [ ] New scripts have a short demo in `__main__`

## Questions / Ideas

Open an issue describing the technique or improvement you want to add. Clear scope makes review much faster.
