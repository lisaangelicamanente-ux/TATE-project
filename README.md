# TATE artwork titles analysis
Digital humanities research project 
## An Exploratory Analysis of Artwork Titles in the Tate Collection

## 1. Research Question

This project aims to investigate how the language used in artwork titles within the Tate collection can reflect institutional and historical patterns in collecting practices across the twentieth century. Rather than treating titles as direct expressions of artistic intent, the project approaches them as hybrid objects shaped by artistic conventions, curatorial decisions, and cataloguing practices.

The central research question is:

**How do the words used in artwork titles in the Tate collection reflect large-scale descriptive and institutional patterns, and how do these patterns change over time?**

---

## 2. Dataset

The project uses the openly available Tate Collection dataset, accessed via the Tate Gallery’s public GitHub repository. The dataset contains metadata for artworks in the Tate collection, including titles, artists, dates, materials, and acquisition information.

Only the artwork-level metadata was used in this project, with particular focus on the following fields:

- `title`: artwork title  
- `year`: year of production  
- `dateText`: textual date description (used when `year` was missing)

The dataset is provided as a CSV file and can be programmatically accessed and reproduced using the code included in this repository.

---

## 3. Data Processing and Pipeline

The analysis follows a simple, reproducible pipeline consisting of the following steps:

1. **Data loading**  
   The dataset is downloaded directly from the Tate GitHub repository using a fixed URL.

2. **Title filtering and cleaning**  
   - Records with missing titles were removed.  
   - Non-informative cataloguing placeholders such as `[title not known]` and variants were excluded.  
   - Titles beginning with `Untitled` were removed.  
   - Titles were lowercased and stripped of punctuation for consistency.

3. **Temporal normalization**  
   - Numeric years were extracted from both structured (`year`) and unstructured (`dateText`) fields.
   - Only artworks dated from 1900 onwards were retained, allowing for a temporal focus on modern and contemporary collecting practices.

4. **Tokenization and lexical processing**  
   - Titles were tokenized into individual words using NLTK.
   - English stopwords were removed to reduce noise from highly frequent but semantically weak terms.

5. **Frequency analysis**  
   - Global word frequencies were calculated across the full dataset.
   - A long-tail (Zipf-like) distribution was visualized to assess overall lexical structure.

6. **Diachronic analysis**  
   - Artworks were grouped by decade based on normalized years.
   - Word frequencies were calculated per decade to explore temporal patterns in title language.

All processing steps are fully implemented in the provided notebook and can be rerun to reproduce the results.

---

## 4. Results

The analysis reveals that the vocabulary of artwork titles follows a pronounced long-tail (Zipf-like) distribution: a small number of highly frequent, generic terms account for a large proportion of all titles, while the majority of words appear only rarely.

Frequently occurring terms tend to be descriptive or classificatory (e.g. genre-related or formal descriptors), whereas expressive or emotionally charged words are comparatively rare. When examined diachronically, some shifts in vocabulary can be observed across decades, suggesting changes in artistic practices as well as institutional framing.

Rather than providing detailed semantic interpretation, these results highlight large-scale patterns in how artworks are named and categorized within an institutional context.

The findings suggest that artwork titles in the Tate collection are strongly shaped by institutional and descriptive conventions. The dominance of generic terms indicates that titles often function as classificatory labels rather than expressive statements.

The long-tail structure of the vocabulary also demonstrates the limitations of automated semantic or sentiment-based approaches for this type of data. Most potentially meaningful or expressive words occur too rarely to support robust quantitative generalization without substantial interpretive intervention.

---

## 5. Limitations and Biases

Several limitations affect the analysis:

- Titles are not always authored by artists and may reflect curatorial or archival decisions.
- Editorial placeholders and cataloguing conventions introduce institutional bias.
- The dataset is English-language–centric, potentially obscuring multilingual practices.
- Word frequency analysis captures surface-level patterns and does not account for contextual meaning.

---

## 6. Reproducibility

This repository contains all code necessary to reproduce the analysis. The main notebook can be run end-to-end to regenerate all intermediate and final outputs. The project follows open research principles and is archived via Zenodo to ensure long-term accessibility and citability.


