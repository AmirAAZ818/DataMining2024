# Persian News Similarity with Cosine Distance

This assignment demonstrates the use of **cosine similarity** for comparing the semantic similarity between three Persian news articles from different topics. The goal is to highlight how content-based text similarity can distinguish between related and unrelated news using text vectorization and similarity scoring.

## Objective

To fetch Persian news articles from the web, process their content using NLP techniques, and compute cosine similarity between pairs to analyze semantic closeness.

## Tools and Libraries

The following Python libraries and tools were used:

- `requests`, `BeautifulSoup` – for web scraping

- `re` (Regular Expressions) – Python’s built-in module for basic text pattern matching and substitutions during preprocessing.

- `hazm` – A Python library specifically designed for Persian natural language processing. It includes tools such as:

  - Text normalization

  - Sentence and word tokenization

  - Part-of-speech tagging (POS)

  - Pre-trained Persian word/sentence embedding models

- `nltk` (Natural Language Toolkit) – A general-purpose NLP library used here for:

  - Parsing grammatical structures (e.g., noun phrases) with RegexpParser

  - Structuring and walking through POS-tagged parse trees

- `numpy` – for numerical computations and cosine similarity

- Pre-trained `POS Tagger` and `Sent2Vec` models – for grammatical parsing and sentence embedding

## Workflow

### 1. Web Scraping

Three Persian news articles from the *Tasnim News Agency* website were scraped. Topics included:

- News 1: Iranian Football
- News 2: Astronomy
- News 3: International Football

Each article’s content was extracted from the HTML `<div class="story">` section.

### 2. Text Preprocessing

Each article went through a preprocessing pipeline:

- Text normalization (e.g., diacritics and zero-width non-joiner removal)
- Sentence and word tokenization
- Stopword removal using Hazm
- POS tagging using a pre-trained Hazm POS tagger
- Extraction of noun phrases (NPs) using defined grammar patterns

### 3. Embedding with Sent2Vec

Keyword phrases from each article were embedded into a fixed-size vector using a **pre-trained Sent2Vec** model from Hazm.

### 4. Cosine Similarity Calculation

Pairwise cosine similarity was computed using the formula:

$$
\text{similarity} = \frac{\vec{A} \cdot \vec{B}}{||\vec{A}|| \cdot ||\vec{B}||}
$$

## Results

The similarity scores between each pair of news articles are summarized below:

| News Pair             | Cosine Similarity |
|-----------------------|-------------------|
| News 1 (Football - Iran) & News 2 (Astronomy) | 0.34              |
| News 1 & News 3 (Football - International)    | 0.36              |
| News 2 & News 3                                | 0.22              |

## How to Run

1. Make sure the following models are present in a `models/` directory:
   - `pos_tagger.model`
   - `sent2vec-naab.model`
2. Install required dependencies:

   ```bash
   pip install -r requirements.txt
    ```
