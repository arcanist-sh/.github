## High-performance Haskell tooling

An ecosystem of tools for building, shipping, and running Haskell. Built in Rust.

### [hx](https://github.com/arcanist-sh/hx) — The Haskell package manager

A fast, opinionated, batteries-included toolchain for Haskell. Build, test, run, format, lint, and publish — all in one tool with managed toolchains.

- **5.6x faster** cold builds than Cabal
- Managed GHC & BHC toolchains
- Deterministic TOML lockfiles
- Steel (Scheme) plugin system

```
curl -fsSL https://arcanist.sh/install.sh | sh
hx new my-app && cd my-app && hx run
```

### [BHC](https://github.com/arcanist-sh/bhc) — Basel Haskell Compiler

A next-generation Haskell compiler with runtime profiles, tensor-native numerics, structured concurrency, and multi-target compilation. GHC-compatible and drop-in for most packages.

- **6 runtime profiles:** default, server, numeric, edge, realtime, embedded
- **Multiple targets:** native, WASI, WASM, CUDA, ROCm, RISC-V
- Strict-by-default numerics with guaranteed fusion and SIMD auto-vectorization
- Scoped structured concurrency with cooperative cancellation

```
hx build --compiler=bhc --profile=server
```

### More

| | |
|---|---|
| [arcanist.sh](https://arcanist.sh) | Landing page |
| [docs.arcanist.sh](https://docs.arcanist.sh) | Documentation |
| [purple-haze](https://github.com/arcanist-sh/purple-haze) | Zola theme with Catppuccin colors |
| [@raskell_io](https://x.com/raskell_io) | Twitter / X |
