---
title: poop
date: 2023-06-19T12:16:47+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1685999298638-553de9deb9fc?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODcxNDgxMjJ8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1685999298638-553de9deb9fc?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODcxNDgxMjJ8&ixlib=rb-4.0.3
---

# [andrewrk/poop](https://github.com/andrewrk/poop)

# Performance Optimizer Observation Platform

Stop flushing your performance down the drain.

## Overview

This command line tool uses Linux's `perf_event_open` functionality to compare the performance of multiple commands
with a colorful terminal user interface.

![image](https://github.com/andrewrk/poop/assets/106511/c4f4d4f1-c25e-473c-bdd2-95a0692d280f)

## Usage

```
Usage: poop [options] <command1> ... <commandN>

Compares the performance of the provided commands.

Options:
 --duration <ms>    (default: 5000) how long to repeatedly sample each command

```

## Building from Source

Tested with [Zig](https://ziglang.org/) `0.11.0-dev.3625+129afba46`.

```
zig build
```

## Comparison with Hyperfine

Poop (so far) is brand new, whereas
[Hyperfine](https://github.com/sharkdp/hyperfine) is a mature project with more
configuration options and generally more polish.

However, poop does report peak memory usage as well as 5 other hardware
counters, which I personally find useful when doing performance testing. Hey,
maybe it will inspire the Hyperfine maintainers to add the extra data points!

Poop does not run the commands in a shell. This has the upside of not
including shell spawning noise in the data points collected, and the downside
of not supporting strings inside the commands.

Poop treats the first command as a reference and the subsequent ones
relative to it, giving the user the choice of the meaning of the coloring of
the deltas. Hyperfine always prints the wall-clock-fastest command first.

Poop (for now) has clunky handling of digits of precision and alignment in the
display. See [#4](https://github.com/andrewrk/poop/issues/4) and
[#10](https://github.com/andrewrk/poop/issues/10).

Poop is also Linux-only.
