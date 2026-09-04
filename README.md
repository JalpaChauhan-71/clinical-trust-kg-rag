# clinical-trust-kg-rag
Research implementation of a Clinical Trust-aware Knowledge Graph and GraphRAG framework for trustworthy clinical information retrieval and question answering.
# Clinical Trust: Orchestrating Knowledge-Graph Augmented RAG for Verifiable Clinical Decision Support Systems

MSc Data Science thesis project — Liverpool John Moores University
Author: Jalpa Chauhan | Supervisor: Karthik O.S.

## Overview
This repository contains the full experimental pipeline for a Knowledge Graph-Augmented
Retrieval-Augmented Generation (KG-RAG) system for verifiable clinical decision support,
built around a novel claim-level verifiability metric, the Audit Trail Coverage Score (ATCS).

## Environment
- Google Colab (T4 GPU), Google Drive for persistence
- Neo4j AuraDB Free (credentials via Colab Secrets)
- Ollama serving `deepseek-r1` locally within the Colab session

## Notebooks (run in order)
| Notebook | Purpose |
|---|---|
| `00_setup.ipynb` | Environment setup, dependency installation, Neo4j/Ollama initialisation |
| `01_data_ingestion.ipynb` | Module 1 — PMC-Patients chunking, Bio-ClinicalBERT embedding, FAISS index |
| `02_kg_construction.ipynb` | Module 2 — scispaCy NER, UMLS entity linking, Neo4j graph construction |
| `03_hybrid_retrieval.ipynb` | Module 3 — dual-pathway vector + graph retrieval with RRF re-ranking |
| `04_multi_agent_orchestration.ipynb` | Module 4 — five-agent LangGraph pipeline |
| `05_audit_trail_generation.ipynb` | Module 5 — audit report and ATCS computation |
| `06_baselines.ipynb` | Standard RAG and LLM-only baseline systems |
| `07_evaluation_framework.ipynb` | Full evaluation: 5 queries × 3 runs × 3 systems |

## Results
- `evaluation_results_FINAL_COMBINED.csv` — raw per-query, per-run results underlying Table 8
- `ttest_results_20260829_174120.csv` — paired t-test output underlying Table 9

## Data and licensing note
The PMC-Patients corpus (Zeng, 2023) is public and open-access. The UMLS Metathesaurus
is **not** redistributed in this repository, as it requires an individual licence from the
US National Library of Medicine. Notebook `02_kg_construction.ipynb` contains the scripts
needed to rebuild the knowledge graph from your own licensed UMLS download.

## Citation
If referencing this work, please cite the accompanying MSc thesis (LJMU, 2026).
