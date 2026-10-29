# WDM-Ex.NO-6-Information-Retrieval-Using-Boolean-Model
**Information Retrieval Using Boolean Model in Python**<br>
**DATE:**<br>
**AIM:** To implement Information Retrieval Using Boolean Model in Python.<br>
**Description:**<br>
The Boolean model in Information Retrieval (IR) is a fundamental model used for searching and retrieving information from a collection of documents. It operates on the principles of set theory and logic, where documents are represented as sets of terms or words, and queries are expressed as Boolean expressions using logical operators such as AND, OR, and NOT.<br>
**Procedure:**
Initialize the BooleanRetrieval class: The BooleanRetrieval class is defined to manage the indexing and searching of documents.
Constructor and Index Initialization: The class constructor initializes an empty index to store the inverted index mapping terms to documents.<br>
**Indexing Documents:**<br>
a) The index_document method is responsible for indexing documents.<br>

b) Tokenize the text content of documents, converting them into lowercase terms.<br>

c) For each term in the document, it adds an entry in the index, associating the term with the document ID.<br>

**Fetch Web Page Text:**<br>
a) The fetch_webpage_text method uses the requests library to fetch content from a given URL.<br>

b) Extract text content from the fetched HTML using BeautifulSoup.<br>

c) The extracted text is returned for further processing.<br>

**Boolean Search:**<br>
a) The boolean_search method performs Boolean searches on the indexed documents.<br>

b) Tokenize the input query and iterates through its terms.<br>

c) For each term in the query, it retrieves documents containing that term and performs Boolean operations (AND, OR, NOT) based on the query's structure.<br>

**Program:**<br>
```import numpy as np
import pandas as pd
class BooleanRetrieval:
    def __init__(self):
        self.index = {}
        self.documents_matrix = None

def index_document(self, doc_id, text):
    terms = text.lower().split()
    print("Document -", doc_id, terms)

    for term in terms:
        if term not in self.index:
            self.index[term] = set()
        self.index[term].add(doc_id)

def create_documents_matrix(self, documents):
    terms = list(self.index.keys())
    num_docs = len(documents)
    num_terms = len(terms)

    self.documents_matrix = np.zeros((num_docs, num_terms), dtype=int)

    for i, (doc_id, text) in enumerate(documents.items()):
        doc_terms = text.lower().split()
        for term in doc_terms:
            if term in self.index:
                term_id = terms.index(term)
                self.documents_matrix[i, term_id] = 1

def print_documents_matrix_table(self):
    df = pd.DataFrame(self.documents_matrix, columns=self.index.keys())
    print(df)

def print_all_terms(self):
    print("All terms in the documents:")
    print(list(self.index.keys()))

def boolean_search(self, query):
    # TYPE YOUR CODE HERE
if name == "main": indexer = BooleanRetrieval()

documents = {
    1: "Python is a programming language",
    2: "Information retrieval deals with finding information",
    3: "Boolean models are used in information retrieval"
}

for doc_id, text in documents.items():
    indexer.index_document(doc_id, text)

indexer.create_documents_matrix(documents)
indexer.print_documents_matrix_table()
indexer.print_all_terms()

query = input("Enter your boolean query: ")
results = indexer.boolean_search(query)
if results:
    print(f"Results for '{query}': {results}")
else:
    print("No results found for the query.")
```
**Output:**<br>
**Result:**
