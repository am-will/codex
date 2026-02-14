# Build Instructions

## 1. System Dependencies (Ubuntu/Debian)

```bash
sudo apt-get update && sudo apt-get install -y \
  build-essential \
  pkg-config \
  libssl-dev \
  libcap-dev \
  clang \
  cmake \
  git \
  curl
```

## 2. Install Rust

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source "$HOME/.cargo/env"
```

The repo pins Rust **1.93.0 stable** via `rust-toolchain.toml` — rustup will handle that automatically on first build.

## 3. Install Helper Tools

```bash
cargo install just
cargo install cargo-nextest  # optional, faster test runner
```

## 4. Clone & Build

```bash
git clone https://github.com/am-will/codex.git
cd codex/codex-rs
cargo build
```

## 5. Set Up Alias

Add this to your `~/.bashrc` (or `~/.zshrc`):

```bash
alias codex='cargo run --manifest-path ~/codex/codex-rs/Cargo.toml --bin codex-tui --'
```

Then reload your shell:

```bash
source ~/.bashrc
```

Now you can run it from anywhere:

```bash
codex
```

## 6. Configure (optional)

Create `~/.codex/config.toml`:

```toml

[agents]
max_threads = 12
model = "gpt-5.3-codex-spark"
reasoning = "xhigh"
```

The `[agents]` section lets you override subagent model, reasoning effort, and max concurrent threads. These are optional — sensible defaults are built in.
