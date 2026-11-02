# RareInjector

RareInjector is a primarily Linux-oriented project designed to replace game assets such as textures, 3D models, and video files at runtime, without modifying the game's original files or requiring traditional mod installations.
The project is currently in development.

> **Project status:** Stubbed repository. Public release is tentatively expected by 15 November 2026.

For additional information, contact N. Evarine of Nomandible.
-- Sora (aka stinkymalinky), an anonymous friend :)

---

## Disclaimer for Game Publishers and Copyright Holders

RareInjector is intended for use with games and other software that users have legitimate access to.
Users are responsible for providing their own replacement assets and ensuring that they have the necessary rights or permissions to use them.
RareInjector does not distribute copyrighted game assets, games, or other third-party media.
Owning a copy of a game does not necessarily grant permission to extract, redistribute, or modify its copyrighted content.
The project is intended for legitimate asset replacement, graphics experimentation, accessibility, and customization. It is not designed to facilitate software piracy, DRM circumvention, or anti-cheat evasion.
RareInjector is an independent project and is not affiliated with any game publisher or graphics hardware manufacturer unless explicitly stated otherwise.

## Overview

RareInjector works through a collection of modular connectors designed to interface with graphics APIs, including:

- Vulkan
- OpenGL
- DirectX

Rather than relying on game-specific modifications, RareInjector aims to intercept graphics operations and substitute assets as they are loaded or processed by the rendering pipeline.
For example, instead of Skyrim rendering Alduin using his original model, RareInjector could substitute an entirely different model, such as Thomas the Tank Engine.
This is not an upscaling or image reconstruction technique like DLSS. The intention is to replace the underlying assets themselves rather than modify the final rendered image.
The project aims to remain graphics API-agnostic, allowing different connectors to handle the underlying implementation while presenting a common interface for asset substitution.

## Asset Replacement

RareInjector is intended to support the replacement of several asset types:

| Asset type | Description |
|---|---|
| 3D Models | Replace existing models with user-provided alternatives. |
| Textures | Substitute textures with other images or materials. |
| Videos | Replace video assets with alternative media. |

Additional asset types may be supported as development progresses.

### Model Handling

Replacing 3D models introduces several compatibility challenges, particularly when replacement models differ significantly from the original assets.
Models may have different proportions, dimensions, skeletal structures, and bone layouts.
RareInjector is being developed with several approaches to address these differences:

- **Model stretching:** Adjust replacement models to better fit the proportions and skeletal layout expected by the original model.
- **Model scaling:** Allow users to adjust the overall size of replacement models independently.
- **Animation disabling:** A feature currently in development will allow users to disable animations entirely when compatibility is not possible or desirable.
- **Animation handling:** Another approach under development aims to intercept and manipulate animation-related data so that animations can be applied even when the replacement model uses a different skeletal structure.

The intention is to provide multiple compatibility options rather than require replacement models to follow a single predefined structure.
Depending on the game and replacement asset, users may choose to adapt the model, disable animation, or attempt to preserve animation through compatibility handling.

## Graphics API Compatibility

RareInjector is designed around modular graphics API connectors.
Each connector is responsible for communicating with its respective graphics API and handling the operations necessary for asset substitution.
This modular architecture is intended to make the project extensible without tying the entire implementation to a single graphics API.

Current target APIs:

- Vulkan
- OpenGL
- DirectX

Actual compatibility will depend on the implementation of each connector, the game being used, and the underlying hardware.

## Supported Hardware

Hardware compatibility is currently very limited. The following table reflects actual testing rather than assumed compatibility.

| Hardware | Status | Notes |
|---|---|---|
| NVIDIA RTX 3060 Ti | Tested | Currently the only tested configuration. |
| Other NVIDIA GPUs | Untested | Compatibility has not been verified. |
| AMD GPUs | Untested | Potentially compatible through supported graphics APIs. |
| Intel GPUs | Untested | Potentially compatible through supported graphics APIs. |
| Integrated GPUs | Untested | Compatibility has not been verified. |

**Important:** Graphics API compatibility does not guarantee hardware compatibility.

This section should be expanded as more users test the project. Ideally, future documentation will include separate compatibility lists for NVIDIA, AMD, and Intel hardware, including specific GPU models, driver versions, and known issues.

## Publisher and Anti-Cheat Compatibility

RareInjector is intended to remain compatible with legitimate publisher-supported use cases.
The project is not intended to provide cheats, wallhacks, competitive advantages, or mechanisms for circumventing anti-cheat software.
There is potential for cooperation with game publishers and anti-cheat providers to establish officially supported compatibility.

### Build Verification

One in-development feature is a verification mechanism that identifies whether an installation corresponds to a known-good RareInjector release.
This could allow publishers and anti-cheat providers to distinguish official RareInjector builds from modified or potentially malicious versions.
Potential implementation details include:

- Verification against known-good releases.
- Cryptographically signed release manifests.
- Build and version identification.
- Revocation of compromised or outdated releases.

This system is intended to provide a basis for publisher cooperation and compatibility verification.

**Note:** Build verification alone does not constitute anti-cheat approval. Any integration with third-party anti-cheat software would require appropriate technical cooperation and authorization. Talk to N. Evarine about that.

## Contributing

Contributions are welcome, particularly those involving additional graphics API support, platform compatibility, bug fixes, and general improvements.
To contribute:

1. Fork the repository.
2. Create a separate branch for your changes.
3. Implement and test your modifications.
4. Submit a merge request describing the changes and their purpose.

Contributions involving Windows support and additional hardware configurations are particularly welcome.

### Contributor Attribution

Contributors will receive individual entries in `Contribs.md`, documenting their respective contributions.
The project intentionally uses a per-contribution attribution format rather than listing each contributor only once.
In other words, someone who makes 500 meaningful contributions could receive 500 individual entries.
Partly for documentation purposes, partly because having a contributor listed 500 times would be quite entertaining.

### Code Quality

AI-assisted development is not inherently discouraged. However, contributions should be reviewed, tested, and understood by the person submitting them.
Please avoid submitting automatically generated code that you cannot explain or maintain.
The project currently has a very small maintenance team, and contributions should be reasonably focused and straightforward to review.

## Issue Reporting

Bug reports are welcome, particularly those involving hardware compatibility and graphics API implementations.
When reporting an issue, please include as much relevant information as possible:

- GPU manufacturer and model.
- Operating system and version.
- Graphics API being used.
- Relevant driver versions.
- Error messages and logs.
- Steps required to reproduce the issue.

### Hardware-Specific Issues

Please understand that the maintainers cannot reasonably be expected to own and test every graphics card available.
For example, debugging an issue exclusive to a legacy Radeon HD 5450 is difficult without access to that hardware.
If you identify a hardware-specific issue and are able to investigate or implement a fix, contributions are greatly appreciated.

## Licensing

RareInjector is distributed under the MIT License.
See `LICENSE.md` for the complete licence text.
Third-party dependencies and user-provided replacement assets may be subject to their own licensing terms.
Users are responsible for ensuring that their use and distribution of replacement assets complies with applicable licences and copyright law.

---

*RareInjector is an independent project. Compatibility, supported hardware, and feature availability are subject to change as development progresses.*
