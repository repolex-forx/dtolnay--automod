# Repolex Knowledge Graph of dtolnay/automod

RDF knowledge graph data for [dtolnay/automod](https://github.com/dtolnay/automod), parsed by [repolex](https://repolex.ai).

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
rlex download dtolnay/automod
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 74d02e471789b227b6c73e91a8a7d1c4e1911ab0
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 74d02e471789b227b6c73e91a8a7d1c4e1911ab0.nq.gz
│   └── repolex
│       └── 74d02e471789b227b6c73e91a8a7d1c4e1911ab0
│           └── chunk-001.nq.gz
├── blob
│   ├── 0191dd71ce98fce8a811288f6d765606f11018ab.nq.gz
│   ├── 1b5ec8b78e237b5c3b3d812a7c0a6589d0f7161d.nq.gz
│   ├── 31aa79387f27e730e33d871925e152e35e428031.nq.gz
│   ├── 381783f2dbf5d7280209e3a41f66f4188eda263a.nq.gz
│   ├── 41178d13e8953ca2d9c89ab636564d9d55480bae.nq.gz
│   ├── 6ee99de25f5a9e38b89890ca465651438486e469.nq.gz
│   ├── 750707701cdae985156601cc906195021ba6a6e5.nq.gz
│   ├── ab1c76ba65d24be9780ed5f62025724e97dd1a53.nq.gz
│   ├── ad70c6ca258c2ce798659503f0afa1eacbf9e334.nq.gz
│   ├── d5f4a4c3dbcfed63db81151b7df6d534a710dba6.nq.gz
│   └── e9e21997b1aca0707f8749ea13c09aec66c899d2.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 74d02e471789b227b6c73e91a8a7d1c4e1911ab0.nq.gz
├── filetree
│   └── 74d02e471789b227b6c73e91a8a7d1c4e1911ab0.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 21 files
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

[dtolnay/automod](https://github.com/dtolnay/automod)

---
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
