# Managed, scripting, and web languages

## C# and VB.NET

Both languages use the .NET SDK.

| Platform | Official installation |
| --- | --- |
| Windows | [.NET on Windows](https://learn.microsoft.com/en-us/dotnet/core/install/windows) |
| macOS | [.NET on macOS](https://learn.microsoft.com/en-us/dotnet/core/install/macos) |
| Linux | [.NET on Linux](https://learn.microsoft.com/en-us/dotnet/core/install/linux) |

Verify:

```bash
dotnet --info
```

## JavaScript

Use the current Node.js LTS release for command-line, server-side, build, and test tooling.

| Platform | Official installation |
| --- | --- |
| Windows | [Node.js downloads](https://nodejs.org/en/download) |
| macOS | [Node.js downloads](https://nodejs.org/en/download) |
| Linux | [Node.js downloads](https://nodejs.org/en/download) |

Verify:

```bash
node --version
npm --version
```

TypeScript is the preferred companion for React and Angular applications in this handbook. Install it per project rather than globally:

```bash
npm install --save-dev typescript
```

Official documentation: [TypeScript download and installation](https://www.typescriptlang.org/download/).

## Dart

| Platform | Official installation |
| --- | --- |
| Windows | [Get the Dart SDK](https://dart.dev/get-dart) |
| macOS | [Get the Dart SDK](https://dart.dev/get-dart) |
| Linux | [Get the Dart SDK](https://dart.dev/get-dart) |

Flutter includes the Dart SDK; do not install a second standalone SDK unless a non-Flutter project requires it.

Verify:

```bash
dart --version
```

## Java

Use a current JDK, not only a JRE. For reproducible builds, select one vendor and major version per repository.

| Platform | Official installation |
| --- | --- |
| Windows | [Oracle JDK downloads](https://www.oracle.com/java/technologies/downloads/) |
| macOS | [Oracle JDK downloads](https://www.oracle.com/java/technologies/downloads/) |
| Linux | [Oracle JDK downloads](https://www.oracle.com/java/technologies/downloads/) |

OpenJDK alternative: [Eclipse Temurin releases](https://adoptium.net/temurin/releases/).

Verify:

```bash
java --version
javac --version
```

## Kotlin

The Kotlin command-line compiler requires a JDK.

| Platform | Official installation |
| --- | --- |
| Windows | [Kotlin command-line compiler](https://kotlinlang.org/docs/command-line.html) |
| macOS | [Kotlin command-line compiler](https://kotlinlang.org/docs/command-line.html) |
| Linux | [Kotlin command-line compiler](https://kotlinlang.org/docs/command-line.html) |

For Gradle-based projects, use the Gradle wrapper committed to the repository instead of installing a global Gradle version.

Verify:

```bash
kotlinc -version
```

## Python

| Platform | Official installation |
| --- | --- |
| Windows | [Python releases for Windows](https://www.python.org/downloads/windows/) |
| macOS | [Python releases for macOS](https://www.python.org/downloads/macos/) |
| Linux | [Using Python on Unix platforms](https://docs.python.org/3/using/unix.html) |

For application projects, the preferred environment and dependency tool in this handbook is [uv](https://docs.astral.sh/uv/).

Verify:

```bash
python --version
python -m pip --version
```

On systems where `python` points elsewhere, use `python3`.

## PHP

| Platform | Official installation |
| --- | --- |
| Windows | [PHP for Windows](https://www.php.net/downloads.php?os=windows) |
| macOS | [Installing PHP on macOS](https://www.php.net/manual/en/install.macosx.php) |
| Linux | [Installing PHP on Unix systems](https://www.php.net/manual/en/install.unix.php) |

Verify:

```bash
php --version
```

## Ruby

| Platform | Official installation |
| --- | --- |
| Windows | [RubyInstaller for Windows](https://rubyinstaller.org/downloads/) |
| macOS | [Installing Ruby](https://www.ruby-lang.org/en/documentation/installation/) |
| Linux | [Installing Ruby](https://www.ruby-lang.org/en/documentation/installation/) |

Use a version manager when maintaining applications on different Ruby versions.

Verify:

```bash
ruby --version
gem --version
```

## Perl

The official Perl site directs each operating system to maintained distributions or package sources.

| Platform | Official installation |
| --- | --- |
| Windows | [Get Perl](https://www.perl.org/get.html) |
| macOS | [Get Perl](https://www.perl.org/get.html) |
| Linux | [Get Perl](https://www.perl.org/get.html) |

Verify:

```bash
perl -v
```

## Lua

Lua publishes portable source releases rather than first-party installers for every operating system.

| Platform | Official installation |
| --- | --- |
| Windows | [Lua downloads and source](https://www.lua.org/download.html) |
| macOS | [Lua downloads and source](https://www.lua.org/download.html) |
| Linux | [Lua downloads and source](https://www.lua.org/download.html) |

Use a trusted operating-system package when a precompiled interpreter is preferred.

Verify:

```bash
lua -v
```
