---
title: bite
date: 2024-04-20T12:18:10+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1712939706371-c17a36bd3935?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTM1ODY2MTF8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1712939706371-c17a36bd3935?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MTM1ODY2MTF8&ixlib=rb-4.0.3
---

# [WINSDK/bite](https://github.com/WINSDK/bite)

<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/logo_dark.png">
    <img height="150px" src="./assets/logo_light.png">
  </picture>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="./assets/logo_text_dark.svg">
    <img height="150px" src="./assets/logo_text_light.svg">
   </picture>
</h1>

<h4 align="center">Ever wanted to inspect every <i>bite</i> of your binary.</h4>

[![Test](https://github.com/WINSDK/bite/actions/workflows/ci.yml/badge.svg)](https://github.com/WINSDK/bite/actions/workflows/ci.yml)
![](https://img.shields.io/github/license/WINSDK/bite)

`BiTE` is a platform-agnostic executable analysis tool. It aims to offer an
environment for inspecting the content of binaries and it's debug info. While it is
still in early development, it supports various architectures.

## Showcase

Here is an example of the assembly listing viewing.

![Assembly listing](./assets/screenshot.png)

The ability to view a binary's disassembly and its associated source code.

![Source Code](./assets/split_source.png)

## Installation

Building from source.
```
cargo install --path .
```

## Features yet to be implemented

Whenever I have time this year I'll try implementing most of these. \
If you feel like it, submit a pull request and I'll have a look at it!

- [x] Port GUI to wgpu + winit
- [x] Header with buttons and options
- [x] Assembly listing exploration
- [x] Interactive terminal
- [ ] Assembly instruction byte patching
- [x] Hex binary viewer
- [ ] Debugging front-end's
  - [ ] [GDB](https://www.sourceware.org/gdb)
  - [ ] [LLDB](https://lldb.llvm.org)
  - [ ] [WinDbg](https://windbg.org)
- [x] X86-64 support
- [x] AArch64/Armv7 support
- [x] Riscv64gc/Riscv32gc support
- [x] MIPS-V support
- [x] Demangling support for most targets
  - [x] MSVC
  - [x] Itanium
  - [x] Rust
- [x] Decoding datastructures depending on each section
- [ ] Assembly listing lifting
  - [x] Resolving addresses
  - [x] Interpreting non-code data
  - [ ] Creating labels for relative jumps
