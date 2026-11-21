# 🌿 cozy-world

**A deterministic, seed-based generator for cozy game worlds.**

Generate beautiful, reproducible worlds for cozy games, survival games, exploration games, and procedural environments. Create terrain, discover locations, encounter wildlife, collect loot, and experience dynamic weather and seasons — all driven by a seed.

<p align="center">
  <a href="https://www.npmjs.com/package/cozy-world">
    <img src="https://img.shields.io/npm/v/cozy-world?style=for-the-badge&color=4CAF50" alt="npm version" />
  </a>
  <a href="https://www.npmjs.com/package/cozy-world">
    <img src="https://img.shields.io/npm/dm/cozy-world?style=for-the-badge&color=2196F3" alt="npm downloads" />
  </a>
  <a href="https://www.npmjs.com/package/cozy-world">
    <img src="https://img.shields.io/npm/l/cozy-world?style=for-the-badge&color=8BC34A" alt="License" />
  </a>
  <a href="https://github.com/astoncloudvn/cozy-world">
    <img src="https://img.shields.io/github/stars/astoncloudvn/cozy-world?style=for-the-badge&color=FFC107" alt="GitHub stars" />
  </a>
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/cozy-world"><strong>📦 View on npm</strong></a>
  ·
  <a href="https://github.com/astoncloudvn/cozy-world"><strong>💻 Source Repository</strong></a>
  ·
  <a href="https://www.npmjs.com/package/cozy-world"><strong>⬇️ Install Package</strong></a>
</p>

---

## ✨ Features

- 🌍 **Procedural Worlds** — Generate terrain, heightmaps, biomes, water, regions, and vegetation.
- 🎲 **Deterministic Generation** — The same seed and options produce the same world.
- 📍 **Discoverable Locations** — Generate named places and points of interest.
- 🐾 **Dynamic Wildlife** — Generate creatures influenced by seasons, weather, and time.
- 🎁 **Procedural Loot** — Generate loot with configurable luck.
- 🌦️ **Living Environments** — Simulate day/night cycles, seasons, and changing weather.
- 🎨 **Rendering Helpers** — Convert world data into image data or heightmap meshes.
- 🧩 **Game-engine Friendly** — Integrate generated data into your own game or rendering pipeline.

## 📦 Installation

Install `cozy-world` using npm:

```bash
npm install cozy-world
```

Other package managers:

```bash
# pnpm
pnpm add cozy-world

# yarn
yarn add cozy-world
```

<p>
  <a href="https://www.npmjs.com/package/cozy-world">
    <img src="https://img.shields.io/badge/npm-cozy--world-CB3837?style=flat-square&logo=npm" alt="Install from npm" />
  </a>
  <a href="https://github.com/astoncloudvn/cozy-world">
    <img src="https://img.shields.io/badge/source-GitHub-181717?style=flat-square&logo=github" alt="Source code" />
  </a>
</p>

## 🚀 Quick Start

```ts
import { CozyWorld } from "cozy-world";

const world = new CozyWorld({
  seed: "meadow-1",
  size: 128,
});

// Access generated world data
console.log(world.map);

// Generate a location
const location = world.generateLocation();
console.log(location);

// Generate wildlife
const creature = world.generateCreature();
console.log(creature);

// Generate loot with a luck bonus
const loot = world.generateLoot({ luck: 0.3 });
console.log(loot);

// Generate a world event
const event = world.generateEvent();
console.log(event);

// Advance the simulation by six hours
world.advanceTime(6);

// Export the world
const savedWorld = world.toJSON();
console.log(savedWorld);
```

## 🌱 How Seed-Based Generation Works

A seed determines the random sequence used to generate a world.

```ts
const worldA = new CozyWorld({
  seed: "peaceful-meadow",
  size: 128,
});

const worldB = new CozyWorld({
  seed: "peaceful-meadow",
  size: 128,
});
```

Both worlds use the same seed and options, making their initial generated data reproducible.

Change the seed to generate a different world:

```ts
const forestWorld = new CozyWorld({
  seed: "misty-forest",
  size: 128,
});
```

**Why it matters:** Reproducible generation makes it easier to save worlds, share seeds, test game logic, and recreate procedural environments.

## 🗺️ World Data

The generated `world.map` provides the world data your game can use.

Depending on the generated map structure, this may include:

- **Heightmap** — Terrain elevation data.
- **Biomes** — Environmental regions and biome assignments.
- **Water** — Water-related map data.
- **Regions** — Spatial divisions of the world.
- **Vegetation** — Vegetation distribution data.

Example:

```ts
const world = new CozyWorld({
  seed: "quiet-valley",
  size: 128,
});

const map = world.map;
```

Use the returned data to build your own terrain renderer, exploration system, or game simulation.

## 📍 Locations, Creatures, Loot & Events

### Locations

```ts
const location = world.generateLocation();
```

Generate named places and points of interest for exploration.

### Creatures

```ts
const creature = world.generateCreature();
```

Generate wildlife with environmental context such as season, weather, and time.

### Loot

```ts
const loot = world.generateLoot({
  luck: 0.3,
});
```

Generate loot using a configurable luck value.

### Events

```ts
const event = world.generateEvent();
```

Generate events for exploration, encounters, or other game systems.

## 🌦️ Time & Environment

Advance the world's simulation:

```ts
world.advanceTime(6);
```

Time progression can affect day/night cycles, seasons, and weather. This allows you to build game mechanics around changing environmental conditions.

## 🎨 Rendering & Integration

`cozy-world` generates world data that can be integrated with your own rendering engine.

### 3D Terrain

Use `toHeightmapMesh(world.map)` to convert the map into heightmap mesh data for a 3D rendering pipeline, such as a Three.js `BufferGeometry` workflow.

```ts
import {
  CozyWorld,
  toHeightmapMesh,
} from "cozy-world";

const world = new CozyWorld({
  seed: "sunlit-hills",
  size: 128,
});

const meshData = toHeightmapMesh(world.map);
```

Adapt the returned mesh data to the geometry format required by your renderer.

### 2D Rendering

Use `toImageData(world.map)` to obtain image data for a 2D canvas workflow.

```ts
import {
  CozyWorld,
  toImageData,
} from "cozy-world";

const world = new CozyWorld({
  seed: "tiny-garden",
  size: 128,
});

const imageData = toImageData(world.map);
```

Use the resulting data in your own canvas rendering code.

## 💾 Saving & Loading

Export the current world state:

```ts
const data = world.toJSON();
```

You can store the resulting data using your preferred save system, database, or storage format.

Check the actual serialized structure before implementing a custom loader.

## 🛠️ Development

Clone the repository:

```bash
git clone https://github.com/astoncloudvn/cozy-world.git
cd cozy-world
```

Install dependencies:

```bash
npm install
```

Build the TypeScript project:

```bash
npm run build
```

Run tests:

```bash
npm test
```

## 🧭 Use Cases

`cozy-world` can be used as a foundation for:

- Cozy exploration games
- Procedural survival worlds
- Farming and nature simulation games
- Wildlife and ecosystem prototypes
- Terrain generation experiments
- 2D and 3D procedural environments

The library provides generation utilities. Your game remains responsible for rendering, player interaction, and gameplay systems built on top of the generated data.

## 📚 Links

<p>
  <a href="https://www.npmjs.com/package/cozy-world">
    <img src="https://img.shields.io/badge/Explore-cozy--world_on_npm-CB3837?style=for-the-badge&logo=npm" alt="Explore cozy-world on npm" />
  </a>
  <a href="https://github.com/astoncloudvn/cozy-world">
    <img src="https://img.shields.io/badge/Source-GitHub-181717?style=for-the-badge&logo=github" alt="View source code" />
  </a>
</p>

- **npm package:** https://www.npmjs.com/package/cozy-world
- **Source repository:** https://github.com/astoncloudvn/cozy-world

## 📄 License

MIT License. See [`LICENSE`](./LICENSE) for details!
