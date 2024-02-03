---
title: WhisperKit
date: 2024-02-03T12:16:18+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1706115963745-3656580b28b7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDY5MzM2NTV8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1706115963745-3656580b28b7?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDY5MzM2NTV8&ixlib=rb-4.0.3
---

# [argmaxinc/WhisperKit](https://github.com/argmaxinc/WhisperKit)

# WhisperKit

WhisperKit is a Swift package that integrates OpenAI's popular [Whisper](https://github.com/openai/whisper) speech recognition model with Apple's CoreML framework for efficient, local inference on Apple devices. 

Check out the demo app on [TestFlight](https://testflight.apple.com/join/LPVOyJZW).

[[Blog Post]](https://www.takeargmax.com/blog/whisperkit) [[Python Tools Repo]](https://github.com/argmaxinc/whisperkittools)

## Table of Contents

- [Installation](#installation)
  - [Prerequisites](#prerequisites)
  - [Steps](#steps)
- [Getting Started](#getting-started)
  - [Quick Example](#quick-example)
  - [Model Selection](#model-selection)
  - [Generating Models](#generating-models)
  - [Swift CLI](#swift-cli)
- [Contributing \& Roadmap](#contributing--roadmap)
- [License](#license)
- [Citation](#citation)

## Installation
WhisperKit can be integrated into your Swift project using the Swift Package Manager.

### Prerequisites
- macOS 14.0 or later.
- Xcode 15.0 or later.

### Steps
1. Open your Swift project in Xcode.
2. Navigate to `File` > `Add Package Dependencies...`.
3. Enter the package repository URL: `https://github.com/argmaxinc/whisperkit`.
4. Choose the version range or specific version.
5. Click `Finish` to add WhisperKit to your project.

## Getting Started
To get started with WhisperKit, you need to initialize it in your project.

### Quick Example
This example demonstrates how to transcribe a local audio file:

```swift
import WhisperKit

// Initialize WhisperKit with default settings
Task {
   let pipe = try? await WhisperKit()
   let transcription = try? await pipe!.transcribe(audioPath: "path/to/your/audio.{wav,mp3,m4a,flac}")?.text
    print(transcription)
}
```

### Model Selection
WhisperKit automatically downloads the recommended model for the device if not specified. You can also select a specific model by passing in the model name:
```swift
let pipe = try? await WhisperKit(model: "large-v3")
```

For a list of available models, see our [HuggingFace repo](https://huggingface.co/argmaxinc/whisperkit-coreml).

### Generating Models

WhisperKit also comes with the supporting repo [`whisperkittools`](https://github.com/argmaxinc/whisperkittools) which lets you create and deploy your own fine tuned versions of Whisper in CoreML format to HuggingFace. Once generated, they can be loaded by simply changing the repo name to the one used to upload the model:

```swift
let pipe = try? await WhisperKit(model: "large-v3", modelRepo: "username/your-model-repo")
```

### Swift CLI

The Swift CLI allows for quick testing and debugging outside of an Xcode project. To install it, run the following:

```bash
git clone https://github.com/argmaxinc/whisperkit.git
cd whisperkit
```

Then, setup the environment and download the models.

**Note**:
1. this will download all available models to your local folder, if you only want to download a specific model, see our [HuggingFace repo](https://huggingface.co/argmaxinc/whisperkit-coreml))
2. before running `download-models`, make sure [git-lfs](https://git-lfs.com) is installed

```bash
make setup
make download-models
```

You can then run the CLI with:

```bash
swift run transcribe --model-path "Models/whisperkit-coreml/openai_whisper-large-v3" --audio-path "path/to/your/audio.{wav,mp3,m4a,flac}" 
```

Which should print a transcription of the audio file.


## Contributing & Roadmap
Our goal is to make WhisperKit better and better over time and we'd love your help! Just search the code for "TODO" for a variety of features that are yet to be built. Please refer to our [contribution guidelines](CONTRIBUTING.md) for submitting issues, pull requests, and coding standards, where we also have a public roadmap of features we are looking forward to building in the future.

## License
WhisperKit is released under the MIT License. See [LICENSE.md](LICENSE.md) for more details.

## Citation
If you use WhisperKit for something cool or just find it useful, please drop us a note at [info@takeargmax.com](mailto:info@takeargmax.com)!

If you use WhisperKit for academic work, here is the BibTeX:

```
@misc{whisperkit-argmax,
   title = {WhisperKit},
   author = {Argmax, Inc.},
   year = {2024},
   URL = {https://github.com/argmaxinc/WhisperKit}
}
```
