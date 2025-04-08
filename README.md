# 🔍 Course Retrieval System

### Master's Project – Team 18  
**Somesh Bachani • Shahana Yasmeen Shaik • Yijun Yan**  
Northeastern University | March 2025

---

## 📘 Overview

This project presents an **intelligent course retrieval engine** designed for the Computer Science curriculum at Northeastern University. The system supports nuanced, real-world queries from students seeking appropriate courses and ranks them based on textual relevance, curriculum structure, and metadata.

Using a hybrid of **Information Retrieval techniques** (e.g., BM25, TF-IDF, Boolean search, PageRank), the system matches user queries against a semantically enriched course catalog to surface the most appropriate and high-impact courses.

---

## 🎯 Objectives

- Enable students to retrieve **relevant CS courses** using natural queries
- Incorporate **metadata** like prerequisites, hours, corequisites, and course level
- Support **graduate-level filtering**, **lab detection**, and **skill-based queries**
- Evaluate effectiveness using **Precision@10** and **nDCG**

---

## 🛠️ Features

### 🔎 Retrieval Methods
- **BM25** relevance scoring (default)
- **TF-IDF + Cosine Similarity** as an alternative
- **Boolean Query Support**: `AND`, `OR`, `NOT`
- **Query Expansion** (e.g., `AI` → `artificial intelligence`)
- **Optional PageRank Boosting** using prerequisite graph

### 🧠 Intelligent Query Handling
- Handles ambiguous queries like:
  - "Which courses teach artificial intelligence?"
  - "Courses that have CS 5010 as a prerequisite"
  - "Beginner-friendly lab courses"

### 🧮 Evaluation
- Precision@10
- nDCG@10
- Manual query-relevance annotation for 15 curated queries

### 💻 Interfaces
- ✅ **Command Line Interface**
- ✅ **Tkinter GUI** with toggles for:
  - TF-IDF vs BM25
  - PageRank boosting

---

## 🧱 System Architecture

```text
      +-------------------+
      |   Course Catalog  |
      |  (XML Input File) |
      +-------------------+
               ↓
      +-------------------+
      |  Index Builder    | ← preprocesses text, parses metadata
      +-------------------+
               ↓
      +-----------------------------+
      |      Retrieval Engine       |
      |  - BM25 / TF-IDF            |
      |  - Boolean Ops              |
      |  - PageRank Re-ranking      |
      +-----------------------------+
               ↓
      +-----------------------------+
      |        Evaluation           |
      |  - P@10, nDCG@10            |
      |  - Query Relevance Map      |
      +-----------------------------+
               ↓
      +-----------------------------+
      |    CLI / Tkinter GUI        |
      +-----------------------------+
```

---

## 📊 Sample Queries

| Query | Sample Courses Retrieved |
|-------|--------------------------|
| _Which courses teach AI?_ | CS 4100, CS 5100, CS 5150, CS 5170 |
| _Courses with CS 5010 prereq_ | CS 5500, CS 7580 |
| _Beginner lab courses_ | CS 1101, CS 2501 |
| _Focus on programming design_ | CS 5010, CS 3500, CS 5500 |
| _Courses about cybersecurity_ | CS 4740, CS 5770 |

---

## 📁 File Structure

```
project/
│
├── cs_courses_enriched_expanded.xml  # Enriched course catalog
├── project.ipynb                     # Main Jupyter notebook
├── query_relevance_map.py           # Query & relevance annotations
├── README.md                         # This file
```

---

## 📈 Evaluation

- **10+ manually annotated queries**
- Combined scoring with **BM25 + PageRank**
- Precision@10: ~0.70 for most queries
- nDCG@10: >0.85 when relevance judgments are used
- Strong performance across beginner, advanced, and domain-specific filters

---

## 📌 Requirements

- Python 3.8+
- Required libraries:
  - `scikit-learn`
  - `nltk`
  - `tkinter`
  - `xml.etree`
  - `collections`, `math`, etc.

---

## 🚀 How to Run

### 📌 Command Line

```bash
python project.py
# Enter queries interactively
```

### 📌 GUI

```bash
# From inside notebook or .py file
run_tk_gui(inv_index, docs, meta, pagerank_scores)
```

- ✅ Toggle BM25 vs TF-IDF
- ✅ Enable/disable PageRank boost
- ✅ See top-10 results with full details

---

## 🧠 Credits

Built as part of a Master's-level Information Retrieval project for CS students at Northeastern University.
