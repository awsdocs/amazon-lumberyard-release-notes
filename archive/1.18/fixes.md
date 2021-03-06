# Fixes<a name="lumberyard-v1.18-fixes"></a>

Lumberyard Beta 1.18 resolves earlier problems. Choose a topic area to learn more about the related fixes.

**Topics**
+ [Asset Processor](#asset-processor-fixes-v1.18)
+ [Cloud Canvas](#cloud-canvas-fixes-v1.18)
+ [Component Entity System](#component-entity-system-fixes-v1.18)
+ [Lua](#lua-fixes-v1.18)
+ [Lumberyard Editor](#lumberyard-editor-fixes-v1.18)
+ [Lumberyard Installation](#lumberyard-installation-fixes-v1.18)
+ [Lumberyard Setup Assistant](#lumberyard-setup-assistant-fixes-v1.18)
+ [Material Editor](#material-editor-fixes-v1.18)
+ [Particle Editor](#particle-editor-fixes-v1.18)
+ [Project Configurator](#project-configurator-fixes-v1.18)
+ [Slices](#slices-fixes-v1.18)
+ [UI Editor](#ui-editor-fixes-v1.18)
+ [Miscellaneous](#miscellaneous-fixes-v1.18)

## Asset Processor<a name="asset-processor-fixes-v1.18"></a>

The Asset Processor now properly logs startup information.

## Cloud Canvas<a name="cloud-canvas-fixes-v1.18"></a>

Cloud Canvas has the following fixes:
+ In the Microsoft Edge browser, if the current Cloud Gem Portal session is accessed using a URL generated by a `lmbr_aws` command, the shared link feature now works.
+ After you use the Player Account Cloud Gem Portal to ban a player, the banned player now appears on the **Banned Players** tab of the Leaderboard Cloud Gem Portal.
+ In Cloud Canvas Resource Manager, when you add a Lambda function resource to a resource group, valid **Node.js** runtime options are now available.
+ iOS devices can now use Open SSL to connect to cloud gem applications.
+ On the **Individual Responses** tab of the In-Game Survey Cloud Gem Portal, the **Export to CSV** option now correctly creates a `.csv` file instead of a `.txt` file.
+ In the Defect Reporter cloud gem, when the Jira integration tag is removed from a deployment and the deployment is updated (for example, by using the *lmbr\_aws deployment update -d *deployment\_name** command), the update no longer fails with `CrossGemCommunicationInterfaceResolver` errors.
+ The **Analytics** and **Administration** links no longer disappear after you sign out of and back into the Cloud Gem Portal.
+ A favicon now appears on the Microsoft Edge browser tab for the Cloud Gem Portal sign-in page.
+ After you use the Defect Reporter Cloud Gem Portal to delete a report, the screenshots and logs corresponding to the deleted report are now deleted from the `lumberyard_version\dev\Cache\project_name\pc\User\ScreenShots\DefectReporter\` and `lumberyard_version\dev\Cache\ project_name\pc\User\log\LogBackups\` directories.
+ After you update the Cloud Gem Framework version of an existing project stack and run the *lmbr\_aws update-framework-version* command, the command now correctly updates the `local-project-settings.json` file to the new Cloud Gem Framework version.
+ On the **Report Detail** page of the Defect Reporter Cloud Gem Portal, the download link for the `DxDiag` file now works correctly in Windows 7.

## Component Entity System<a name="component-entity-system-fixes-v1.18"></a>

The component entity system has the following fixes:
+ When an entity is highlighted, you can now select the entity in the **Entity Outliner** without any issues.
+ When you search or filter for component types in the **Entity Outliner**, disabled components now appear in the search/filter results as well.
+ If you change an entity name while the **Entity Inspector** is open, the title bars for pinned inspectors will also update.
+ The **Road** component no longer leaves artifacts at the end of segments.
+ The **Style** value on the **Point Light** component now increases or decreases by a value of 1.
+ Filtering by entity name in the **Entity Outliner** no longer causes memory or performance issues.
+ Updated tag names are now properly reflected in the component.
+ All digits in a float field are now properly selected.

## Lua<a name="lua-fixes-v1.18"></a>

Lua has the following fixes:
+ Lua assets are now reliably reloaded.
+ Using the Lua IDE to debug no longer produces debugging and performance issues.
+ The **Lua Script** component now properly updates when you change types in an associated Lua file.

## Lumberyard Editor<a name="lumberyard-editor-fixes-v1.18"></a>

Lumberyard Editor has the following fixes:
+ The editor no longer stops working when you exit game mode, if an entity and the viewport camera are too far apart.
+ The editor no longer stops working when you assign the default material to a geom cache.
+ Global probes no longer overpower local probes.
+ The editor no longer stops working when you edit an asset that has special characters.
+ You can now easily select the transform gizmo in the viewport.
+ The editor no longer stops working when you enter game mode after choosing **Close Level** in the **Legacy Entities Detected** window.
+ You can now use **Ctrl\+Z** to undo any moves that you make as the **Camera** component.

## Lumberyard Installation<a name="lumberyard-installation-fixes-v1.18"></a>

When you log in to Lumberyard with your Amazon account, you will no longer receive an invalid error page. Previously, new Lumberyard users could experience an authentication issue with the login window that prevented Lumberyard Editor from launching successfully. For more information, see the [Lumberyard forums](https://forums.awsgametech.com/t/how-to-bypass-the-editor-login-window-when-unable-to-connect/3141).

## Lumberyard Setup Assistant<a name="lumberyard-setup-assistant-fixes-v1.18"></a>

You can now run the **Setup Assistant** in a remote desktop connection.

## Material Editor<a name="material-editor-fixes-v1.18"></a>

When you create a material with a waterfall shader, you can now select the **Environment map** check box under **Shader Generation Params**.

## Particle Editor<a name="particle-editor-fixes-v1.18"></a>

The **Particle Editor** has the following fixes:
+ GPU emitters now spawn the same number of particles as CPU emitters in the preview window.
+ Particles now persist for the correct number of frames. For example, a muzzle flash that should persist for one frame, now draws for only one frame.

## Project Configurator<a name="project-configurator-fixes-v1.18"></a>

The **Project Configurator** has the following fixes:
+ Clicking **Advanced Settings** for the Samples Project now auto-populates the components.
+ When you create or enable a gem in your project, only the added gem and the project are recompiled. Previously all gems in the project were recompiled.

## Slices<a name="slices-fixes-v1.18"></a>

Slices have the following fixes:
+ The entity status now shows the correct setting in the **Entity Inspector**.
+ Nested slice instances now accept keep overrides that are saved to a high-level slice.
+ The viewport now remains stable and responsive when you save a slice.
+ The editor no longer stops working when you save a slice in debug mode.
+ Slice icons no longer disappear in the **Entity Outliner** when you save a slice with cyclical dependencies.
+ The undo option no longer displays slice overrides that do not exist.
+ Reverting the root level slice will no longer revert slice overrides.
+ The slice save operation now properly saves all overrides.

## UI Editor<a name="ui-editor-fixes-v1.18"></a>

The **UI Editor** has the following fixes:
+ You can now push a new slice instance into a UI slice.
+ The **UILayoutFitter** now works properly with sprite sheets.
+ The `UiGameEntityContext:OnSliceInstantiated` no longer stops working when you spawn a slice within a slice.
+ The **UiImageComponent** no longer stops working when the load screen is rendered.
+ The **UiTextComponent** no longer stops working when you set the character spacing in Lua.
+ Moving a text element no longer produces unnecessary XML parsing.
+ Text no longer wraps incorrectly when you push to slice.
+ The **Mask** component is no longer affected by the fader.
+ Fonts are no longer corrupted after extensive gameplay.
+ Root slice entities that are compiled in UI canvas assets can now reuse the entity ID from the source asset.
+ The entity picker now works properly for Lua scripts on UI canvas elements.
+ The **UILayoutFitter** now accurately calculates the height of layout grids.
+ Layouts are now recomputed when there are changes to layout cell properties.
+ All active particles are now cleared when there are changes to a canvas with the **Particles** component.

## Miscellaneous<a name="miscellaneous-fixes-v1.18"></a>

Lumberyard has the following miscellaneous fixes:
+ Restoring the editor layout is no longer an issue on multi-monitor setups with disparate resolutions and sizes.
+ Log files are now properly archived. Previously, logs were appended to the same file.
+ Input and Alt\+Tab no longer cause issues when switching out of a game while it loads.
+ Output and debug directory paths now point to the correct location.
+ EBuses that have deprecated interfaces and/or traits now provide deprecation information.