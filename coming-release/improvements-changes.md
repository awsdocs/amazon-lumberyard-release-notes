# Amazon Lumberyard Release Notes: Improvements and Changes in [VERSION NUMBER] ([MONTH OF RELEASE] [YEAR OF RELEASE])

Lumberyard Beta [VERSION NUMBER]] provides improvements and changes to Lumberyard systems and functionality.

**Topics**
+ [AWS Native SDK - Updated to 1.7.167](#SDK-improvements-changes-v1.22)
+ [Large Worlds](#Worlds-improvements-changes-v1.22)
+ [Mobile/macOS](#macOS-improvements-changes-v1.22)
+ [Networking](#network-improvements-changes-v1.22)
+ [Twitch Commerce SDK deprecated](#Twitch-improvements-changes-v1.22)
+ [Visual Studio 2017](#VS-improvements-changes-v1.22)
+ [Miscellaneous](#misc-improvements-changes-v1.xx)



## AWS Native SDK version update<a name="SDK-improvements-changes-v1.22"></a>

+ AWS Native SDK version was updated to 1.7.167. 
**Note for Linux users:** If your project or a gem depends on AWS Native SDK on Linux (such as a Twitch gem) then debug/profile builds requires your Linux configuration to have libssl.so.1.1 and libcrypto.so.1.1 present on your system. Release builds link these libraries staticly. No changes are required for release Linux builds of Lumberyard.

## Large Worlds<a name="Worlds-improvements-changes-v1.22"></a>

### Large Worlds: Legacy Terrain
+ Users can now remove the legacy terrain system from the engine using compile/script flag enable_legacy_terrain in dev/Code/wscript.
+ Users can now enable more detailed memory, I/O, and performance metrics for the Legacy Terrain System with cvars e_TerrainPerformanceSecondsPerLog and e_TerrainPerformanceCollectMemoryStats.
+ Removed dependency on Legacy Terrain from several core systems in the engine.

### Large Worlds: Roads has the following improvements and changes:
+ Road meshification is ~4x faster due to improvements in batching, jobification, and time slicing.

## Mobile/macOS<a name="macOS-improvements-changes-v1.22"></a>
+ Added support for Xcode 11. Requires macOS High Sierra or higher.

## Networking<a name="network-improvements-changes-v1.22"></a>

Networking: Network Context has the following improvements and changes:
+ In Lumberyard, Network Context simplifies writing multiplayer components in C++. What can take 100 lines of code in raw GridMate implementation, Network Context accomplishes in less than a dozen lines with the interface.
+ Network Context is part of the context family, along with Serialize Context, Edit Context and Behavior Context. Network Context allows you to tag component member variables as network fields or remote procedure calls and use them in a simpler manner, compared to direct GridMate use.
+ <<link to the public doc on Network Context goes here>>
+ MultiplayerSample has been updated to use Network Context in multiple components, such as HealthBarComponent.

## Twitch Commerce SDK deprecated<a name="Twitch-improvements-changes-v1.22"></a>

+ The Twitch Gem no longer requires the Twitch Commerce SDK. The SDK is deprecated. 

## Visual Studio 2017<a name="VS-improvements-changes-v1.22"></a>

Lumberyard 1.22 includes the following Visual Studio support changes:
+ Visual Studio 2017 version 15.9.2 is now supported version.
+ Visual Studio 2015 is no longer supported.

## Miscellaneous<a name="misc-improvements-changes-v1.xx"></a>
