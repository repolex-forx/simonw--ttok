# Repolex Knowledge Graph of simonw/ttok

RDF knowledge graph data for [simonw/ttok](https://github.com/simonw/ttok), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/ttok
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── df24f500721ce5f2a75d9ecfbd4fdc58a896c1e0
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── df24f500721ce5f2a75d9ecfbd4fdc58a896c1e0
│           └── chunk-001.nq.gz
├── blob
│   ├── 056d8a564237056beae14a2fb344fded24243e6a.nq.gz
│   ├── 08fe582aae360ec83b5872ee1c3ecbe024d164ba.nq.gz
│   ├── 1d378850c585a2d2ca3143f952ef321875d34634.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 27c7caec3d92b2a4bf761570cccd5c7dea07eb8b.nq.gz
│   ├── 98dcca0c2836ae53d67260be8a5431b855e461bb.nq.gz
│   ├── a4ab4daf1d424ca02ea50b95adc964ba1f75d534.nq.gz
│   ├── b86af21e48ada1406a59de9e0a9261817dd11521.nq.gz
│   ├── d07256dab453e5590f34199dca2c55f533bc0d33.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── df24f500721ce5f2a75d9ecfbd4fdc58a896c1e0.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[simonw/ttok](https://github.com/simonw/ttok)

---
*Parsed on 2026-10-12 by [repolex](https://repolex.ai)*
