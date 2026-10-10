# Repolex Knowledge Graph of psf/black-pre-commit-mirror

RDF knowledge graph data for [psf/black-pre-commit-mirror](https://github.com/psf/black-pre-commit-mirror), parsed by [repolex](https://repolex.ai).

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
rlex download psf/black-pre-commit-mirror
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a5439e9af2ff9371297bb1a76a01b8ad17989b88
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── a5439e9af2ff9371297bb1a76a01b8ad17989b88
│           └── chunk-001.nq.gz
├── blob
│   ├── 137957045a6c938eec1408ca9af8ba47d59f4caa.nq.gz
│   ├── 33dcc4d9c10e55a28eae19590785466fee9892b3.nq.gz
│   ├── 42751296bebbec155cd0a87720ec492ad92880c9.nq.gz
│   ├── 850bcf4c38f19a5c7a4f6c03ae7d7a11010e7a57.nq.gz
│   └── 97f1e74dff51de79d11b43b88fae74685c6ef4ea.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── a5439e9af2ff9371297bb1a76a01b8ad17989b88.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 13 files
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

[psf/black-pre-commit-mirror](https://github.com/psf/black-pre-commit-mirror)

---
*Parsed on 2026-10-10 by [repolex](https://repolex.ai)*
