# Glitch Art Studio (`io.glitchr.studio`)

The package every Glitch Art project starts from. It has no code of its own. Its `package.json` is also Glitch Art's
catalogue: the `"hub"` section, which Unity ignores and [Forge Store](https://github.com/glitchr-forge/unity-store)
reads.

| Package | What it is |
|---|---|
| `io.glitchr.toolkit` - Glitch Art Toolkit | The shared editor tools: orbit camera, Scene-view TextMesh Pro editing, Dock icon, studio layout, package publisher, MCP for Unity extensions ([glitchr-studio/unity-toolkit](https://github.com/glitchr-studio/unity-toolkit)) |
| `io.glitchr.store` - Forge Store | The package store in the editor, connected to Glitch Art's Forge ([glitchr-forge/unity-store](https://github.com/glitchr-forge/unity-store)) |
| `io.glitchr.licensing` - Forge Seal | Licence checks for a game sold through a Forge: a game adds it itself ([glitchr-forge/unity-licensing](https://github.com/glitchr-forge/unity-licensing)) |

Not listed: Tile Weaver (`io.glitchr.tileweaver`), only in the projects that use it, and MCP for Unity, installed from
Marco's fork by each project's `manifest.json`.

## Install

1. Add Forge Store to the project, from its Git URL (Package Manager > + > Add package from git URL):
   `https://github.com/glitchr-forge/unity-store.git`
2. In Window > Forge Store > Sources, add this package as a Git package:
   `https://github.com/glitchr-studio/unity-studio.git#v0.2.0`
3. Forge Store lists the catalogue's packages; install the ones the project needs.

## The `"hub"` section

The same document as a hub's `hub.json` (Forge Store's
[docs/sources.md](https://github.com/glitchr-forge/unity-store/blob/main/docs/sources.md)), kept in the package so a
tag freezes the list:

```json
"hub": {
  "version": 1,
  "name": "Glitch Art",
  "sources": [
    {"name": "Glitch Art Toolkit", "type": "git", "url": "https://github.com/glitchr-studio/unity-toolkit.git#v0.3.0"}
  ]
}
```

`dependencies` stays empty for now: Unity resolves a package's dependencies from a registry only, never from Git.
Once Glitch Art's Forge serves the `io.glitchr.*` packages as a scoped registry, the package will depend on the
toolkit and the store, and installing it alone will bring them.
