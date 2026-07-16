# Native and systems languages

## Ada

The preferred community entry point is Alire, which installs and manages Ada toolchains and dependencies.

| Platform | Official installation |
| --- | --- |
| Windows | [Alire documentation and installation](https://alire.ada.dev/docs/) |
| macOS | [Alire documentation and installation](https://alire.ada.dev/docs/) |
| Linux | [Alire documentation and installation](https://alire.ada.dev/docs/) |

Alternative compiler source: [GNU Ada / GNAT](https://www.gnu.org/software/gnat/).

Verify:

```bash
alr version
gnat --version
```

## Assembly

Assembly requires an assembler for the selected processor architecture and object format.

| Platform | Official installation |
| --- | --- |
| Windows | [NASM](https://www.nasm.us/) or [Visual Studio downloads](https://visualstudio.microsoft.com/downloads/) for Microsoft toolchains |
| macOS | [Xcode resources](https://developer.apple.com/xcode/resources/) for Apple Clang and the platform assembler |
| Linux | [GNU Binutils](https://www.gnu.org/software/binutils/) or [NASM](https://www.nasm.us/) |

Verify the chosen toolchain, for example:

```bash
nasm -v
as --version
```

## C

| Platform | Official installation |
| --- | --- |
| Windows | [Visual Studio and Build Tools](https://visualstudio.microsoft.com/downloads/) |
| macOS | [Xcode resources](https://developer.apple.com/xcode/resources/) |
| Linux | [GCC binaries and packages](https://gcc.gnu.org/install/binaries.html) or [LLVM packages](https://apt.llvm.org/) |

Verify:

```bash
cc --version
```

On Windows Developer Command Prompt:

```powershell
cl
```

## C++

| Platform | Official installation |
| --- | --- |
| Windows | [Visual Studio and Build Tools](https://visualstudio.microsoft.com/downloads/) |
| macOS | [Xcode resources](https://developer.apple.com/xcode/resources/) |
| Linux | [GCC binaries and packages](https://gcc.gnu.org/install/binaries.html) or [LLVM packages](https://apt.llvm.org/) |

Common build tools:

- [CMake downloads](https://cmake.org/download/)
- [Ninja releases](https://github.com/ninja-build/ninja/releases)

Verify:

```bash
c++ --version
cmake --version
```

## COBOL

GnuCOBOL is the preferred open-source toolchain for the PositionTape implementation.

| Platform | Official installation |
| --- | --- |
| Windows | [GnuCOBOL project](https://www.gnu.org/software/gnucobol/) |
| macOS | [GnuCOBOL project](https://www.gnu.org/software/gnucobol/) |
| Linux | [GnuCOBOL project](https://www.gnu.org/software/gnucobol/) |

The project publishes source releases; operating-system packages or maintained project distributions may provide binaries.

Verify:

```bash
cobc --version
```

## Delphi / Object Pascal

Delphi's IDE and compiler are Windows-hosted. Free Pascal provides the cross-platform Object Pascal toolchain.

| Platform | Official installation |
| --- | --- |
| Windows | [Embarcadero Delphi downloads](https://www.embarcadero.com/products/delphi/starter) or [Free Pascal downloads](https://www.freepascal.org/download.html) |
| macOS | [Free Pascal downloads](https://www.freepascal.org/download.html) |
| Linux | [Free Pascal downloads](https://www.freepascal.org/download.html) |

A Delphi Windows installation can target additional platforms depending on edition and installed platform support, but it is not a native macOS or Linux IDE installation.

Verify Free Pascal:

```bash
fpc -iV
```

## Fortran

The Fortran community maintains platform-specific GNU Fortran setup instructions.

| Platform | Official installation |
| --- | --- |
| Windows | [Install GNU Fortran](https://fortran-lang.org/learn/os_setup/install_gfortran/) |
| macOS | [Install GNU Fortran](https://fortran-lang.org/learn/os_setup/install_gfortran/) |
| Linux | [Install GNU Fortran](https://fortran-lang.org/learn/os_setup/install_gfortran/) |

Alternative commercial/HPC route: [Intel oneAPI HPC Toolkit](https://www.intel.com/content/www/us/en/developer/tools/oneapi/hpc-toolkit-download.html).

Verify:

```bash
gfortran --version
```

## Go

| Platform | Official installation |
| --- | --- |
| Windows | [Go downloads](https://go.dev/dl/) |
| macOS | [Go downloads](https://go.dev/dl/) |
| Linux | [Go downloads](https://go.dev/dl/) |

Verify:

```bash
go version
```

## Objective-C

Objective-C is primarily supported by Apple's platform toolchain. GNUstep enables portable Objective-C development but does not reproduce Apple's frameworks.

| Platform | Official installation |
| --- | --- |
| Windows | [GNUstep project](https://gnustep.github.io/) |
| macOS | [Xcode resources](https://developer.apple.com/xcode/resources/) |
| Linux | [GNUstep project](https://gnustep.github.io/) and [LLVM](https://releases.llvm.org/) |

The PositionTape Objective-C implementation is source-level on Windows because a complete native Apple-compatible environment is not available there.

Verify on macOS/Linux:

```bash
clang --version
```

## Rust

The official installer is `rustup`, which installs Rust, Cargo, and toolchain components.

| Platform | Official installation |
| --- | --- |
| Windows | [Install Rust](https://www.rust-lang.org/tools/install) |
| macOS | [Install Rust](https://www.rust-lang.org/tools/install) |
| Linux | [Install Rust](https://www.rust-lang.org/tools/install) |

Windows also requires a supported linker toolchain, normally the Visual Studio C++ Build Tools for the MSVC target.

Verify:

```bash
rustc --version
cargo --version
```

## Swift

| Platform | Official installation |
| --- | --- |
| Windows | [Install Swift](https://www.swift.org/install/) |
| macOS | [Install Swift](https://www.swift.org/install/) |
| Linux | [Install Swift](https://www.swift.org/install/) |

On macOS, Xcode supplies the Apple platform SDKs in addition to the Swift compiler.

Verify:

```bash
swift --version
```
