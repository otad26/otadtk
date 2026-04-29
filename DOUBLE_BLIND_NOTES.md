# Anonymity Notes (for reviewers)

This package was prepared for double-blind review at NeurIPS 2026
(Evaluations & Datasets track). The single source of truth for the
review-period URL is the OpenReview submission record; this source tree
itself contains no material that identifies the authors or their
institutions.

## What we audited

| Axis | Status |
|------|--------|
| `pyproject.toml` `authors` | `Anonymous Author(s) <anonymous@example.org>` |
| `pyproject.toml` `project.urls` | Intentionally omitted during review |
| `LICENSE` copyright holder | `Anonymous Author(s)` |
| `README.md` | No author/affiliation, no arXiv badge, no embedded code-host URL |
| Source-file headers | No author / institution comments |
| Adapter checkpoint metadata (`.pt`) | Only `encoder`, `loss_type`, `epoch`, `loss` — no author or hostname |
| **Adapter checkpoints** | **All 18 bundled under `otadtk/checkpoints/`; package runs end-to-end with no network access** |
| Reference encoders | Loaded from official public hubs (HuggingFace / TF-Hub / `torch.hub`); those calls do not reveal our identity |
| Citation block | Anonymous BibTeX placeholder |

If you discover any artefact that violates anonymity, please notify the area
chair; we will release a corrected snapshot.

## How a reviewer reproduces every result

```bash
# (URL filled in by the OpenReview submission record)
unzip otadtk.zip && cd otadtk          # or: clone the anonymous mirror
pip install -e .                        # 37 MB wheel, 18 adapters bundled
python -m pytest tests/ -q              # 7 smoke tests, no network needed
otadtk vggish ref/ eval/ --diagnose     # OTAD on real audio
```

## After acceptance (camera-ready plan)

This file will be removed and the toolkit will be re-released with author
identifiers as follows:

1. **GitHub** (de-anonymised, full commit history, issues, CI).
2. **PyPI** — `pip install otadtk` from the public index, with `project.urls`
   re-populated.
3. **Zenodo DOI** for long-term archival of the exact reviewed snapshot.
4. **HuggingFace Hub** — optional separate hosting of the checkpoints, in
   case the wheel size limit on PyPI tightens in the future.
