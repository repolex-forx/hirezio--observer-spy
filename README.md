# Repolex Knowledge Graph of hirezio/observer-spy

RDF knowledge graph data for [hirezio/observer-spy](https://github.com/hirezio/observer-spy), parsed by [repolex](https://repolex.ai).

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
rlex download hirezio/observer-spy
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4f7880e29298929846c3d73aa93d2f1af5bc4813
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 4f7880e29298929846c3d73aa93d2f1af5bc4813.nq.gz
│   └── repolex
│       └── 4f7880e29298929846c3d73aa93d2f1af5bc4813
│           └── chunk-001.nq.gz
├── blob
│   ├── 062e207fbed04607d534156fd356e1ba128858c2.nq.gz
│   ├── 0c0eaa51be7be9ee3b3f6f65aa7b7c9c06216755.nq.gz
│   ├── 288467ca985a461dd25e513df85e62930193f2ec.nq.gz
│   ├── 2b11978124a84c5539ace30381bac3cdc5b3dccc.nq.gz
│   ├── 2cc17ed85d7cac88f18cdb9f96872c90c860d8d5.nq.gz
│   ├── 2e1fa2d52e12f690ce40ac89f77912faba0f993d.nq.gz
│   ├── 2ec9500fb056f8ab70cb5e799eeb98196c9a63ea.nq.gz
│   ├── 2f28cead03959213f1f1abd3f8a3a76f280bc1a0.nq.gz
│   ├── 3081792b48e17e9acf0c3715b0172b3b7e158559.nq.gz
│   ├── 3091757a3b27c76b9b3c136092afbc21d7f3ef47.nq.gz
│   ├── 39836ba90471164ee1cf4daad0ff9f1014b177eb.nq.gz
│   ├── 3e05e098499b96eaf130a6a5e48e211736d1a3f4.nq.gz
│   ├── 4451331b2a15ce1f53147ee3586249ce41bd8a11.nq.gz
│   ├── 52dfa81aeb5080e9f4fc83afbb48f262c1529cb6.nq.gz
│   ├── 8039744e7e4f8a4c66165f0986fd7e7098be7302.nq.gz
│   ├── 822c99376cec47f96e70ded6cae3b31e54240d18.nq.gz
│   ├── 84dcb122af08159d4135ebbf530f11b3129b988b.nq.gz
│   ├── 8d44bedafd4446f1235de5f318704ecddef32551.nq.gz
│   ├── 92151799425320bde8f0f183bab485dce848c721.nq.gz
│   ├── a54445346d103e67e7088b2f1d07883f2c023e28.nq.gz
│   ├── ad3ff4a5a1dc8d38c4113aec6f9714659d9c4a8b.nq.gz
│   ├── b5c68e55be4d9bd48161c9a86ba89064299c0ec2.nq.gz
│   ├── b81acd0c5a588747a68664c4a877a643bf96cdb3.nq.gz
│   ├── b86bb6427440320ce5b4f2d8ddcb2d0f8ad7277d.nq.gz
│   ├── bbe8f850b26f652bd26dcd88b2c28e497c6a8a05.nq.gz
│   ├── c47302842eef3f7274bc3347b3eaf2c3d401fb84.nq.gz
│   ├── cad57977c10863ab0bb6660e96826808c050cef0.nq.gz
│   ├── cfafeeeebde91be0428d7a953bca4ab239876f4a.nq.gz
│   ├── d71a03b9f3e0fa8edcf35519c21add021db36103.nq.gz
│   ├── e6926ad2626f162efacd23753d9da1eed84398cd.nq.gz
│   ├── eb68026d48a0026002573cb7ee8695c3ab2a9305.nq.gz
│   └── eee11dd613de5539a99d58d78ea8c32d92c34e85.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── 4f7880e29298929846c3d73aa93d2f1af5bc4813.nq.gz
├── filetree
│   └── 4f7880e29298929846c3d73aa93d2f1af5bc4813.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 42 files
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

[hirezio/observer-spy](https://github.com/hirezio/observer-spy)

---
*Parsed on 2026-11-23 by [repolex](https://repolex.ai)*
