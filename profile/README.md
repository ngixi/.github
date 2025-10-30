# 🌈 NGIXI

> *A multimedia framework experiment that's equal parts ambition and chaos*

## What Is This? 🤔

NGIXI is a **heavily work-in-progress experimental/toy project** exploring cross-platform multimedia frameworks built on modern native technologies. Most of what's documented here represents architectural plans, ongoing research, and rapid prototyping—not finished features.

**Current Reality**: Hundreds of commits happening frequently. Everything is in flux. What worked yesterday might be completely restructured tomorrow. This is architecture-in-motion.

### The Vision (What We're Building Toward)

- 🚀 **WebAssembly** (Wasmtime) - Sandboxed execution for portable multimedia code
- 🎨 **WebGPU** (Google Dawn) - Cross-platform GPU graphics (Linux/macOS/Windows)
- 🎬 **FFmpeg** - Multimedia processing pipeline (planned)
- 🎵 **CPAL** - Cross-platform audio I/O (planned)
- ⚡ **Zig** - Systems programming language for the entire stack
- 🪟 **SDL3** - Cross-platform windowing (migrating to SDL3 components)

### Current Status

```
[████████████████████████] 100% Architectural Planning
[████████░░░░░░░░░░░░░░░░] 30% In Active Development
[████░░░░░░░░░░░░░░░░░░░░] 15% Actually Working
[░░░░░░░░░░░░░░░░░░░░░░░░] 0% Stable
[███████████████████████░] 95% Ideas & Experiments
```

**This is rapidly evolving research code.** Expect constant breaking changes, architectural rewrites, and commits by the hundred. Nothing is done. Everything is becoming.

---

## Repository Overview 📦

The NGIXI ecosystem is split across multiple repositories, each serving a specific purpose:

### Core Projects

#### 🎯 [ngixi](https://github.com/ngixi/ngixi)
**The main multimedia framework (architectural prototype)**

The heart of the project—or will be. Currently a testbed for WebAssembly integration patterns and multimedia framework architecture exploration.

- **Tech**: Zig, Wasmtime/Wasmer exploration
- **Target Platforms**: Linux, macOS, Windows
- **Status**: 🔥 Heavy architectural development
- **What Exists**:
  - Custom Wasmer Zig bindings (wasmer-zig-api module)
  - Grain language runtime experiments
  - Benchmark utilities
- **What's Planned**: Integration with Dawn, FFmpeg, CPAL, SDL3 windowing

#### 🌅 [ngixi-webgpu](https://github.com/ngixi/ngixi-webgpu)
**WebGPU bindings for Zig (cross-platform target)**

Zig wrapper around Google's Dawn WebGPU implementation. Currently Windows-focused while we expand to Linux/macOS.

- **Tech**: Zig, Dawn/WebGPU
- **Target Platforms**: Windows (✅ in progress), Linux (planned), macOS (planned)
- **Status**: 🔥 Active development
- **What Works**:
  - Windows Dawn DLL integration
  - Basic WebGPU Zig API
  - zigwin32 bindings for Windows-specific code
- **What's Coming**: 
  - Migrating to SDL3 components for cross-platform windowing
  - Linux Dawn builds
  - macOS Dawn builds (need Mac build server)

#### 🪟 [ngixi-zigwin32gen](https://github.com/ngixi/ngixi-zigwin32gen)
**Win32 API bindings generator (cross-compilation tool)**

Maintained fork of marlersoft's zigwin32gen. Generates Zig bindings for Win32 API to enable cross-compilation to Windows from any platform.

- **Tech**: Zig, win32json metadata
- **Purpose**: Generate Win32 bindings for cross-platform builds targeting Windows
- **Use Case**: Build Windows binaries from Linux/macOS without needing Windows SDK
- **Status**: Maintenance fork
- **Features**:
  - Automated binding generation from Microsoft metadata
  - Hungarian notation support
  - Union pointer handling
  - Comprehensive API coverage for cross-compilation scenarios

### Infrastructure

#### 🏗️ [ngixi-builds](https://github.com/ngixi/ngixi-builds)
**CI/CD and pre-built binaries (🔥 HOT IN FLIGHT 🔥)**

GitHub Actions build server for automated dependency compilation. **Very much under active construction.**

- **Purpose**: Build everything so you only need Zig installed locally
- **Status**: 🚧 Only Dawn Windows + Win32 bindings actually working right now
- **What's Done**:
  - ✅ `build-dawn-windows.yml` - Dawn WebGPU Windows builds
  - ✅ `build-zig-win32.yml` - Win32 bindings generation
- **What's In Progress/Planned**:
  - 🚧 Dawn Linux builds
  - 🚧 Dawn macOS builds (need Mac build server!)
  - 📋 Wasmtime builds (all platforms)
  - 📋 SDL3 builds (all platforms)
  - 📋 FreeType builds (planned)
  - 📋 FFmpeg builds (future)
- **Current Versions** (subject to constant change):
  - Dawn: `v20251026.130842`
  - Wasmtime: `v38.0.3` (planned)
  - SDL: `release-3.2.4` (planned)
  - FreeType: `VER-2-14-1` (planned)

---

## Why These Technologies? 🛠️

### WebAssembly (Wasmtime)
Provides a secure, portable execution environment for running multimedia processing code. Wasmtime offers near-native performance with sandboxing guarantees.

### WebGPU (Dawn)
Modern GPU API that works across platforms. Dawn is Google's production implementation, offering excellent performance and compatibility.

### Zig
A systems programming language that values explicitness and control. Perfect for interfacing with C libraries while maintaining safety where desired.

### FFmpeg
The de facto standard for multimedia processing. If it involves video or audio, FFmpeg can handle it.

---

## Getting Started 🚀

**⚠️ WARNING**: Most of this doesn't fully work yet. This is active R&D.

### What You Actually Need

- **Zig 0.15.1+** - That's it. The build server handles everything else.
- **Patience** - Things change rapidly
- **Flexibility** - Yesterday's API is tomorrow's rewrite
- **Coffee** - Non-negotiable ☕

### Platform Support Goals

- **Windows**: Primary development platform (most testing here)
- **Linux**: Planned (Dawn builds needed)
- **macOS**: Planned (need Mac build infrastructure)

Everything is designed to be cross-platform from day one, even if the builds don't all exist yet.

See individual repository READMEs for current build status and instructions (which may be outdated by the time you read them).

---

## Project Philosophy 🎯

NGIXI exists to:

1. **Learn** - Experiment with modern native technologies
2. **Explore** - Test the boundaries of WebAssembly in multimedia contexts
3. **Iterate Fast** - Hundreds of commits, constant evolution, rapid prototyping
4. **Share** - Document the journey (architectural plans, experiments, failures)
5. **Have Fun** - Build cool stuff without the pressure of production deadlines

This is **not**:
- Production-ready software
- A stable API
- Finished (or even close)
- Following a roadmap (we're making the map as we explore)
- Taking itself too seriously

### The Reality

Most repository documentation describes **architectural intent and plans**, not current functionality. We're building in public, iterating constantly, and documenting our thinking as we go. What exists today is a foundation and a lot of exploration.

---

## Contributing 🤝

Interested in joining the experiment? Contributions welcome!

- Found a bug? Open an issue
- Have an idea? Start a discussion
- Want to contribute? Submit a PR
- Just curious? Browse the code

**Bonus points for**:
- Improving documentation
- Adding examples
- Fixing build issues
- Bringing snacks 🍕

---

## License 📜

All NGIXI projects are MIT licensed unless otherwise specified. Life's too short for complicated licenses when you're building toys.

---

## Contact & Community 💬

- **Organization**: [@ngixi](https://github.com/ngixi)
- **Issues**: Use the relevant repository's issue tracker
- **Discussions**: Coming soon™

---

*"It's not a bug, it's an undocumented feature!"* - NGIXI development philosophy

**Remember**: This is an experiment in constant motion. Commits happen by the hundreds. Things will break. Entire architectures will change. Yesterday's code is tomorrow's history. That's part of the fun. 🎪

**Status**: Everything is becoming. Nothing is done. Welcome to the chaos. 🌀
