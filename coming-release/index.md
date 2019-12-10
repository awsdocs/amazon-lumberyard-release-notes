# Lumberyard Release Notes – Beta [VERSION NUMBER] ([MONTH OF RELEASE] [YEAR OF RELEASE])

Lumberyard Beta [VERSION NUMBER] continues to add new features, improvements, and fixes. Thank you to everyone in our community whose suggestions help us continue to make Lumberyard better with every release! Send feedback to our [forums](https://forums.awsgametech.com/) as well as the Lumberyard team at lumberyard-feedback@amazon.com. For the latest Lumberyard updates, follow us on [Twitter](https://twitter.com/amznlumberyard), [Facebook](https://www.facebook.com/amazonlumberyard/), and our [blog](https://aws.amazon.com/blogs/gametech/).

**Topics**
+ [Highlights](#highlights)
+ [Improvements and Changes](improvements-changes.md)
+ [Fixes](fixes.md)
+ [Known Issues](known-issues.md)

## Highlights<a name="highlights"></a>

Here's a sampling of the new features found in Lumberyard [1.22 link].

**Topics**
+ [Asset Pipeline](#highlights-pipeline)
+ [AWS Native SDK](#highlights-SDK)
+
+

### Asset Pipeline<a name="highlights-pipeline"></a>

**Asset Bundler** - a command line tool to bundle game assets for release. The following are additional new features that support Asset Bundling:
+ Asset Validation Gem - gem useful for run your game exclusively from Asset Bundles.
+ Product Dependency System - Builders now generate product dependencies, including copy jobs. Product dependencies are the backbone of asset bundling and allow the Asset Bundler to evaluate at an asset and determine all of the other assets that rely on it. 
+ Missing Dependency Scanner - a tool to identify potential missing product dependencies.
+ XML Schema System - a framework for defining dependencies for XML files.
+ Asset Tagging System - File Tagging System. This system provides a way to "tag" an asset as a certain type such as "editor-only", "shader" or "ignore product dependencies", which is then used by the Missing Dependency Scanner and other tools.

**Delta Catalogs** - .Pak files (paks) now contain smaller versions of AssetCatalog.xml that live within a pak and describe only the files within that pak.  At run time when opening a new pak file through CryPak the system will automatically search for a delta catalog within the pak and if found update the asset registry with the information within that pak file layered over the old data (You can add new assets or update old assets)

### AWS Native SDK version update<a name="highlights-SDK"></a>

AWS Native SDK version was updated to 1.7.167. **Note for Linux users:** if your project or a gem depends on AWS Native SDK on Linux (such as Twitch gem) then debug/profile builds requires your Linux configuration to have libssl.so.1.1 and libcrypto.so.1.1 present on your system. Release builds link these libraries staticly, so no changes required for release Linux builds of Lumberyard.

### ...
