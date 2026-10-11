# Repolex Knowledge Graph of agronholm/ep2018demo

RDF knowledge graph data for [agronholm/ep2018demo](https://github.com/agronholm/ep2018demo), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download agronholm/ep2018demo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4dbda56eabb4160e98ae92b306e2e090372368d4
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4dbda56eabb4160e98ae92b306e2e090372368d4
│           └── chunk-001.nq.gz
├── blob
│   ├── 0d01b7bcce62556e99793af029d8d6b40c51f7e1.nq.gz
│   ├── 20bbb7da29a1ae0be0d9f35b206f5ba88bec2bba.nq.gz
│   ├── 6cab2ee46ed3b7e64f754de23276cbbc04ebf139.nq.gz
│   ├── cd5cb71f7d5d52131ce52f2e79b8401b06af295d.nq.gz
│   ├── d0f6e04134a07d76e55521652a9aa0759db3fa5e.nq.gz
│   └── dbf2760216b5645ec57afeae18cc0a75e186ebfb.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4dbda56eabb4160e98ae92b306e2e090372368d4.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 12 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[agronholm/ep2018demo](https://github.com/agronholm/ep2018demo)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
