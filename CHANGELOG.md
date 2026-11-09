# Changelog

## 0.2.0

The package is Glitch Art's catalogue: its `package.json` has a `"hub"` section (the format of a hub's `hub.json`)
listing Glitch Art Toolkit 0.3.0, Forge Store and Forge Seal, which Forge Store reads when the package is added as a
source. `dependencies` is empty until the Forge serves a registry: the 0.1.0 dependencies could not be resolved from
Git, so the package could not be installed.

## 0.1.0

First version. `io.glitchr.studio` is now the team's base package, with no code of its own: it depends on
`io.glitchr.toolkit` 0.3.0 (Glitch Art Toolkit, the editor tools formerly published under this name) and
`io.glitchr.store` 1.0.0 (Forge Store).
