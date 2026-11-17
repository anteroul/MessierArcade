# Messier Arcade

Demo game built with [Messier Engine](https://github.com/anteroul/messier-engine), a WebGPU game engine and editor
that runs in the browser. It contains four simple minigames, picked from an arcade menu, plus the editor's showcase
scene.

| Scene | What it shows | Controls |
| --- | --- | --- |
| **Arcade** | The menu: a dark showroom with a lit stand per game, spotlights, emissive trims, world-space text, scene loading with `sceneManager` | `A`/`D` or arrows choose, `Enter` play |
| **Neon Run** | A neon city at speed: unlit emissive materials, 2D shapes as a sun and glows, a shadow-casting sunset, an engine drone that rises with speed | `A`/`D` steer, `R` restart |
| **Topple** | Physics under a daytime sky: stacks of metal, lacquer and marble blocks, a cannon with a charged shot and an aiming arc, positional sound for falling blocks | `WASD` aim, hold and release `Space` to fire, `R` reset |
| **Starfall** | Space shooter: metallic hull, point-light explosions, parallax star sheets and nebulae made of 2D shapes, guns that pan with the ship | `WASD` fly, `Space` fire, `R` restart |
| **Gem Rush** | A tour of the scripting API: forces, raycasts, signals, groups, spawning and destroying objects, slow motion | `WASD` roll, `Space` jump, `R` restart |
| **Main** | The editor's showcase scene: PBR materials, lights, shadows, a glTF and an OBJ model, physics | — |

`Backspace` returns from a game to the Arcade. Sound starts after your first click or key press, as browsers require.

## Open it

You need the Messier editor, 0.4.0 or later, in Chrome or Edge (project folders use the File System Access API).

1. Clone this repository.
2. In the editor, **☰ → Open Project…** and pick the cloned folder.
3. Choose **Arcade** in the scene picker and press **▶ Play**, or press **Build** to download the arcade as a single
   web page that runs anywhere WebGPU does.

The editor saves changes back into the folder as you work, and picks up files you change outside it.

## What's inside

```
project.json          name, build settings (the Arcade first, then the games), start scene
scenes/*.messier      one scene per file (JSON)
scripts/*.ts          the games' rules: one TypeScript script per file
assets/models/        sample models (a glTF lantern, an OBJ crystal with its .mtl); .meta files hold their ids
tsconfig.json         lets VS Code type-check the scripts…
.messier/messier.d.ts …against the types of the 'messier' module (written by the editor)
```

Scripts are plain TypeScript classes that import from `'messier'`. Edit them in the editor's Scripts tab or in VS Code:
the editor hot-reloads changes, even during Play. See the engine's
[scripting guide](https://github.com/anteroul/messier-engine/blob/main/docs/scripting.md).

## Where it comes from

The scenes are generated from the engine's demo builders (`src/demos/`, `src/demoGame.ts` and `src/demo.ts` in the
engine repository) with `npm run generate:demo`, which writes this folder as `examples/Demo/`. Regenerating replaces
the project files (it keeps `.git`, this README and `LICENSE`), so changes made in the editor are overwritten the next
time the demo is regenerated.

## License

This demo game is licensed under the MIT License (see [LICENSE](LICENSE)). The Messier engine and editor have their
own license; the files the editor puts into projects and builds (the game runtime and `.messier/messier.d.ts`) may be
shared with your games under the engine's additional permissions.
