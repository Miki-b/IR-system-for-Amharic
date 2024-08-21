Introduction and Overview

We are currently working on enhancing the retrieval process of Amharic search engines. This project focuses on developing efficient text preprocessing, indexing, and creating a posting file. After weighing every term in the corpus using tf*idf, the IR system will compare these weights with a given query using cosine similarity and rank the documents for retrieval.

Statement of the problem and Justification

Amharic is the official working language of the federal government of the Federal Democratic Republic of Ethiopia and is estimated to be spoken by well over 20 million people as a first or second language. Amharic is the second most spoken Semitic language in the world (next to Arabic). Amharic is widely used in text processing activities in governmental, non governmental and private institutions. Increased availability of large scale Amharic documents in electronic format and affordable computer resources are good opportunities for developing automatic Amharic information retrieval systems.

According to the information obtained from various sources during the assessment of the current situation of the technology in the field (Amharic information retrieval), the following problems are identified: 
• There is no available standard affixes dictionary for Amharic text 
 • There is no general stemmer to be used in indexing for Amharic text, and
 • There is lack of a standard stop-word list.
To asses this problem, we have used the hornmorphology stemmer to extract the roots of words in a document. While this algorithm might be inefficient at times, it can be modified to handle large text at once.

Methodology

This project was done in a total of four parts, each one addressing a certain problem for the IR system. Hence we start from tokenization and normalizing, to stop word removal and determining cut-off points, to preparing vector models from the term frequencies, and finally query optimization and retrieval. 






Part one:

Demonstrates a comprehensive text processing and analysis pipeline for Amharic language documents. It utilizes a variety of Python libraries to perform key tasks, including regular expression handling for Amharic text normalization, natural language processing for tokenization, data structure manipulation for index term removal based on word frequency analysis, and data visualization to provide insights into the distribution of word frequencies. The main steps involve extracting text from PDF files, tokenizing the text while normalizing Amharic punctuation and apostrophes, analyzing the word frequencies and removing high-frequency index terms, and finally writing the filtered tokens to a file. This processing pipeline can be valuable for a range of applications, such as information retrieval, text mining, and natural language processing, particularly for the Amharic language. 

Part two:

Reads a list of stop words from a file named "stopwords.txt" and converts it to a set for efficient lookup. It then defines a function that takes the tokenized text and the set of stop words, and returns a new list of words with the stop words removed. Additionally, the code reads the tokenized text from a file named "tokenized.txt", normalizes and tokenizes it, and then removes the stop words using the previously defined function. Finally, it writes the resulting list of words (the index) to a file named "index.txt", with each word separated by a space. This process of stop word removal and index generation is a common technique used in text processing and information retrieval applications to improve the effectiveness of search and analysis.


Part three:

Defines a function that takes a token, a list of tokens, a document ID, and a list of all document tokens, and creates a dictionary (vector) with the token as the key and the document ID and frequency as the value. This process is used to generate an inverted index and a list of document vectors. The inverted index maps each token to a dictionary of document IDs and their corresponding frequencies, while the list of document vectors contains the vectors for each document. Additionally, the code iterates through a directory of PDF files, extracts the text from each file, normalizes and tokenizes the text, removes stop words, and creates the inverted index and document vectors. Finally, the code saves the list of document vectors to a file using the pickle module, and later loads the data from the file, allowing for efficient storage and retrieval of the generated data structures.

Part four:

The core ideas behind this are the use of the term frequency-inverse document frequency (TF-IDF) and cosine similarity.

TF-IDF is a widely used technique in information retrieval to determine the relevance of a term to a document within a collection. The term frequency (TF) measures how important a word is within a particular document, while the inverse document frequency (IDF) measures how important the word is across all documents. By combining these two metrics, TF-IDF provides a way to score the importance of a term in a document, which is crucial for ranking the relevance of documents to a given query.
Cosine similarity is a metric used to measure the similarity between two non-zero vectors, such as the document vectors and the query vector. It calculates the cosine of the angle between the two vectors, which reflects the degree of similarity. Documents with higher cosine similarity to the query vector are considered more relevant and are ranked higher in the search results.

The key steps are:

-	Creating document vectors using the TF-IDF scores of the terms
-	Calculating the cosine similarity between the document vectors and the query vector
-	Ranking the documents based on their cosine similarity to the query

By employing these techniques, the system can efficiently retrieve the most relevant documents for a given query, which is a fundamental task in many applications, such as web search, document retrieval, and content recommendation.
                                                                                                                                                                                                                                                                                                                                                     
Why Python was substantial for this project

We chose Python due to its extensive libraries and the simplicity of its syntax. Python's robust ecosystem provides a wide range of tools that are particularly useful for Natural Language Processing (NLP) tasks, making it an ideal choice for our project.


Some important Libraries

The major libraries used for preprocessing the text include:
- nltk.tokenize: For tokenizing the text into words and sentences.
- re: For regular expression operations, which are essential for text cleaning.
- os: For handling file operations.
- collections: Specifically, `Counter` for counting word frequencies.
- pdfminer.high_level: For extracting text from PDF files.
- matplotlib.pyplot: For visualizing data.
- pickle: for serializing and deserializing Python objects, allowing for the storage and retrieval of data in a binary format.

Challenges faced
- Collecting a Corpus: Gathering a large and representative corpus of Amharic text was challenging due to the limitation of resources 
- Suffix Removal: Amharic words have complex suffixes. Finding a common list of suffixes for effective removal proved difficult. We 
- Stemming: Designing an efficient stemmer for Amharic was challenging due to the language's extensive dictionary and morphological complexity. Some algorithms processed words too slowly, at a rate of only one word per second. 
- Deciding cut-off points


Determining cut-off points

Deciding on cut-off words was tedious, as it required determining a threshold to remove the most common words while retaining significant terms. The corpus size had to be large so that the percentage cutoff would be substantial. Initially, we aimed for a cutoff greater than  20%, and for words that occurred less than once to be removed from the list.

Terms chosen as Indices 

Indexing terms are selected after stemming and stop word removal. These terms include the roots of tokens, excluding the most common words which finally results in a vector that creates a dictionary with the token as the key and the Document ID and frequency of the word as the value.

Conclusion  

The development of an Amharic information retrieval system has provided the research team with invaluable insights into the field of natural language processing, particularly the unique challenges presented by low-resource languages. By addressing the morphological complexities inherent in the Amharic language, which features a distinct script and intricate word formation processes, the team has gained a deeper understanding of the importance of tailoring language technology solutions to the specific needs and characteristics of individual languages. This process has involved adapting core information retrieval techniques, such as term frequency-inverse document frequency and cosine similarity scoring, to handle the peculiarities of Amharic effectively.
