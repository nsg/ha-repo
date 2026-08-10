<div align="center">
  <h1>NSG Home Assistant add-ons</h1>
  <p>Home Assistant catalog metadata for add-ons maintained in their own source repositories.</p>
</div>

## About

This is an installable Home Assistant add-on repository. Each top-level add-on
folder contains only the metadata Home Assistant needs to present and install
that add-on. Source code, container builds, release artifacts, and container
images remain in the add-on's own project repository.

## Add-ons

| Add-on | Architectures | Project |
| --- | --- | --- |
| [Bosun](bosun/README.md) | `amd64` | [nsg/bosun](https://github.com/nsg/bosun) |
| [Camon](camon/README.md) | `amd64` | [nsg/camon](https://github.com/nsg/camon) |

## Install

[![Add repository to my Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fnsg%2Fha-repo)

Or add the repository manually:

1. Open **Settings → Apps → App store** in Home Assistant.
2. Open the **⋮** menu, select **Repositories**, and add
   `https://github.com/nsg/ha-repo`.
3. Select an app from the store and install it.

Home Assistant versions that still use the former name show **Add-ons** and
**Add-on store** instead of **Apps** and **App store**.

## Repository structure

```text
repository.yaml       Home Assistant repository metadata
bosun/                Bosun catalog entry
camon/                Camon catalog entry
<add-on>/config.yaml  Runtime and image metadata
<add-on>/README.md    Store summary
<add-on>/DOCS.md      Documentation shown in Home Assistant
```

The repository intentionally contains no application source, Dockerfiles,
build workflows, binaries, or container images.
