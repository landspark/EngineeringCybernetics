# Engineering Cybernetics

[![Organization](https://img.shields.io/badge/org-Landspark-blue)](https://github.com/landspark) 
[![Format](https://img.shields.io/badge/format-Markdown%20%2B%20LaTeX-green)](#) 
[![Data Language](https://img.shields.io/badge/Data-中文%20%7C%20Chinese-red)](#)

## Languages

- English: [README.md](./README.md)
- 汉语: [README.zh-cn.md](./README.zh-cn.md)

## Background

*Engineering Cybernetics* is a masterwork by QIAN Xuesen (H.S. Tsien). The system analysis, feedback logic, and state-space theories within are not only foundational to modern control engineering but also hold immense guiding value for Artificial Intelligence, complex systems analysis, and cross-disciplinary modeling today.

However, traditional scanned PDFs are entirely opaque to Large Language Models (LLMs) and modern Retrieval-Augmented Generation (RAG) systems. 

This project aims to reconstruct the entire book (3rd Edition, Chinese) into a high-signal-to-noise ratio, pure-text database. We (Landspark Digital Tech) have transformed the book into Markdown format, complete with precisely transcribed LaTeX mathematical equations and native tables. This allows developers to directly ingest, analyze, and call upon these classic engineering theories using AI tools without the friction of complex formatting barriers.

## Original Source Information

For strict academic tracking and cross-validation, this digital knowledge base is extracted from the following physical publication:

* **Title**: Engineering Cybernetics (Vol. 1 & 2) - 3rd Edition
* **Authors**: QIAN Xuesen (H.S. Tsien), SONG Jian
* **Series**: Chinese Classic Texts of Science and Technology
* **Publisher**: Science Press (Beijing, China)
* **Date of Publication**: February 2011
* **ISBN**: 978-7-03-030094-2

## Data Processing Pipeline

To convert hundreds of pages of complex literature into structured text, we implemented a semi-automated ETL pipeline:

* **Baseline Extraction**: We utilized MinerU to parse the scanned pages, extracting the raw text, mathematical equations, and base tables.
* **Table Reconstruction**: For complex HTML tables exported by MinerU, we deployed LLM agents to forcefully compress and convert them into native, dependency-free Markdown tables for maximum compatibility.
* **Regex Cleaning & Human QA**: We utilized regular expressions bundled with human verification to batch-replace English punctuation—erroneously introduced by OCR engines—with standardized Chinese typographic punctuation.
* **Non-Textual Data Parsing**: The original book contains numerous explanatory bitmap images. For maximum index efficiency, we stripped these visual assets and replaced them with text-based "image placeholders" (retaining only the original figure numbers and captions).

## Directory Structure

The entire book (including the foreword and appendices) has been modularized into 23 Markdown files located in the `docs/` directory:

* `chapter_000.md` (Introduction & Foreword)
* `chapter_001.md` to `chapter_021.md` (Core content: Chapters 1 through 21)
* `chapter_022.md` (Appendix: Selected bibliography of Chinese works)
* The root directory contains a custom `LICENSE` file detailing absolute copyright constraints.

## Known Issues

During the regex cleaning and transformation pipeline, an operational error unintentionally purged a subset of the "image placeholders" that should have been retained. 

Consequently, while reading or ingesting the data, you may encounter missing figure tags or captions. Due to bandwidth constraints, these specific gaps have not been fully patched.

## Contribution Protocol

The core architecture and baseline data are now deployed. Given the immense volume of complex mathematical operators and potential OCR hallucinations, we welcome community compute power:

* Missing LaTeX symbols or transcription errors
* Typographical or punctuation anomalies
* Restoring accidentally deleted image placeholders

Please feel free to open an **Issue** with exact coordinates, or preferably, submit a **Pull Request (PR)** to directly patch the system.

## Copyright & License Boundaries

* The intellectual property of the original text, concepts, and physical formulas belongs absolutely to the original authors (QIAN Xuesen, SONG Jian) and Science Press. We pay the highest respect to their original intellect.
* Our digital reconstruction, Markdown architecture, and LaTeX transcription pipelines are licensed strictly for non-commercial academic research and NLP/AI model training.
* **Using this repository for direct commercial profit is absolutely prohibited.** For precise legal boundaries, you must read the custom `license` file in the root directory.
