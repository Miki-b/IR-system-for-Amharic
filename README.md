

# **Amharic Information Retrieval System**

## **Introduction and Overview**

We are currently enhancing the retrieval process of Amharic search engines. This project focuses on developing efficient text preprocessing, indexing, and creating a posting file. After weighing every term in the corpus using **TF-IDF**, the IR system compares these weights with a given query using **Cosine Similarity** and ranks the documents for retrieval.

---

## **Statement of the Problem and Justification**

Amharic is the official working language of the Federal Democratic Republic of Ethiopia and is spoken by over 20 million people. Despite its wide use in text processing activities in governmental, non-governmental, and private institutions, there are no standardized tools available for Amharic text processing, including:

- No affixes dictionary for Amharic.
- Lack of a general stemmer for Amharic text.
- Absence of a standard stop-word list.

We aim to address these gaps using the **Hornmorphology Stemmer** for extracting the roots of words, despite the algorithm's inefficiency at times. We will enhance it to handle large text more efficiently.

---

## **Methodology**

This project is divided into four main parts, each addressing a specific problem in the IR system, from text preprocessing to query optimization and retrieval:

### **Part 1: Text Processing Pipeline**

- **Objective**: Process Amharic language documents using various Python libraries to extract, normalize, and tokenize text.
- **Key Actions**:
  - Extract text from **PDF files**.
  - Tokenize and normalize text, handling Amharic punctuation and apostrophes.
  - Analyze word frequencies and remove high-frequency index terms.
  - Save filtered tokens to a file for further use in indexing.

### **Part 2: Stop Word Removal and Index Generation**

- **Objective**: Remove stop words to improve text analysis and create an index.
- **Key Actions**:
  - Read stop words from **"stopwords.txt"**.
  - Remove stop words from tokenized text.
  - Write the resulting words (index) to **"index.txt"** for future use in retrieval.

### **Part 3: Creating the Inverted Index**

- **Objective**: Build an inverted index for fast document retrieval.
- **Key Actions**:
  - Create a dictionary of tokens, document IDs, and word frequencies.
  - Use the **pickle module** for serializing the data to save the document vectors.
  - Load and retrieve document vectors for efficient search operations.

### **Part 4: Query Optimization and Retrieval**

- **Objective**: Rank documents based on their relevance to a query using **TF-IDF** and **Cosine Similarity**.
- **Key Actions**:
  - Create document vectors using **TF-IDF** scores.
  - Calculate **Cosine Similarity** between the document vectors and the query vector.
  - Rank and retrieve the most relevant documents for a given query.

---

## **Why Python Was Chosen**

We chose **Python** due to its extensive libraries and simplicity. Python's ecosystem is rich with tools for **Natural Language Processing (NLP)**, making it an ideal choice for handling the complexities of Amharic text processing. Key libraries used in this project include:

- **nltk.tokenize**: For tokenizing the text.
- **re**: For regular expression operations.
- **os**: For handling file operations.
- **collections**: Specifically, `Counter` for word frequency counting.
- **pdfminer.high_level**: For PDF text extraction.
- **matplotlib.pyplot**: For data visualization.
- **pickle**: For serializing and deserializing Python objects.

---

## **Challenges Faced**

- **Corpus Collection**: Gathering a large and representative corpus of Amharic text was a significant challenge due to resource limitations.
- **Suffix Removal**: Amharic words have complex suffixes, and finding a standard list for effective removal was difficult.
- **Stemming**: Designing an efficient stemmer for Amharic was challenging due to the language's extensive dictionary and morphological complexity.
- **Cut-off Points**: Deciding on appropriate cut-off points for frequent words to ensure both significant and less common terms are retained.

---

## **Determining Cut-off Points**

The process of deciding on cut-off words was tedious, as it required determining a threshold to remove common words while retaining significant terms. Our initial cut-off aimed for:
- A percentage cutoff greater than **20%**.
- Removal of words that occurred **less than once** in the corpus.

---

## **Terms Chosen as Indices**

Indexing terms are selected after stemming and stop word removal. These terms include the roots of tokens, excluding the most common words. The final index is created by generating a dictionary with the token as the key and the **Document ID** and **frequency** of the word as the value.

---

## **Conclusion**

The development of an **Amharic Information Retrieval System** has provided invaluable insights into natural language processing, especially for low-resource languages like Amharic. The system addresses the morphological complexities of Amharic, including its distinct script and intricate word formation processes. By utilizing **TF-IDF** and **Cosine Similarity**, we have tailored traditional information retrieval techniques to meet the unique challenges of Amharic text processing.

This work has paved the way for future advancements in the field and demonstrates the potential for language technology solutions that can be adapted to the needs of individual languages.

---



