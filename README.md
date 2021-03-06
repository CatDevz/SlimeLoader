# 🗺️ SlimeLoader

Slime loader is a map loader & saver for the file format Slime as specified [here](https://github.com/CatDevz/SlimeLoader/blob/master/SLIME_FORMAT.txt) implemented in Minestom.

Features:
```
- [x] World loading
  - [x] Blocks
  - [x] TileEntities
  - [ ] Entities
  - [x] Extra Data
        (Data will be loaded into the instance's "Data" Tag)
- [ ] World saving
  - [ ] Blocks
  - [ ] TileEntities
  - [ ] Entities
  - [ ] Extra Data
        (Data from "Data" Tag will be saved)
- [ ] Async
```

## Installation

Add the following to your `build.gradle.kts`

```kotlin
repositories { 
  maven("https://jitpack.io")
}

dependencies { 
  implementation("com.github.CatDevz:SlimeLoader:master-SNAPSHOT")
}
```

## Usage

The library is quite simple to use. If you need to get your slime world from somewhere else (ex. AWS S3) you can implement the `SlimeSource` interface. 

#### Kotlin

```kotlin
val instanceManager = MinecraftServer.getInstanceManager()
val instanceContainer = instanceManager.createInstanceContainer()

val file = File("Slime file goes here")
val slimeSource: SlimeSource = FileSlimeSource(file)
val slimeLoader: IChunkLoader = SlimeLoader(instanceContainer, slimeSource)

instanceContainer.chunkLoader = slimeLoader
```

#### Java

```java
InstanceManager instanceManager = MinecraftServer.getInstanceManager();
InstanceContainer instanceContainer = instanceManager.createInstanceContainer();

File file = new File("Slime file goes here");
SlimeSource slimeSource = new FileSlimeSource(file);
SlimeLoader slimeLoader = new SlimeLoader(instanceContainer, slimeSource, false);

instanceContainer.setChunkLoader(slimeLoader);
```

## License

SlimeLoader is licensed under the MIT license

###### Written by [Cody](https://github.com/CatDevz) for AstroMC
