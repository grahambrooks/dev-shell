# dev-shell a rust cli for interacting with ChatGPT

[![Project Status: Concept – Minimal or no implementation has been done yet, or the repository is only intended to be a limited example, demo, or proof-of-concept.](https://www.repostatus.org/badges/latest/concept.svg)](https://www.repostatus.org/#concept)

## Description

This is a ChatGPT CLI application written in Rust. The application allows users to interact with the ChatGPT API for AI text generation within their terminal.

As a cli the application can accept input from other tools.

```bash
git log HEAD~2 | dev-shell Summarize as a release note
```

### Project build and release status

![ci](https://github.com/grahambrooks/dev-shell/actions/workflows/ci.yaml/badge.svg) ![release](https://github.com/grahambrooks/dev-shell/actions/workflows/build.yaml/badge.svg) ![security audit](https://github.com/grahambrooks/dev-shell/actions/workflows/security-audit.yaml/badge.svg)



## Building

### Prerequisites

- Rust stable https://www.rust-lang.org/tools/install

Clone the repository and run the tests

```bash
cargo test
```

Build the application

```bash
cargo build --release
```

add the binary `target/release/dev-shell` to your path or copy to a directory that is already on your path.


## Use-cases

### Summarize for a git commit 

The following summarizes changes and commits those changes.

```bash
git diff | dev-shell Summarize changes as a git commit message. | git commit -a -F -
```

Which is a little long-winded, so you can create an alias in your shell.

```bash
alias dscommit="git diff | dev-shell Summarize changes as a git commit message. | git commit -a -F -"
```
## Repository maintenance

Currently, repository maintenance is manual and run semi regularly.

### Updating the rust toolchain

```bash
rustup update
```

Remember to update the rust toolchain used by bazel in the WORKSPACE.bazel file.

### Updating dependencies

The following command will update the Cargo.lock file with the latest versions of dependencies.

```bash
cargo update
```

### Updating/syncing bazel dependencies

This command then takes the updated dependencies and updates the equivalent bazel dependencies.

```bash
export CARGO_BAZEL_REPIN=true
bazel test //...
```
