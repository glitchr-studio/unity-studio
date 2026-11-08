# Glitch Art Studio (`io.glitchr.studio`)

The package every Glitch Art project starts from. It has no code of its own: it brings the team's packages as
dependencies.

| Package | What it is |
|---|---|
| `io.glitchr.toolkit` - Glitch Art Toolkit | The shared editor tools: orbit camera, Scene-view TextMesh Pro editing, Dock icon, studio layout, package publisher, MCP for Unity extensions ([glitchr-studio/unity-toolkit](https://github.com/glitchr-studio/unity-toolkit)) |
| `io.glitchr.store` - Forge Store | The package store in the editor, connected to Glitch Art's Forge ([glitchr-forge/unity-store](https://github.com/glitchr-forge/unity-store)) |

Not included, on purpose:

- **Forge Seal** (`io.glitchr.licensing`): a game sold with a licence adds it itself.
- **Tile Weaver** (`io.glitchr.tileweaver`): only the projects that use it.
- **MCP for Unity**: installed from Git (Marco's fork), which a package cannot depend on. Each project lists it in
  its `manifest.json`.

## Install

Unity resolves a package's dependencies from a registry only, never from Git. Until Glitch Art's Forge serves the
`io.glitchr.*` packages as a scoped registry, list the dependencies next to this package in `Packages/manifest.json`:

```json
"io.glitchr.studio": "https://github.com/glitchr-studio/unity-studio.git#v0.1.0",
"io.glitchr.toolkit": "https://github.com/glitchr-studio/unity-toolkit.git#v0.3.0",
"io.glitchr.store": "https://github.com/glitchr-forge/unity-store.git"
```

Once the Forge's registry is online, the scoped registry and the first line are enough:

```json
"scopedRegistries": [{ "name": "Glitch Art", "url": "https://<forge>/upm", "scopes": ["io.glitchr"] }]
```
