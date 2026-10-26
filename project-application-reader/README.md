# XX Project workspace

Notes and tools for reading `XX.pdf` (application) with a focus on the Norwegian Meteorological Institute. See `AGENTS.md` for working rules and `MET_CONTRIBUTION.md` for extracted results and `XX.md` for Met's WPX tasks in relation to the XX pilot.

## Environment

```bash
mamba env create -f environment.yml   # creates XX (conda-forge, PyMuPDF)
```

## PDF tools

```bash
python pdf_tools/extract_pdf_text.py          # per-page text and keyword hit pages into pdf_work/
python pdf_tools/render_pages.py 33 47        # render pages to pdf_work/png/ to check tables and figures
```

`pdf_work/` holds generated files and can be deleted and regenerated.
