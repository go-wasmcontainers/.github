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

> **Status: engine v0.22.0 is released and the playground (v0.3.0) is live.**
> The engine runs natively with a wazero executor: `wctr pull`, `images`, `run`
> (with `-p` published ports), `port`, `ps`, `logs`, `exec`, `rm`, `rmi`, `inspect`, `kill`, `start`, `stop`,
> `restart`, `diff`, `events`, `stats`, `volume`, `network`, `commit`, `tag`,
> `system df`, `system prune`, `completion` and, built in, `build` and `compose`.
> **`wctr` is a module of its own now, so install it and the daemon with two
> commands**:
> `go install github.com/go-wasmcontainers/engine/cmd/wctr@v0.1.0` and
> `go install github.com/go-wasmcontainers/engine/cmd/wctrd@v0.22.0`. The
> engine has networking (sockets, DNS by container name, networks with aliases and
> several networks per container, a class network through the relay) and the
> WASIX process subset behind `sh`, pipelines and shell-form `RUN`. The playground
> runs a dashboard and `wctr` in a tab with no server, with networking, Join
> class and wasi-nn, works offline, and keeps its containers across reloads. No
> attach, no `-p` in the browser yet (in progress), and no shell, stdin or `exec`
> in the playground. The shell's base image is public:
> `wctr pull ghcr.io/go-wasmcontainers/shell:0.1.0`. Everything else on the
> roadmap is **planned**, not shipped: a mini-Kubernetes.

## Repositories

| Repo | What it is |
|------|------------|
| [**engine**](https://github.com/go-wasmcontainers/engine) | the `wctrd` daemon and `wctr` command: a container engine for WASI (wasip1) workloads, pure Go (v0.22.0) |
| [**playground**](https://github.com/go-wasmcontainers/playground) | In-browser container playground: the dashboard and a `wctr` terminal running WASI containers, [live](https://go-wasmcontainers.github.io/playground/) (v0.3.0) |
| [**relay**](https://github.com/go-wasmcontainers/relay) | the classroom relay and firewall (`wctr-relay`), security groups modelled on OpenStack Neutron (v0.3.1; `--cors-origin`) |
| [**build**](https://github.com/go-wasmcontainers/build) | `wctr build`: images from a Containerfile, shell-form `RUN` and live step output (v0.4.0, built into `wctr`) |
| [**compose**](https://github.com/go-wasmcontainers/compose) | `wctr compose`: multi-container applications from Compose files in YAML, JSON or HCL2, with service-name networking (v0.3.2, built into `wctr`) |
| [**shell**](https://github.com/go-wasmcontainers/shell) | a POSIX shell for WASI containers and its base image with the coreutils (v0.1.0; the image `ghcr.io/go-wasmcontainers/shell:0.1.0` is public) |
| [**gpu**](https://github.com/go-wasmcontainers/gpu) | wasi-nn on the CPU and on WebGPU, wasi:webgpu compute and rendering to surfaces (v0.5.0) |
| [**dashboard**](https://github.com/go-wasmcontainers/dashboard) | a graphical dashboard for the engine (containers, images, volumes, networks, GPU surfaces and a `wctr` terminal), built with go-widgets, in the browser (v0.6.0); [live demo](https://go-wasmcontainers.github.io/dashboard/) |
| [**docs**](https://github.com/go-wasmcontainers/docs) | the documentation site (Hugo + Hextra), served at [/docs/](https://go-wasmcontainers.github.io/docs/) |
| [**go-wasmcontainers.github.io**](https://github.com/go-wasmcontainers/go-wasmcontainers.github.io) | the landing page (Hugo) |
| [**brand**](https://github.com/go-wasmcontainers/brand) | logo, icons and social images |

go-wasmcontainers belongs to the systems family of the go-* ecosystem, with
[go-filesystems](https://github.com/go-filesystems),
[go-volumes](https://github.com/go-volumes) and
[go-virtio](https://github.com/go-virtio).
