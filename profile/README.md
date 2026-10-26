<p align="center"><img src="https://raw.githubusercontent.com/go-wasmcontainers/brand/main/social/go-wasmcontainers.png" alt="go-wasmcontainers" width="720"></p>

# go-wasmcontainers

🌐 **[Website](https://go-wasmcontainers.github.io)** · 📚 **[Documentation](https://go-wasmcontainers.github.io/docs/)**

**A container engine whose containers are WASI modules, compatible with the Docker Engine API, in pure Go (CGO=0), with an in-browser playground for cloud and container training labs.**

A container here is a `wasip1/wasm` module: the image is an OCI image with
`os=wasip1` and `arch=wasm`, and the engine runs it with
[wazero](https://wazero.io) instead of a Linux kernel. The engine is the
`wctrd` daemon and its command line is `wctr`; `wctrd` listens on
`/var/run/wctr.sock` (`WCTR_HOST` points `wctr` elsewhere) and speaks the Docker
Engine API, so existing API clients work too. The same engine runs inside a
browser tab, which makes a lab a web page rather than a virtual machine to
provision: **[try it in your browser](https://go-wasmcontainers.github.io/playground/)**.

> **Status: engine v0.9.0 is released and the playground is live.** The engine
> runs natively with a wazero executor (`wctr pull`, `images`, `run`, `ps`,
> `logs`, `rm`, `rmi`, `inspect`, `kill`, `start`, `stop`, `restart`, `diff`,
> `events`, `stats`, `volume`, `system df`, `system prune`, `version` and
> `completion` for bash, zsh, fish and PowerShell; install with
> `go install github.com/go-wasmcontainers/engine/cmd/wctr@v0.9.0`); v0.2.0
> added the browser executor, v0.3.0 the `cli/lineedit` line editor, v0.4.0
> made containers survive a `wctrd` restart and a page reload, v0.6.0 added
> events, v0.7.0 stats (CPU is not measured) and v0.8.0 named volumes, and v0.9.0 pulls `tar+zstd`
> layers and enables WebAssembly exception handling. The playground runs
> engine v0.9.0 in a tab with no server (`start`, `stop`, `restart`, `diff`,
> `stats`, `events`, volumes, `system df|prune`, and the C tools `lua`,
> `sqlite3` and `minigzip` built by go-pkgx for wasip1), works offline, and keeps its
> containers across reloads (playground v0.1.0). No networking, `exec`, attach,
> build, stdin or shell yet. Everything else on this
> page is **planned**, not shipped: container networking
> (the WasmEdge socket ABI), a shell and `exec` (a WASIX subset), building from a
> Dockerfile, Compose, and a mini-Kubernetes. Images are meant to be apt-like,
> built from [pkgx](https://github.com/go-pkgx) `wasip1` bottles (the
> `wasip1/wasm` target is itself being added to go-pkgx).

## Repositories

| Repo | What it is |
|------|------------|
| [**engine**](https://github.com/go-wasmcontainers/engine) | the `wctrd` daemon and `wctr` command: a container engine for WASI (wasip1) workloads, pure Go |
| [**playground**](https://github.com/go-wasmcontainers/playground) | In-browser container playground: a `wctr` terminal running WASI containers, [live](https://go-wasmcontainers.github.io/playground/) |
| [**dashboard**](https://github.com/go-wasmcontainers/dashboard) | a graphical dashboard for the engine (containers, images, volumes and a `wctr` terminal), built with go-widgets, in the browser; [live demo](https://go-wasmcontainers.github.io/dashboard/) |
| [**docs**](https://github.com/go-wasmcontainers/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-wasmcontainers.github.io/docs/) |
| [**go-wasmcontainers.github.io**](https://github.com/go-wasmcontainers/go-wasmcontainers.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-wasmcontainers/brand) | logo, icons and social images |

go-wasmcontainers belongs to the systems family of the go-* ecosystem, with
[go-filesystems](https://github.com/go-filesystems),
[go-volumes](https://github.com/go-volumes) and
[go-virtio](https://github.com/go-virtio).
