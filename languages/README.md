# Language toolchains

Official download and installation entry points for the languages represented in Genkidama and PositionTape.

This folder records the toolchain needed to compile or execute each language on Windows, macOS, and Linux. Some languages provide a single cross-platform installer; others depend on an operating-system compiler toolchain or package manager. A dash does not mean that the language cannot run on the platform—it means there is no first-party native installer that should be presented as equivalent.

## Inventory

The combined language matrix currently covers:

- Ada
- Assembly
- C
- C++
- C#
- COBOL
- Dart
- Delphi / Object Pascal
- Fortran
- Go
- Java
- JavaScript
- Julia
- Kotlin
- Lua
- MATLAB / GNU Octave
- Objective-C
- OCaml
- Perl
- PHP
- Prolog
- Python
- R
- Ruby
- Rust
- Scratch
- Standard ML
- Swift
- VB.NET

## Categories

- [Managed, scripting, and web languages](managed-scripting-web.md)
- [Native and systems languages](native-systems.md)
- [Scientific, functional, and educational languages](scientific-functional.md)

## Related but not a programming language

PositionTape also verifies SQLite behavior. Install it from the official [SQLite download page](https://www.sqlite.org/download.html):

- Windows: precompiled command-line tools are available on the download page.
- macOS: use the system package or a package manager when a newer CLI is required.
- Linux: use the distribution package or compile the official amalgamation/source archive.

## Selection rules

1. Prefer the language project's official download or installation page.
2. When the language does not publish native installers, link to its official compiler, package manager, or platform toolchain.
3. Use LTS releases for long-lived applications when the ecosystem defines an LTS channel.
4. Record the selected version in the consuming repository with the ecosystem's version file or lockfile where possible.
5. Verify installation by printing both the runtime and compiler/package-manager versions.
6. Do not install multiple competing toolchains globally unless a project requires them; use version managers or isolated environments where the ecosystem supports them.

## Platform note

The same source language does not imply identical platform capability. Objective-C, Delphi, Swift, Assembly, and some scientific toolchains have platform-specific libraries, build targets, or limitations. The links here install a valid language toolchain; they do not promise that every application or framework is portable across all three operating systems.
