# manverup

**Man**ifest-based **Ver**sioned **Up**dates.

> Downloaded 40 GB.
>
> Waited an hour.
>
> The game/program/app ended up being almost the same size as before with just a few bug fixes.

That experience inspired Manverup.

The idea is simple: if only 500 MB changed, why should users download 40 GB again?

Manverup is an open-source Python tool that enables incremental updates for projects composed of independent files, modules, services, or assets.

Instead of forcing users to download an entire application, package, or game every time an update is released, Manverup compares local and remote manifests and downloads only the files whose version has increased.
## Why?
Many applications distribute updates as large monolithic packages. Even when only a few files have changed, users may be required to download gigabytes of data again.

Manverup follows a different approach:

- Every file or module has a unique identifier.
- Every file or module has a version number.
- A manifest contains the list of all available elements and their versions.
- During an update, local and remote manifests are compared.
- Only elements whose version is newer on the remote side are downloaded.

This reduces:

- Download size
- Update time
- Bandwidth usage
- Temporary storage requirements
## How it works
A project is divided into independently updatable elements.

Each element contains:

- Unique identifier
- Version number

The manifest contains all available elements and their latest versions.

Update flow:

1. Load the local manifest.
2. Download the remote manifest.
3. Compare versions.
4. Identify elements with newer remote versions.
5. Download only those elements.
6. Replace outdated local files.

```text
Local manifest        Remote manifest
--------------        ---------------
core v1               core v2
ui v3                 ui v3
audio v4              audio v5

Download:
- core v2
- audio v5

Skip:
- ui v3
```
## Goals
- Simple manifest format
- Version-based updates
- Minimal downloads
- Server-agnostic design
- Easy integration into existing projects
- Language-independent update targets
## Architecture requirements
Manverup works best when the application is organized into clearly separated modules, services, or asset packs.

The more independent the components are, the smaller and more efficient the updates become.

Examples:

- Games with separate asset packs
- Plugins and extensions
- Modular applications
- Microservice-based deployments
- Downloadable content (DLC)
- Large datasets divided into packages
## Scope and Expectations
Manverup is developed as a practical open-source project, not as a commercial-grade update platform.

The goal is not to compete with mature solutions that have been refined for years, nor to claim that this implementation is the most efficient possible approach.

Instead, the objective is to provide a simple and understandable framework that developers can use, improve, extend, or replace according to their needs.

If someone builds a faster, safer, or more scalable alternative, that is a success for the idea itself.

The project welcomes criticism, improvements, and contributions.
## Acknowledgements
The core idea behind Manverup is not new.

Version-based updates and incremental downloads have existed for decades in tools such as package managers, version control systems, and software deployment platforms. Git, pip, and many other systems already avoid transferring data that has not changed.

What inspired this project is the fact that many large software distributions still rely on update mechanisms that can feel unnecessarily heavy from the user's perspective, often requiring the download of tens of gigabytes even when only a relatively small portion of the content has changed.

Manverup is an attempt to provide a simple, open-source, and reusable implementation of the same philosophy:

**only transfer what actually changed.**
## Status
Early development.
## Inspiration
The project was inspired by the idea that software updates should transfer only the data that actually changed.

Modern package managers and version control systems already rely on similar principles. Manverup applies the same philosophy to general-purpose project deployment and asset distribution.
