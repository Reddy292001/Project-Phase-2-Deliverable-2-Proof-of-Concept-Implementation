# Search Engine Optimization: Phase 2 Proof of Concept

## Project Overview
This project is a Phase 2 proof-of-concept implementation for a simplified search engine built in Python. The goal of this phase is to partially implement the data structures proposed in Phase 1 and demonstrate the core functionality of the application.

The system focuses on four main capabilities:

1. storing documents efficiently  
2. performing keyword-based search  
3. ranking search results  
4. suggesting autocomplete terms based on a prefix  

This implementation is not meant to be a full production search engine. Instead, it is a modular prototype that shows how the selected data structures work together to support the application's main requirements.

## Data Structures Implemented
The proof of concept uses the following data structures:

### 1. Document Store
A Python dictionary is used to store documents by document ID.

- **Purpose:** direct document access
- **Why it was chosen:** dictionaries provide fast average-case lookup, insertion, and deletion

### 2. Inverted Index
The inverted index maps each term to the documents in which it appears, along with term frequency.

- **Purpose:** efficient keyword search without scanning every document
- **Why it was chosen:** it is the standard structure used in text retrieval systems

### 3. Trie
A trie is used for prefix-based suggestions.

- **Purpose:** autocomplete
- **Why it was chosen:** it allows fast prefix traversal and word collection

### 4. Heap-Based Ranking
Search results are ranked using Python's `heapq.nlargest()` function.

- **Purpose:** return the top-k results by score
- **Why it was chosen:** it avoids sorting the full result set when only a few top results are needed

## Files Included
- `SEO_Phase2.ipynb` – main notebook with implementation, discussion, demo, and tests
- `search_engine_poc.py` – Python version of the proof-of-concept implementation
- `SEO_Phase2_Report_Updated_v2.docx` – written report for Deliverable 2
- `README.md` – project overview and usage instructions

## Main Features
The current proof of concept supports:

- adding a document
- removing a document
- keyword search
- top-k ranked results
- autocomplete suggestions
- simple tokenization and term-frequency scoring
- basic tests for correctness and edge cases

## How the System Works
When a document is added:

1. the document is stored in the document dictionary  
2. the text is tokenized into lowercase words  
3. the inverted index stores term frequencies by document  
4. each token is inserted into the trie for prefix suggestions  

When a query is searched:

1. the query is tokenized  
2. matching documents are found through the inverted index  
3. scores are calculated using summed term frequencies  
4. the top-k documents are returned using heap-based ranking  

When a prefix is entered:

1. the trie is traversed character by character  
2. all matching completions under that prefix are collected  
3. the first few suggestions are returned  

## Demonstration and Testing
The notebook includes both demonstration examples and grouped tests.

### Demo operations
The demo shows:
- adding sample documents
- checking vocabulary and document counts
- searching for terms like `python trie`
- removing a document and confirming the results change
- generating autocomplete suggestions such as `py`

### Test coverage
The notebook includes tests for:
- trie insertion and prefix lookup
- inverted index add/remove behavior
- search engine integration
- edge cases such as missing terms, empty results, and invalid top-k values

## How to Run
### Option 1: Google Colab
1. Open the notebook `SEO_Phase2.ipynb` in Google Colab.
2. Run the notebook cells from top to bottom.
3. Review the outputs from the demo and test sections.

### Option 2: Local Jupyter Notebook
1. Install Python 3.10+.
2. Install Jupyter if needed:
   ```bash
   pip install notebook
   ```
3. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
4. Open `SEO_Phase2.ipynb` and run all cells.

### Option 3: Run Python Script
If using the standalone Python script:
```bash
python search_engine_poc.py
```

## Example Usage
```python
engine = SearchEngine()

engine.add_document(1, "Python provides useful tools for text processing.")
engine.add_document(2, "Trie structures are useful for autocomplete.")
engine.add_document(3, "Inverted indexes improve search efficiency.")

print(engine.search("python search", k=2))
print(engine.suggest("tr"))
```

## Design Choices
A few design choices were made to keep the implementation simple and readable:

- duplicate document IDs are rejected instead of overwritten
- ranking uses raw term frequency instead of TF-IDF or BM25
- tokenization is basic and does not include stemming or stop-word removal
- the trie is updated using the current indexed vocabulary
- if `k <= 0`, the search method returns an empty list

These decisions helped keep the code manageable for a proof-of-concept stage.

## Challenges Faced
Some of the main implementation challenges were:

- keeping the trie and inverted index consistent after document deletion
- avoiding overly complex ranking while still demonstrating top-k retrieval
- keeping the code modular enough for future expansion
- making the notebook readable by breaking large blocks into smaller sections

These were addressed by using separate classes, helper methods, and grouped tests.

## Limitations
This is still an early-stage prototype. The current version has several limitations:

- no phrase searching
- no stemming or stop-word removal
- no TF-IDF or BM25 ranking
- no file-based document ingestion
- no web interface
- limited scalability for very large datasets

## Next Steps
The next development steps would be:

- improve tokenization with stop-word removal and stemming
- add better ranking such as TF-IDF or BM25
- support phrase queries and Boolean queries
- improve trie memory usage
- add persistent storage for the index
- build a simple user interface for searching

## GitHub Link
Add your repository link here before submission:

`[Insert GitHub repository link here]`

## Author
Sai Venkata Bharath Reddy Singareddy

## Course
Algorithms and Data Structures (MSCS-532-B01)
