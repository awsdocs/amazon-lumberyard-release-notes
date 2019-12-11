# Amazon Lumberyard Release Notes: Improvements and Changes in [VERSION NUMBER] ([MONTH OF RELEASE] [YEAR OF RELEASE])

Lumberyard Beta [VERSION NUMBER]] provides improvements and changes to Lumberyard systems and functionality.

**Topics**
+ [Asset Pipeline](#Pipeline-improvements-changes-v1.22)
+ [AWS Native SDK Updated](#SDK-improvements-changes-v1.22)
+ [Large Worlds](#Worlds-improvements-changes-v1.22)
+ [Mobile](#mobile-improvements-changes-v1.22)
+ [Platform](#platform-improvements-changes-v1.22)
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

### Memory stomp detection tool
When enabled, checks for memory corrupted by reads/writes outside the boundaries of allocated memory.   

### Asset Memory Analyzer
The Asset Memory Analyzer is an experimental feature that gives you a breakdown of all memory that has been allocated by the various assets loaded into the game. Use it to get a better idea of what assets are actually loaded at runtime and what their individual contribution is to memory use.

**Usage**

Enabling the driller:
1. Edit AzCore/Debug/AssetMemoryDriller.h, and ensure AZ_ANALYZE_ASSET_MEMORY is defined (just need to uncomment the line). 
1. If you want to enable analysis in other build types (excluding Release), you may manually enable memory tracking:
  1. Edit dev/Code/Framework/AzCore/AzCore/Memory/Config.h
  1. Uncomment the line that says #define AZCORE_ENABLE_MEMORY_TRACKING
1. Edit Game.xml located in dev/Dragonfly/Config:
  1. Set the field enableDrilling to true.
  1. Set the field enableAssetMemoryDriller to true.

View the live analysis in ImGUI:

If ImGUI is enabled, you can open the analysis window by choosing AssetMemoryAnalyzer → Open from the debug menu.
This opens the Asset Memory Analysis window.

Each recorded asset is displayed, along with the number of allocations and total kilobytes allocated, for both heap and VRAM.
You can use the buttons at the top of the window to sort descending on any of the available categories.
You can expand individual assets to view both:
+ Individual allocations that belong to an asset, and
+ Sub-assets that were loaded as a consequence of loading this asset.

Export the analysis to a JSON file:

You can export the analysis to a JSON file in a number of ways:
+ If ImGUI is enabled, you can choose AssetMemoryAnalyzer → Export JSON from the debug menu.
+ In the console, you can enter assetmem_export to generate the file.
+ From C++ code, you can call ExportJSONFile on the AssetMemoryAnalyzerRequestBus, with nullptr as the parameter to generate it to the default location.
  + Example: EBUS_EVENT(AssetMemoryAnalyzerRequestBus, ExportJSONFile, nullptr);
This will generate a file in your @log@ directory (e.g. dev/Cache/dragonfly/pc/user/log on Windows) titled assetmem-<TIMESTAMP>.json.

View JSON files in the web viewer:

The web viewer is located at dev/Gems/AssetMemoryAnalyzer/www/AssetMemoryViewer/index.html.

Open it your web browser (Chrome appears to be most reliable), and on the webpage that opens you can drag-and-drop your JSON file or click on the target area to browse to it.

This will display the contents of the file in an expandable table. You can sort the table by any of the columns. The columns give a breakdown by multiple categories:
+ **Heap Allocations** and **VRAM Allocations**.
+ Local summary (i.e. not including any sub-assets) and Total summary (i.e. including all sub-assets).
+ Number of allocations and kilobytes allocated.

Drill into any of the listed assets to discover:
+ Individual allocations belonging to that asset.
+ Sub-assets that were loaded as a consequence of loading this asset.

Instrument Code

Initial asset loading:

The AssetMemoryDriller traps allocations (heap and VRAM) that occur during a slice of code execution or "scope" when an asset is active for recording. 

When a system begins loading a new asset, it should use the AZ_ASSET_NAMED_SCOPE macro to demarcate the C++ scope in which that asset may be actively making allocations. **Code example**

Subsequent asset processing:

Later on, when a system is going to do more work involving an asset, or if the asset is being handed off to a different thread, it should use the AZ_ASSET_ATTACH_TO_SCOPE macro with a pointer that was allocated and tracked by the initial asset. This will associate any further allocations with the same asset. **Code example**

You can attempt to attach to any pointer that was created while that asset was in scope, *or even any portion of memory that was allocated to it.* For instance, the following code works: **Code example**

What this means is that you don't need an original pointer to an object that was allocated within a scope in order to attach to it, just something "close enough". This makes it possible to attach across systems to objects that have been defined with multiple inheritance.

Ebus asset processing:

Ebus handlers can automatically attempt to attach to a scope for each handler receiving an event. This works when the handler itself was allocated as part of an asset.

If the handler was created while an asset was in scope, you can modify an Ebus as follows: **Code example**

Some Lumberyard Ebuses already use this feature, such as the TickBus. If you find others that should use it, please add them! (But you should not default to using this EventProcessingPolicy if it is not applicable; see Cost of instrumentation below.)

Instrumentation considerations:

+ Creating a new named scope requires function calls, an environment lookup, locking a mutex, two hashtable lookups, and thread-local modifications.
+ Attaching to an existing scope requires function calls, an environment lookup, locking a mutex, a lookup in a large red-black tree, and thread-local modifications.

Most of the time this is a relatively small cost in the scheme of things, but it is significant enough that you should not use the AZ_ASSET_ATTACH_TO_SCOPE macro (or use the AssetMemoryDrillerEventProcessingPolicy on your Ebus) redundantly, or if it is unlikely to attach to anything.

There is **zero cost to instrumentation** in builds where the AssetMemoryDriller is disabled, i.e. if the AZ_ANALYZE_ASSET_MEMORY macro remains undefined. (This is the default in Performance builds.)


### Other improvements
+ Improved memory tracking for VRAM and display of e_MemoryProfiling cvar (LY-104969). Memory usage now is broken down:
  + VRAM
   Texture: Render targets, Assets, Dynamic
   Buffer: Vertex, Index, Constant, Other
   + CPU: broken down by main allocators
+ Restructure of Allocator's class hierarchy; making them more stable to boot ordering (solving some issues in Release/monolithic builds).
+ Memory driller: fixes to dump all allocations to CSV file.
**NOTE**: with any change affecting memory layout, previous memory-related bugs that did not cause crashes/issues could now produce unexpected behavior. For example, a memory overrun that previously was not producing any visible/detectable bug, may now produce issues.
+ IMGUI Improvements: Now using the latest version of IMGUI with added support for consoles and controllers.
+ Asserts Framework improvement: Now using only AZ_Assert with 3 levels of the sys_assert CVAR:  0: nothing, 1: log only, 2: dialog when asserts fails on all platforms.

## Mobile<a name="mobile-improvements-changes-v1.22"></a>

+ Added support for Xcode 11. Requires macOS High Sierra or higher.
+ Support for iOS v13 
+ iOS and Android: Optimization for GPU Bandwidth - Eliminate 'Diffuse Accumulation' render target during the Lighting pass which resulted in memory savings of 88 bits per pixel perf frame. It is enabled through cvar "r_DeferredShadingLBuffersFmt = 2".
+ Latest NDK (r20) support.
+ Improvements to Release/Shader Compilation workflow (Remove extra step, Error reporting).
+ Android: Improve Load Times by 40 percent faster when loading assets from the .APK not in .pak files.
+ Support for Android Q - API 29

## Platform<a name="platform-improvements-changes-v1.22"></a>
+ Achievements/trophies Gem: The Achievement Gem provides an interface to your game to Achievement and Trophy services for console games. It allows for games to unlock, query, and update achievement and trophy data through the services provided for that console. 

+ Add Rich presence to Platform services: The Presence Gem provides an interface to your game to the Presence services for console games. It allows for games to set and query the presence status for a user on that console. Presence is the message that is displayed in friends lists and on a users profile as set by the game based on the user's activity. 


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
