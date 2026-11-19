# twain-child-voice-ach-2026
# Mapping Child Voices in Mark Twain’s Fiction: A Computational Analysis

This repository contains code and supplementary materials for Manal Altammami’s conference paper, “Mapping Child Voices in Mark Twain’s Fiction: A Computational Analysis.”

The study combines corpus stylistics with close reading to examine lexical diversity, repetition, and vernacular language. It compares Twain’s child-centered novels with other American fiction and examines differences between narration and quoted speech.

## Corpus

The corpus contains 39 works:

| Group | Works |
|---|---:|
| Twain’s child-centered fiction | 3 |
| Non-Twain child fiction | 8 |
| Adult reference fiction | 28 |
| Total | 39 |

The primary texts are *The Adventures of Tom Sawyer* (1876), *The Prince and the Pauper* (1881), and *Adventures of Huckleberry Finn* (1884).

Texts were obtained from Project Gutenberg. The corpus metadata records the works, authors, publication years, corpus groups, and source URLs.

Whole-work comparisons include both narration and dialogue. The corpus groups therefore do not represent separate samples of children’s and adults’ speech.

## Repository structure

- `data/corpus_metadata.csv`: Corpus list and source information.
- `data/lexicon.csv`: The 218-entry dialectal and colloquial lexicon, with categories and sources.
- `data/review/`: Contextual review decisions and speaker-attribution records.
- `code/`: Analysis notebooks and scripts.
- `results/`: Counts, token totals, normalized frequencies, statistical comparisons, and robustness checks.
- `figures/`: Figures used in the paper.
- `requirements.txt`: Python dependencies and versions.

## Text preparation

Cleaning removed Project Gutenberg material, contents lists, captions, and chapter headings. Text boundaries were inspected, and selected stories within collections were retained.

Original spelling and vernacular forms were preserved. For word counts, texts were lowercased and curly apostrophes normalized. Tokenization retained single-letter words and internal apostrophes and hyphens but excluded leading apostrophes.

Quoted passages include both dialogue and storytelling. Unquoted passages mainly contain narration. Quotation boundaries therefore provide an approximate distinction between these narrative levels.

## Analyses

The code examines:

- Lexical diversity using MTLD and HD-D.
- Frequencies of *and*, *then*, *so*, and *but*, and lexical diversity after their removal.
- Repeated words and expressions discussed by Janet Holmgren McKay.
- Dialectal and colloquial matches using a 218-entry lexicon.
- Spelling variants discussed by Katherine Buxbaum.
- Verbal *a-*prefixing across works, speakers, and narrative levels.
- Frequency differences using log-likelihood tests.

Corpus-level lexical diversity scores were calculated from concatenated texts rather than averages of individual works. Vernacular and grammatical frequencies were normalized per 10,000 tokens.

The default lexical diversity settings were an MTLD threshold of 0.72 and an HD-D sample size of 42 tokens. Additional checks tested MTLD thresholds of 0.70, 0.72, and 0.74 and HD-D sample sizes of 42, 100, and 200 tokens.

## Language-model assistance and manual review

Language-model assistance supported speaker attribution and contextual review of lexicon matches.

Speaker attribution used reporting clauses and surrounding context. Every assignment was checked manually. Uncertain or unattributed passages remained in quoted totals but were excluded from individual character counts.

Lexicon matches were reviewed in context to distinguish vernacular uses from standard uses, names, and foreign-language expressions. The review excluded 151 uncertain matches. Reported frequencies represent retained matches rather than all vernacular language in the texts.

The verbal *a-*prefixing search produced 574 candidates. Contextual review retained 487 and excluded 87. The reviewed CSV records inclusion and exclusion decisions and their reasons. Retained forms include dialect spellings such as *a-goin’* and *a-gwyne*.

The reviewed files are necessary to reproduce the reported results; candidate extraction alone does not reproduce the final counts.

## Running the analysis

1. Download or clone this repository.
2. Install the dependencies:

   ```bash
   python -m pip install -r requirements.txt
