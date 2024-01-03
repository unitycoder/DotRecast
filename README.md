[![License: Zlib](https://img.shields.io/badge/License-Zlib-lightgrey.svg)](https://opensource.org/licenses/Zlib)
[![.NET](https://github.com/ikpil/DotRecast/actions/workflows/dotnet.yml/badge.svg)](https://github.com/ikpil/DotRecast/actions/workflows/dotnet.yml)
[![CodeQL](https://github.com/ikpil/DotRecast/actions/workflows/codeql.yml/badge.svg?branch=main)](https://github.com/ikpil/DotRecast/actions/workflows/codeql.yml)
[![NuGet Version and Downloads count](https://buildstats.info/nuget/DotRecast.Core)](https://www.nuget.org/packages/DotRecast.Core)
![Github Repo Size](https://img.shields.io/github/repo-size/ikpil/DotRecast)
![Languages](https://img.shields.io/github/languages/top/ikpil/DotRecast)
[![Visitors](https://api.visitorbadge.io/api/daily?path=https%3A%2F%2Fgithub.com%2Fikpil%2FDotRecast&countColor=%23263759&style=flat-square)](https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fikpil%2FDotRecast)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/ikpil?style=flat-square&logo=GitHub-Sponsors&link=https%3A%2F%2Fgithub.com%2Fsponsors%2Fikpil)](https://github.com/sponsors/ikpil)

# Screenshot
![screenshot](https://user-images.githubusercontent.com/313821/266750582-8cf67832-1206-4b58-8c1f-7205210cbf22.gif)

https://user-images.githubusercontent.com/313821/266782992-32a72a43-8f02-4214-8f1e-86b06952c8b7.mp4

# Introduction
1. DotRecast is a port of C++'s [recastnavigation](https://github.com/recastnavigation/recastnavigation) and Java's [recast4j](https://github.com/ppiastucki/recast4j) to the C# language.
2. For game development, C# servers, C# project, and Unity3D are supported.
3. DotRecast consists of Recast and Detour, Crowd, Dynamic, Extras, TileCache, DemoTool, Demo


## DotRecast.Recast

Recast is state of the art navigation mesh construction toolset for games.

Recast is...
* 🤖 **Automatic** - throw any level geometry at it and you will get a robust navmesh out
* 🏎️ **Fast** - swift turnaround times for level designers
* 🧘 **Flexible** - easily customize the navmesh generation and runtime navigation systems to suit your specific game's needs.

Recast constructs a navmesh through a multi-step rasterization process:

1. First Recast voxelizes the input triangle mesh by rasterizing the triangles into a multi-layer heightfield.
2. Voxels in areas where the character would not be able to move are removed by applying simple voxel data filters.
3. The walkable areas described by the voxel grid are then divided into sets of 2D polygonal regions.
4. The navigation polygons are generated by triangulating and stitching together the generated 2d polygonal regions.

## DotRecast.Detour

Recast is accompanied by Detour, a path-finding and spatial reasoning toolkit. You can use any navigation mesh with Detour, but of course the data generated with Recast fits perfectly.

Detour offers a simple static navmesh data representation which is suitable for many simple cases.  It also provides a tiled navigation mesh representation, which allows you to stream of navigation data in and out as the player progresses through the world and regenerate sections of the navmesh data as the world changes.

## DotRecast.Recast.Demo

You can find a comprehensive demo project in the `DotRecast.Recast.Demo` folder. It's a kitchen sink demo showcasing all the functionality of the library. If you are new to Recast & Detour, check out [SoloNavMeshBuilder.cs](/src/DotRecast.Recast.Demo/Builder/SoloNavMeshBuilder.cs) to get started with building navmeshes and [TestNavmeshTool.cs](/src/DotRecast.Recast.Demo/Tools/TestNavmeshTool.cs) to see how Detour can be used to find paths.

### Building DotRecast.Recast.Demo

1. `DotRecast.Recast.Demo` uses [dotnet 8](https://dotnet.microsoft.com/) to build platform specific projects. Download it and make sure it's available on your path, or specify the path to it.
2. Open a command prompt, point it to a directory and clone DotRecast to it: `git clone https://github.com/ikpil/DotRecast.git`
3. Open `<DotRecastDir>\DotRecast.sln` with Visual Studio 2022 and build `DotRecast.Recast.Demo`
   - Optionally, you can run using the `dotnet run` command with `DotRecast.Recast.Demo.csproj`

#### Windows

- need to install [microsoft visual c++ redistributable package](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist)

#### Linux & macOS & Windows

- Navigate to the `DotRecast.Recast.Demo` folder and run `dotnet run`

### Running Unit tests

#### With VS2022

- In Visual Studio 2022 go to the test menu and press `Run All Tests` 

#### With CLI

- in the DotRecast folder open a command prompt and run `dotnet test`

## Integrating with your game or engine

It is recommended to add the source directories `DotRecast.Core`, `DotRecast.Detour.Crowd`, `DotRecast.Detour.Dynamic`, `DotRecast.Detour.TitleCache`, `DotRecast.Detour.Extras` and `DotRecast.Recast` into your own project depending on which parts of the project you need. For example your level building tool could include `DotRecast.Core`, `DotRecast.Recast`, and `DotRecast.Detour`, and your game runtime could just include `DotRecast.Detour`.

## Discuss

- Discuss Recast & Detour: http://groups.google.com/group/recastnavigation
- Development blog: http://digestingduck.blogspot.com/

## License

DotRecast is licensed under ZLib license, see [LICENSE.txt](LICENSE.txt) for more information.
