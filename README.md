Semantic Search Engine -project


Problem Statement
Conventional file systems rely on exact filename or keyword matches for retrieval, forcing users to recall precise names or locations. As personal and organizational storage grows, this becomes inefficient and error-prone, especially when file content is more memorable than its name. There is a need for a file retrieval system that understands the meaning behind a user's query rather than just matching text patterns.

Objectives

Design a simulated virtual file system with disk block management, disk scheduling (SSTF/C-SCAN), and ACL-based access control(access control list).
Build a DBMS layer to persist file metadata and vector embeddings for fast similarity search.
Integrate an NLP-based semantic search engine using Sentence-Transformer embeddings and cosine similarity to rank files by relevance to natural-language queries.
Combine the OS, DBMS, and NLP layers into a single end-to-end pipeline — from file upload/query input to ranked, permission-filtered results.
Demonstrate improved retrieval accuracy over traditional exact-match search through a working prototype.
Traditional file systems retrieve data only through exact filename or path matches, forcing users to remember precise naming conventions. The Semantic Search Engine removes that constraint by retrieving files based on meaning, allowing natural-language queries like "find my resume from last year" to surface the right file even if it's named doc_final_v2.docx.

The system integrates three core computer science domains into one working pipeline:

Operating Systems layer — a simulated virtual file system (C++) that manages disk blocks, implements disk scheduling algorithms (SSTF / C-SCAN) for efficient access ordering, and enforces Access Control List (ACL) permissions to govern who can read, write, or search which files.
DBMS layer — a relational/vector hybrid store (SQLite or PostgreSQL) that persists file metadata (name, size, timestamps, owner) alongside chunked text and vector embeddings, enabling fast similarity lookups without re-embedding on every query.
NLP/AI layer — a Sentence-Transformer model (all-MiniLM-L6-v2) converts both stored file content and incoming search queries into dense vector embeddings; cosine similarity ranks stored files by semantic closeness to the query.

How it works end-to-end: a user uploads a file or types a natural-language query → the search controller routes it to either the file-ingestion path or the query path → the semantic search engine embeds the text and compares it against stored vectors → access control filters results by permission → the virtual file system/disk scheduler retrieves the actual blocks from the simulated disk → ranked results are returned with a query/access log entry.

Why it matters: this mirrors real-world systems (like OS-level search indexing or enterprise document retrieval) while giving hands-on practice across OS, DBMS, and applied NLP — the exact intersection the PBL evaluation is meant to test.
rag
