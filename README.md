# Glitch Art Studio (`io.glitchr.studio`)

The package every Glitch Art project starts from. It has no code of its own. It depends on
[Forge Store](https://github.com/glitchr-forge/unity-store) (`io.glitchr.store`), the open-source package store, and is
its Glitch Art preset: the `"hub"` section of its `package.json`, which Unity ignores and Forge Store reads from the
disk as soon as this package is in the project. Forge Store itself stays neutral; everything Glitch Art is here, as
data:

- **Glitch Art on GitHub**: the repositories of `glitchr-forge` named `unity-*` that are UPM packages. The public ones
  are listed for everyone; the private ones need a GitHub token that can read them (Forge Store > Sources > GitHub);
- the packages below, by their Git URLs;
- the **theme**: Glitch Art's coral accent and logo in the window's header.

A user can hide the preset in Forge Store's Sources and add their own sources beside it.

| Package | What it is |
|---|---|
| `io.glitchr.toolkit` - Glitch Art Toolkit | The shared editor tools: orbit camera, Scene-view TextMesh Pro editing, Dock icon, studio layout, package publisher, MCP for Unity extensions ([glitchr-studio/unity-toolkit](https://github.com/glitchr-studio/unity-toolkit)) |
| `io.glitchr.store` - Forge Store | The package store in the editor, connected to Glitch Art's Forge ([glitchr-forge/unity-store](https://github.com/glitchr-forge/unity-store)) |
| `io.glitchr.licensing` - Forge Seal | Licence checks for a game sold through a Forge: a game adds it itself ([glitchr-forge/unity-licensing](https://github.com/glitchr-forge/unity-licensing)) |

Not listed: Tile Weaver (`io.glitchr.tileweaver`), only in the projects that use it, and MCP for Unity, installed from
Marco's fork by each project's `manifest.json`.

## Install

In Forge Hub, **Prepare for Glitch Art** on a project writes the packages every project gets into its
`Packages/manifest.json` (the sources marked `"install": true` below); what the project has already is kept.

Or by hand, in `Packages/manifest.json` - Forge Store first, then this package:

```json
"io.glitchr.store": "https://github.com/glitchr-forge/unity-store.git",
"io.glitchr.studio": "https://github.com/glitchr-studio/unity-studio.git#v0.4.1"
```

Window > Forge Store then shows Glitch Art's sources; install the packages the project needs.

The dependency on `io.glitchr.store` is declared, but Unity resolves a package's dependencies from a registry only,
never from Git. Checked with Unity 6000.3.28f1: when the project lists `io.glitchr.store` itself (from Git or a
folder), that entry wins whatever version this package asks for; without it, the project's packages fail to resolve
("Package [io.glitchr.store@1.2.0] cannot be found"). So list both, as above, until Glitch Art's Forge serves the
`io.glitchr.*` packages as a scoped registry: then this package alone brings the store.

## The `"hub"` section

The same document as a hub's `hub.json` (Forge Store's
[docs/sources.md](https://github.com/glitchr-forge/unity-store/blob/main/docs/sources.md)), kept in the package so a
tag freezes the list. `"package"` names a source's package without reading it; `"install": true` marks the ones
every project gets:

```json
"hub": {
  "version": 1,
  "name": "Glitch Art",
  "sources": [
    {"name": "Glitch Art Toolkit", "type": "git", "url": "https://github.com/glitchr-studio/unity-toolkit.git#v0.4.0",
     "package": "io.glitchr.toolkit", "install": true}
  ]
}
```

The preset's other source, in the same section:

```json
{"name": "Glitch Art on GitHub", "type": "github", "owner": "glitchr-forge", "pattern": "unity-*"}
```

and its look: `"theme": {"accent": "#fc6875", "accentDark": "#fc6875", "logo": "..."}`.
