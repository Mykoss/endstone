# Endstone

**High-performance Minecraft Bedrock server software, extensible with Python and C++ plugins.**

- GitHub: https://github.com/EndstoneMC/endstone
- Docs: https://endstone.dev
- License: Apache-2.0

## About

Endstone is a custom Bedrock Dedicated Server that exposes a rich plugin API (60+ events, commands, forms, scoreboards, inventories, permissions). Plugins can be written in Python or C++.

## Stack

- **Language:** Python 3.10+ (plugin API), C++ (core server)
- **Build system:** CMake + Conan (for building from source)
- **Package:** `pip install endstone` (pre-built binaries via PyPI)

## Running on Replit

> **Note:** Replit does not expose UDP ports, so game clients cannot connect to a Bedrock server hosted here. However, Replit is suitable for plugin development, API exploration, and studying the codebase.

### Easiest setup — install pre-built package

```bash
pip install endstone
endstone
```

### Build from source

Requires CMake, a C++17 compiler, and Conan 2. The `pyproject.toml` uses `conan-py-build` as its build backend.

```bash
pip install conan-py-build setuptools-scm
pip install .
```

### Docker

```bash
docker pull endstone/endstone
docker run --rm -it -p 19132:19132/udp endstone/endstone
```

## Key directories

| Path | Contents |
|------|----------|
| `endstone/` | Python plugin API package |
| `src/endstone/` | Python source (CLI, runtime) |
| `src/bedrock/` | Bedrock server integration |
| `include/` | C++ headers |
| `tests/` | Test suite |
| `docs/` | MkDocs documentation source |
| `recipes/` | Conan recipes |

## User preferences

<!-- Add your preferences here -->
