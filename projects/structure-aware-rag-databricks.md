# Structure-Aware RAG on Databricks

[Repository](https://github.com/soulipaco/structure-aware-rag-databricks) · [Retrieval design](https://github.com/soulipaco/structure-aware-rag-databricks/blob/main/docs/retrieval.md) · [Evaluation design](https://github.com/soulipaco/structure-aware-rag-databricks/blob/main/docs/evaluation.md)

## The problem

Fixed-window chunking can retrieve a paragraph that points somewhere else without retrieving the referenced evidence. It also tends to flatten headings, sections, tables, and provenance into text fragments that are difficult to reason about later.

## The idea

The project preserves source structure and explicit relationships. In its public eCFR demonstration, a vector result can expose an exact CFR citation; the relationship-aware path resolves that citation against the pinned corpus and adds the referenced section as its own citable evidence. Traversal stops after one exact hop.

## What was built

- extractors for eCFR XML, Markdown, JSONL, and delimited sources;
- structured authoring and chunking contracts;
- persisted relationship edges with provenance and resolution status;
- local and Databricks retrieval paths;
- governed Delta snapshot behavior and Vector Search integration;
- a public gold evaluation set with in-scope and out-of-scope questions;
- deterministic local demos and a live Databricks workflow.

## Evidence

The repository reports 200 tests and 83% coverage, enforced through CI on Python 3.10 and 3.12. On the small committed public evaluation set, the live relationship-aware configuration improved from 2/5 to 5/5 in-scope passes and from 7/10 to 10/10 citation/evidence recall; both configurations abstained on 2/2 out-of-scope questions.

The set is intentionally small. The result supports the repository's narrow claim about exact CFR reference expansion, not a general RAG accuracy claim.

![Exact one-hop retrieval trace](../assets/projects/rag-retrieval-trace.png)

## Best next clicks

- [Run the service-free local demo](https://github.com/soulipaco/structure-aware-rag-databricks#quick-start)
- [Public corpus selection](https://github.com/soulipaco/structure-aware-rag-databricks/blob/main/docs/public_corpus_selection.md)
- [Data contracts](https://github.com/soulipaco/structure-aware-rag-databricks/blob/main/docs/data-contracts.md)
- [Databricks demo runbook](https://github.com/soulipaco/structure-aware-rag-databricks/blob/main/docs/databricks_demo_runbook.md)

[Back to portfolio](../README.md)
