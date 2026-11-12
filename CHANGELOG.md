# Changelog

## 0.4.0

The Glitch Art preset of Forge Store 1.2.0, which no longer has any source built in:

- depends on `io.glitchr.store` 1.2.0 (list it in the project's manifest too until Glitch Art's Forge serves a
  registry: Unity does not resolve a package's dependencies from Git);
- the `"hub"` section adds Glitch Art's Forge (`https://glitchr.io/upm/-/hub.json`) and the GitHub source
  `glitchr-forge` / `unity-*` (private repositories with a GitHub token);
- a `"theme"`: Glitch Art's accent and logo in Forge Store's header.

## 0.3.1

The kit installs Glitch Art Toolkit 0.4.0 (Hierarchy icons from the rules packages register, and Unity 6.3's entity
IDs without obsolete warnings).

## 0.3.0

The kit: each source of the `"hub"` section names its package (`"package"`), and the ones every project gets are
marked `"install": true` - Glitch Art Toolkit and Forge Store; Forge Seal stays in the catalogue, for the games that
sell. Forge Hub's Prepare for Glitch Art writes those into a project's manifest in one click.

## 0.2.0

The package is Glitch Art's catalogue: its `package.json` has a `"hub"` section (the format of a hub's `hub.json`)
listing Glitch Art Toolkit 0.3.0, Forge Store and Forge Seal, which Forge Store reads when the package is added as a
source. `dependencies` is empty until the Forge serves a registry: the 0.1.0 dependencies could not be resolved from
Git, so the package could not be installed.

## 0.1.0

First version. `io.glitchr.studio` is now the team's base package, with no code of its own: it depends on
`io.glitchr.toolkit` 0.3.0 (Glitch Art Toolkit, the editor tools formerly published under this name) and
`io.glitchr.store` 1.0.0 (Forge Store).
