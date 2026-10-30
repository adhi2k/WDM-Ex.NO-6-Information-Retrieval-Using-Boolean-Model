# WDM-Ex.NO-6-Information-Retrieval-Using-Boolean-Model
Information Retrieval Using Boolean Model in Python**<br>
### DATE: 30/10/2026
### AIM:
To implement Information Retrieval Using Boolean Model in Python.<br>
### Description:
The Boolean model in Information Retrieval (IR) is a fundamental model used for searching and retrieving information from a collection of documents. It operates on the principles of set theory and logic, where documents are represented as sets of terms or words, and queries are expressed as Boolean expressions using logical operators such as AND, OR, and NOT.<br>
### Procedure:
Initialize the BooleanRetrieval class: The BooleanRetrieval class is defined to manage the indexing and searching of documents.
Constructor and Index Initialization: The class constructor initializes an empty index to store the inverted index mapping terms to documents.<br>
### Indexing Documents:
a) The index_document method is responsible for indexing documents.<br>

b) Tokenize the text content of documents, converting them into lowercase terms.<br>

c) For each term in the document, it adds an entry in the index, associating the term with the document ID.<br>

### Fetch Web Page Text:
a) The fetch_webpage_text method uses the requests library to fetch content from a given URL.<br>

b) Extract text content from the fetched HTML using BeautifulSoup.<br>

c) The extracted text is returned for further processing.<br>

### Boolean Search:
a) The boolean_search method performs Boolean searches on the indexed documents.<br>

b) Tokenize the input query and iterates through its terms.<br>

c) For each term in the query, it retrieves documents containing that term and performs Boolean operations (AND, OR, NOT) based on the query's structure.<br>

### Program:
```
import re
import numpy as np
import pandas as pd

class BooleanRetrieval:

    def __init__(self):
        self.index = {}

    def index_document(self, doc_id, text):
        terms = re.findall(r'\b\w+\b', text.lower())

        for term in terms:
            self.index.setdefault(term, set()).add(doc_id)

    def boolean_search(self, query):
        query = query.lower()

        if " and " in query:
            terms = query.split(" and ")
            return set.intersection(
                *(self.index.get(t.strip(), set()) for t in terms)
            )

        elif " or " in query:
            terms = query.split(" or ")
            return set.union(
                *(self.index.get(t.strip(), set()) for t in terms)
            )

        elif query.startswith("not "):
            term = query[4:].strip()
            all_docs = {1, 2, 3}
            return all_docs - self.index.get(term, set())

        else:
            return self.index.get(query, set())


if __name__ == "__main__":

    print("INFORMATION RETRIEVAL USING BOOLEAN MODEL")
    print("-----------------------------------------")

    indexer = BooleanRetrieval()

    documents = {
        1: "Python is a programming language",
        2: "Information retrieval deals with finding information",
        3: "Boolean models are used in information retrieval"
    }

    for doc_id, text in documents.items():
        indexer.index_document(doc_id, text)
        print("Document:", doc_id, "-", text)

    print("\nInverted Index:")
    for term, doc_ids in indexer.index.items():
        print(term, ":", sorted(doc_ids))

    query = input("\nEnter your boolean query: ")

    results = indexer.boolean_search(query)

    if results:
        print("\nResults for", query, ":", sorted(results))
    else:
        print("\nNo results found.")

```
### Output:
<img width="928" height="683" alt="image" src="https://github.com/user-attachments/assets/ee52a4b3-1c0e-4f15-97eb-438bc66ea80f" />

### Result:
Thus, Information Retrieval using the Boolean Model was successfully implemented in Python. The program creates an inverted index and retrieves relevant documents using AND, OR, and NOT logical operators.

