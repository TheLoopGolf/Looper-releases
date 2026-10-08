# Third-party notices

Looper is proprietary software (Copyright (c) 2026 Loop Audio Lab, all rights reserved; see
`LICENSE` and `EULA.md`). It is built with the third-party components below, which remain the
property of their owners and are used under their own licences. Nothing in Looper's EULA limits
your rights under those licences.

The only dependency fetched by the build is JUCE (CMake `FetchContent`, tag **8.0.6**, see
`CMakeLists.txt`); the other entries are libraries bundled inside the JUCE modules Looper links
(`juce_audio_utils`, `juce_audio_processors`, `juce_audio_formats`, `juce_gui_basics`,
`juce_gui_extra`, `juce_dsp` and their dependencies). System libraries (C/C++ runtime, threads,
OS audio / graphics frameworks) are provided by the operating system.

## JUCE

- Copyright (c) Raw Material Software Limited.
- Used under the **JUCE 8 End User Licence Agreement** (commercial JUCE licence), not the AGPLv3:
  https://juce.com/legal/juce-8-licence/
- JUCE is dual licensed under the JUCE licence and the AGPLv3. Looper does not use the AGPLv3
  option.

## Components bundled in JUCE 8.0.6 and compiled into Looper

| Component | Used for | Licence |
|-----------|----------|---------|
| VST3 SDK 3.7.12 (Steinberg Media Technologies GmbH) | VST3 plug-in format | Steinberg VST3 Licence (proprietary) or GPLv3, see the SDK's `LICENSE.txt`. VST is a registered trademark of Steinberg Media Technologies GmbH. |
| AudioUnitSDK (Apple Inc.) | Audio Unit plug-in format (macOS) | Apache License 2.0 |
| FLAC (Josh Coalson, Xiph.Org Foundation) | Reading FLAC samples | BSD 3-clause |
| Ogg Vorbis (Xiph.Org Foundation) | Ogg Vorbis audio format support | BSD 3-clause |
| zlib (Jean-loup Gailly, Mark Adler) | Compression | zlib licence |
| libpng | PNG images | libpng / zlib licence |
| jpeglib (Independent JPEG Group) | JPEG images | IJG licence: "this software is based in part on the work of the Independent JPEG Group" |
| HarfBuzz | Text shaping | "Old MIT" licence |
| SheenBidi (Muhammad Tayyab Akram) | Bidirectional text | Apache License 2.0 |

The full licence texts ship inside the JUCE source tree (see JUCE's `LICENSE.md`, "The JUCE
Framework Dependencies", for the exact file of each one). Audio Units is a trademark of Apple
Inc.

## Algorithms

- **PCG32** random number generator (`Source/VoiceEngine/FastRng.h`): Looper's own
  implementation of the published PCG32 XSH-RR algorithm by Melissa E. O'Neill
  (https://www.pcg-random.org). The reference C implementation is Apache License 2.0.
- **YIN** pitch detection (de Cheveigne and Kawahara, 2002) and the Simper state-variable filter
  are implemented from their published descriptions.

## Factory content

The factory patches and samples are synthesised by Looper's own generator
(`Tools/FactoryContent`); they contain no third-party recordings.
