# Amazon Lumberyard Release Notes: Fixes for [VERSION NUMBER] ([MONTH OF RELEASE] [YEAR OF RELEASE])

Lumberyard Beta [VERSION NUMBER]] resolves earlier problems. Choose a topic area to learn more about the related fixes.

**Topics**
+ [Editor](#editor-fixes-v1.22)
+ [FEATURE 2](#anchor-link-here)

## [FEATURE 1]

## Editor<a name="editor-fixes-v1.22"></a>
+ Selecting entities is now faster. Entity selection/deselection of all entities in a 20k level was 374 seconds and is now less than 10 (53x faster).

+ Entering Game Mode while an Entity Outliner filter is active is now faster. Entering Game Mode in a level with 20K entities while a filter is applied in the Entity Outliner used to take 5m 48s and now takes 3.18s.

+ Fixed a bug that occurred when searching for a component and clicking in the entity inspector that led to an unintended text field to appear.

+ Creating a child entity of a layer will now properly add the entity relative to the camera and terrain rather than placing the entity at 0,0,0.

+  Fixed a bug that caused the entity inspector to open the add component menu, rather than the new level dialog, when no entity was selected.

+  Fixed a bug that caused the entity inspector to scroll to the bottom of the component list after clearing an asset reference field.

+  Fixed a bug that was causing some components to display the number of components already on the entity in the Add Component menu.

+  Fixed a bug that caused the Align object to surface option from not being able to be disabled if enabled and immediately disabled.

+  Fixed a bug that prevented the “move component to top” option in the entity inspector from working when an entity contained more than 31 components.

+  Made it so the list of overrides doesn’t display an override count if there is only 1 override to save in the save slice overrides menu.

+  Now displays “no results found” if a search result in the entity outliner doesn’t return an entity.

+  Customers can now interact with asset reference property fields. Customers can click in a field, change the reference text, and see a list of assets that match the string and asset type appropriate for the field.

+  Removed an invalid console warning when saving a layer after the first time the layer is saved.

+ Removed the dialog telling customers that LY is already running if the customer tries to launch a second instance of the editor.

+  Pasting a second environment probe on an entity no longer crashes the editor.

+  Fixed a bug that caused locked layers to not lock entity selection in the viewport after returning from game mode.

+  Entering rename mode but not renaming a layer no longer marks the layer dirty.

+  There is now a “find layer in Asset Browser” option from a layer in the Entity Outliner.

+  Fixed a bug that caused the editing of some properties in a pinned entity inspector to not update the unselected entity the pinned panel was pinned from.

+  Fixed a bug that caused a level to think changes had occurred if the level was immediately closed after opening it.

+  Fixed a bug that resulted in a new component being created if an asset was dragged from the Asset Browser directly to a component asset reference field.

+  Added a warning if a customer attempts to save a layer with the same name as a layer that already exists in the level’s layer folder but does not exist in the level.

+  Fixed a bug that resulted in a crash when you removed an asset reference from a component and tried to save the asset.

+  Fixed a bug that failed to set the “Save as binary” property correctly after using the Recover layer option.

+  Fixed an issue displaying slice overrides in the outliner after unsuccessful slice push operations.


## [FEATURE 2]

[FEATURE 2] has the following fixes:
+ ...
