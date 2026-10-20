## Haskell tooling for the age of AI-authored code

When generating code is cheap, correctness has to be checkable. arcanist.sh builds the
Haskell tools that make it so, in Rust and in public: a fast toolchain, a compiler built
to check everything it can, and a registry where verification accumulates.

### [hx](https://github.com/arcanist-sh/hx) · the whole Haskell toolchain in one fast binary

Installs GHC and Cabal, builds, tests, formats and lints, pins every dependency by hash,
and publishes packages. It drives GHC and Cabal rather than replacing them, and gives AI
agents the same commands over MCP.

```bash
curl -fsSL https://arcanist.sh/hx/install.sh | sh
hx init my-app && cd my-app && hx run
```

- 5.6× faster cold builds than cabal, [measured](https://arcanist.sh/hx/benchmarks/)
- Lockfiles that pin sources by SHA-256; `--locked` for CI
- Workspaces, `hx install`, coverage, profiling, publishing, managed GHC and bhc toolchains

### [bhc](https://github.com/arcanist-sh/bhc) · the Basel Haskell Compiler

A clean-slate compiler for the Haskell you already write, in beta. Native code through
LLVM, WebAssembly for WASI, and a runtime profile chosen per build. Type classes are
elaborated into explicit dictionaries, so every definition's meaning is spelled out.

- All 221 modules of Pandoc type-check and compile; its Markdown reader and HTML writer run
- 236 / 243 WebAssembly fixtures byte-identical to native
- [Where bhc stands](https://arcanist.sh/bhc/status/), measured, with the caveats

### [registry](https://github.com/arcanist-sh/registry) · packages, signed and checked

A Haskell package repository plain cabal reads next to Hackage, signed with
hackage-security. hx publishes to it, and the
[bhc verifier](https://github.com/arcanist-sh/bhc-verifier) builds every new version and
records the result beside the package: the first piece of a commons where a check that
ran once is recorded instead of repeated.

### Where this goes

A checkable toolchain, meaning made explicit, verification that accumulates, and then
[the commons](https://arcanist.sh/commons/): definitions named by what they mean and the
contract they run under, each carrying a record of what was checked. The reasoning is in
the [manifesto](https://arcanist.sh/manifesto/).

| | |
|---|---|
| [arcanist.sh](https://arcanist.sh) | Website and blog |
| [docs.arcanist.sh](https://docs.arcanist.sh) | Documentation for hx and bhc |
| [registry.arcanist.sh](https://registry.arcanist.sh) | Browse the package registry |
| [vellum](https://github.com/arcanist-sh/vellum) · [brutalist-blueprint](https://github.com/arcanist-sh/brutalist-blueprint) | The Zola themes behind arcanist.sh and the original bhc site |
| [@raskell_io](https://x.com/raskell_io) | X |
