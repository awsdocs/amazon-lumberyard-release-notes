# Amazon Lumberyard Release Notes: Improvements and Changes in [VERSION NUMBER] ([MONTH OF RELEASE] [YEAR OF RELEASE])

Lumberyard Beta [VERSION NUMBER]] provides improvements and changes to Lumberyard systems and functionality.

**Topics**
+ [Asset Pipeline](#Pipeline-improvements-changes-v1.22)
+ [AWS Native SDK Updated](#SDK-improvements-changes-v1.22)
+ [Large Worlds](#Worlds-improvements-changes-v1.22)
+ [Mobile/macOS](#macOS-improvements-changes-v1.22)
+ [Networking](#network-improvements-changes-v1.22)
+ [Systems](#systems-improvements-changes-v1.22)
+ [Twitch Commerce SDK](#Twitch-improvements-changes-v1.22)
+ [Visual Studio 2017](#VS-improvements-changes-v1.22)
+ [Miscellaneous](#misc-improvements-changes-v1.22)

## Asset Pipeline<a name="Pipeline-improvements-changes-v1.22"></a>

### New Features

**Asset Bundler** - a command line tool to bundle game assets for release. The following are additional new features that support Asset Bundling:
+ Asset Validation Gem - gem useful for run your game exclusively from Asset Bundles.

+ Product Dependency System - Builders now generate product dependencies, including copy jobs. Product dependencies are the backbone of asset bundling and allow the Asset Bundler to evaluate at an asset and determine all of the other assets that rely on it.
+ Missing Dependency Scanner - a tool to identify potential missing product dependencies.
+ XML Schema System - a framework for defining dependencies for XML files.
+ Asset Tagging System - File Tagging System. This system provides a way to "tag" an asset as a certain type such as "editor-only", "shader" or "ignore product dependencies", which is then used by the Missing Dependency Scanner and other tools.

**Delta Catalogs** - .Pak files (paks) now contain smaller versions of AssetCatalog.xml that live within a pak and describe only the files within that pak.  At run time when opening a new pak file through CryPak the system will automatically search for a delta catalog within the pak and if found update the asset registry with the information within that pak file layered over the old data (You can add new assets or update old assets).

### Improvements

**Asset Processor**

+ Asset Processor Timer - The Asset Processor now displays 3 timers: Last Scan, Analysis, and Processing.  Each timer represents the amount of time the Asset Processor spent in each of those three phases.
+ Improved Error File Visibility - Made asset warnings more visible in the Asset Processor.
+ Added folders for platform-specific AssetProcessorPlatformConfig.ini so to separate generic vs platform-specific configs
+ Performance improvements.

**Stale File Load Cleanup** 

+ Removed some unnecessary calls that were loading deprecated files.

**Copy Dependency Builder**

+ Some copy jobs that were previously defined in AssetProcessorPlatformConfig.ini have been removed. In their place, we have a new CopyDependencyBuilder that performs the same copy to the cache. This CopyDependencyBuilder also examines the assets it copies for product dependencies, emitting what it finds.

**Gems version**

Some of the Gems included have new versions.

+ Populate the app descriptors (see the command on this page https://docs.aws.amazon.com/lumberyard/latest/userguide/az-module-gems.html) to make sure your project continues to work.
+ If populating app descriptors fails for your project, manually edit your project's Gems.json file to reference the new versions of the Gems. 
+ Update your project's Editor.xml and Game.xml (found in the config folder under project root).
  + In the editor.xml, change the line mentioning Gem.LyShine to: <Class name="AZStd::string" field="dynamicLibraryPath" value="Gem.LyShine.0fefab3f13364722b2eab3b96ce2bf20.v0.1.0" type="{189CC2ED-FDDE-5680-91D4-9F630A79187F}"/>
  + In the Game.xml, update the line referencing the SaveData Gem to: <Class name="AZStd::string" field="dynamicLibraryPath" value="Gem.SaveData.d96ab03f53d14c9e83f9b4528c8576d7.v0.1.0" type="{189CC2ED-FDDE-5680-91D4-9F630A79187F}"/>
</Class>

<Class name="DynamicModuleDescriptor" field="element" type="{D2932FA3-9942-4FD2-A703-2E750F57C003}">

## AWS Native SDK version update<a name="SDK-improvements-changes-v1.22"></a>

+ AWS Native SDK version was updated to 1.7.167.
**Note for Linux users:** If your project or a gem depends on AWS Native SDK on Linux (such as a Twitch gem) then debug/profile builds requires your Linux configuration to have libssl.so.1.1 and libcrypto.so.1.1 present on your system. Release builds link these libraries staticly. No changes are required for release Linux builds of Lumberyard.

## Large Worlds<a name="Worlds-improvements-changes-v1.22"></a>

**Large Worlds: Legacy Terrain**

+ Users can now remove the legacy terrain system from the engine using compile/script flag enable_legacy_terrain in dev/Code/wscript.
+ Users can now enable more detailed memory, I/O, and performance metrics for the Legacy Terrain System with cvars e_TerrainPerformanceSecondsPerLog and e_TerrainPerformanceCollectMemoryStats.
+ Removed dependency on Legacy Terrain from several core systems in the engine.

**Large Worlds: Roads**

+ Road meshification is ~4x faster due to improvements in batching, jobification, and time slicing.

## Systems<a name="systems-improvements-changes-v1.22"></a>

Memory Improvements
+ Memory stomp detection tool. When enabled, checks for memory corrupted by reads/writes outside the boundaries of allocated memory.   
+ Improved memory tracking for VRAM and display of e_MemoryProfiling cvar (LY-104969). Memory usage now is broken down:
++ VRAM
+++ Texture: Render targets, Assets, Dynamic
+++ Buffer: Vertex, Index, Constant, Other
++ CPU: broken down by main allocators
+ Restructure of Allocator's class hierarchy; making them more stable to boot ordering (solving some issues in Release/monolithic builds)
+ Asset Memory Analyzer Asset Memory Analyzer
+ Memory driller: fixes to dump all allocations to CSV file
**NOTE**: with any change affecting memory layout, previous memory-related bugs that did not cause crashes/issues could now produce unexpected behavior. For example, a memory overrun that previously was not producing any visible/detectable bug, may now produce issues.

## Mobile/macOS<a name="macOS-improvements-changes-v1.22"></a>

+ Added support for Xcode 11. Requires macOS High Sierra or higher.

## Networking<a name="network-improvements-changes-v1.22"></a>

Networking: Network Context has the following improvements and changes:
+ In Lumberyard, Network Context simplifies writing multiplayer components in C++. What can take 100 lines of code in raw GridMate implementation, Network Context accomplishes in less than a dozen lines with the interface.
+ Network Context is part of the context family, along with Serialize Context, Edit Context and Behavior Context. Network Context allows you to tag component member variables as network fields or remote procedure calls and use them in a simpler manner, compared to direct GridMate use.
+ link to the public doc on Network Context goes here
+ MultiplayerSample has been updated to use Network Context in multiple components, such as HealthBarComponent.

## Twitch Commerce SDK deprecated<a name="Twitch-improvements-changes-v1.22"></a>

+ The Twitch Gem no longer requires the Twitch Commerce SDK. The Twitch Commerce SDK is deprecated. 

## Visual Studio 2017<a name="VS-improvements-changes-v1.22"></a>

Lumberyard 1.22 includes the following Visual Studio support changes:
+ Visual Studio 2017 version 15.9.2 is now the supported version.
+ Visual Studio 2015 is no longer supported.

## Miscellaneous<a name="misc-improvements-changes-v1.xx"></a>
+ The Resource Compiler Image tool will be deprecated in an upcoming Lumberyard release, replaced by the ImageProcessing gem.
