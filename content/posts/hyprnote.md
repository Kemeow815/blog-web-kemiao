---
title: hyprnote
date: 2025-04-27T12:21:35+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1743993330456-6fa7a903b3bd?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDU3Mjc2MDR8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1743993330456-6fa7a903b3bd?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3NDU3Mjc2MDR8&ixlib=rb-4.0.3
---

# [fastrepl/hyprnote](https://github.com/fastrepl/hyprnote)

![README banner](https://github.com/user-attachments/assets/44ebe793-004e-4313-8e04-2491ab076bea)

<p align="center">
<h1 align="center">Hyprnote <i>(Public Beta)</i></h1>
<p align="center">AI notepad for meetings. <strong>Local-first & Extensible</strong>.</p>
 <p align="center">
  <a href="https://hyprnote.com/discord" target="_blank"><img src="https://img.shields.io/static/v1?label=Join%20our&message=Discord&color=blue&logo=Discord" alt="Discord"></a>
  <a href="https://x.com/tryhyprnote" target="_blank"><img src="https://img.shields.io/static/v1?label=Follow%20us%20on&message=X&color=black&logo=x" alt="X"></a>
</p>
</p>
   
## Introduction

**What does Hyprnote do?**

- Records and transcribes your meetings  
- Generates **powerful summaries** from your raw meeting notes

**What’s special about it?**

- <ins>Works **offline**</ins> using **open-source models** (_Whisper_ & _Llama_)  
- Highly [extensible](https://docs.hyprnote.com/extensions/), powered by [plugins](https://docs.hyprnote.com/plugins/)

## Installation

```bash
brew tap fastrepl/hyprnote && brew install hyprnote --cask
```

- [Macos](https://hyprnote.com/download) (public beta)
- [Windows](https://github.com/fastrepl/hyprnote/issues/66) (soon)
- [Linux](https://github.com/fastrepl/hyprnote/issues/67) (maybe)

## Highlights

### Hypercharge your notes
Casually jot stuff down and Hyprnote will craft a meeting note based on your memos.

<img src="https://github.com/user-attachments/assets/1615a9f0-7a30-44c1-b142-0d1774a84e89" width="720" />

### Offline & Privacy
Hyprnote is local-first which means you can be off the grid and it's perfectly fine.

<img src="https://github.com/user-attachments/assets/e5014024-3f6a-457a-8f1c-3b183883b782" width="720" />

### Extensions & Plugins
Just like VSCode, You can add or create extensions based on your circumstances.

<img src="https://github.com/user-attachments/assets/341d2e6c-a2c7-432b-95b8-fdc2018838d5" width="720" />

<br />
<br />

For example, [transcript extension](https://docs.hyprnote.com/extensions/transcript.html) is powered by [listener plugin](https://docs.hyprnote.com/plugins/listener.html).

```ts
useEffect(() => {
  const channel = new Channel<SessionEvent>();
  listenerCommands.subscribe(channel);

  channel.onmessage = (e) => {
    if (e.type === "started") {
      setIsLive(true);
    }
    if (e.type === "stopped") {
      setIsLive(false);
    }
  };

  return () => {
    listenerCommands.unsubscribe(channel);
  };
}, []);
```
