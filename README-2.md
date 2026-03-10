# KITAAB
## Knowledge Infrastructure for Textual Analysis of Arabic Books

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Project: Digital Maktaba](https://img.shields.io/badge/Project-Digital%20Maktaba-blue)](https://github.com/Digital-Maktaba-Project)
[![Status: In Progress](https://img.shields.io/badge/Status-In%20Progress-yellow)]()

---

## Overview

KITAAB is an open-source, integrated multi-modal dataset of Arabic Islamic books, developed as part of the [Digital Maktaba Project](https://github.com/Digital-Maktaba-Project) at FSCIRE (Foundation for Religious Sciences, Bologna) in collaboration with the University of Modena and Reggio Emilia and the University of Palermo.

The dataset is designed as shared research infrastructure serving multiple downstream tasks simultaneously: OCR model training on Arabic bibliographic scripts, LLM-based subject classification, and inductive taxonomy construction for Arabic and Islamic digital libraries.

Each record in KITAAB corresponds to a single Arabic Islamic book and comprises five components:

| Component | Format | Description |
|---|---|---|
| Bibliographic metadata | JSON / CSV | Title, author, subject, language, date |
| First and last ten pages | PDF | Paratextual zones for subject inference |
| Frontispiece image | JPG / PNG | High-resolution scan of the title page |
| Kraken OCR output | TXT | Raw OCR transcription of the frontispiece |
| Validated paratextual text | TXT | Corrected transcription of first and last ten pages |

---

## Motivation

### Methodological

The paratextual sampling strategy — the first and last ten pages of each volume — is grounded in established bibliographic practice. Front matter (titles, prefaces, tables of contents) and back matter (colophons, indices, concluding remarks) are the information-dense zones most productive for subject inference, as documented in the metadata extraction literature (Choi et al.; Tkaczyk et al.). For Arabic Islamic books specifically, these zones concentrate the bibliographic, structural, and thematic signals most relevant to subject classification.

### Legal

A consequential benefit of this structure is its compatibility with copyright constraints on open data publication. Since most legal frameworks permit the use of limited portions of a work, the first-and-last-ten-pages design represents the most extensive legally shareable unit of each volume, making open release possible without requiring full-text access. KITAAB is intended as a replicable model for open dataset construction in heritage contexts where full-text release is not possible.

### Infrastructural

To the knowledge of this project, no comparable dataset exists in the Arabic NLP or digital humanities literature. Existing Arabic text corpora are predominantly derived from news sources and social media, while Arabic book datasets focus on sentiment analysis of reader reviews rather than document content. KITAAB addresses this gap by providing a publicly available, replicable resource for LLM-based classification research on Arabic heritage materials.

---

## Dataset Structure

```
KITAAB/
├── metadata/
│   ├── kitaab_metadata.csv        # Full bibliographic metadata for all records
│   └── kitaab_metadata.json       # Same metadata in JSON format
├── books/
│   └── [book_id]/
│       ├── [book_id]_pages.pdf    # First and last ten pages
│       ├── [book_id]_front.jpg    # Frontispiece image
│       ├── [book_id]_ocr_raw.txt  # Raw Kraken OCR output
│       └── [book_id]_ocr_val.txt  # Validated paratextual transcription
└── README.md
```

### Metadata Fields

| Field | Description |
|---|---|
| `book_id` | Unique identifier |
| `title_arabic` | Title in Arabic script |
| `title_transliterated` | Transliterated title |
| `author_arabic` | Author name in Arabic script |
| `author_transliterated` | Transliterated author name |
| `subject` | Subject classification (La Pira topographic scheme) |
| `language` | Primary language of the text |
| `date` | Date of publication or composition (where known) |
| `source_library` | Holding institution |
| `frontispiece_available` | Boolean |
| `ocr_validated` | Boolean |

---

## Downstream Tasks

KITAAB supports three primary research tasks:

**1. OCR Model Training**
The frontispiece images paired with validated transcriptions provide training data for Kraken-based OCR workflows targeting Arabic bibliographic scripts, including Naskh, Thuluth, Ruqah, and Kufi styles found in historical frontispieces.

**2. LLM-Based Subject Classification**
The validated paratextual text layer supports evaluation of large language models on subject classification tasks against the La Pira Library's 52-topic controlled vocabulary, and against other classification schemes.

**3. Taxonomy Induction**
The corpus as a whole supports inductive taxonomy construction through multi-model LLM consensus analysis, as described in El Ganadi et al. (2025) and the ongoing Digital Maktaba Project methodology.

---

## Related Projects

- **Digital Maktaba Project** — LLM-assisted framework for Arabic digital libraries
- **KITAAB-OCR** — Kraken OCR fine-tuning pipeline for Arabic bibliographic scripts (forthcoming)
- **La Pira Library Topographic Classification** — FSCIRE institutional subject scheme
- **Giorgio La Pira Library, FSCIRE** — Source collection

---

## Citation

If you use KITAAB in your research, please cite:

```bibtex
@dataset{elganadi2026kitaab,
  author       = {El Ganadi, Amina},
  title        = {KITAAB: Knowledge Infrastructure for Textual Analysis of Arabic Books},
  year         = {2026},
  publisher    = {Digital Maktaba Project},
  url          = {https://github.com/Digital-Maktaba-Project/KITAAB},
  note         = {Dataset in preparation}
}
```

And the associated journal article:

```bibtex
@article{elganadi2025digitalmaktaba,
  author  = {El Ganadi, Amina and Gagliardelli, Luca and Ruozzi, Federico},
  title   = {Digital Maktaba project: Toward a metadata-driven, LLM-assisted framework for arabic digital libraries},
  journal = {International Journal on Digital Libraries},
  volume  = {26},
  pages   = {19},
  year    = {2025},
  doi     = {10.1007/s00799-025-00432-w}
}
```

---

## License

The dataset is released under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You are free to share and adapt the material for any purpose, provided appropriate credit is given.

Individual book contents remain subject to the copyright of their respective publishers. KITAAB contains only legally shareable portions of each volume in accordance with applicable copyright frameworks.

---

## Contributors

**Amina El Ganadi**
PhD Candidate, Digital Humanities and Islamic Studies
University of Modena and Reggio Emilia / University of Palermo
Research Fellow, FSCIRE (Foundation for Religious Sciences, Bologna)

---

## Contact

For questions, contributions, or collaboration inquiries, please open an issue or contact the project maintainer via the Digital Maktaba Project GitHub organisation.

---

## Status

KITAAB is currently in active preparation. The first release will include a curated subset of books from the Giorgio La Pira Library (FSCIRE). Full release and documentation are forthcoming.
