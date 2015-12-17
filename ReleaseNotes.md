# Highlights

## Skeleton asset

A new Skeleton asset (*.xkskel) has been introduced. Both models and animations now hold a reference to a skeleton. This allows to reuse the same skeleton definition in multiple assets and to retarget models and animations to different skeletons.

Skeletons can be created alongside other assets, when importing an FBX file or other model format.

<img src="http://doc.xenko.com/1.5/rn_images/SkeletonThumbnail.png" align="center" />

## Root motion support for models, cameras, lights, etc.

Animations now apply root motion if they have no skeleton, or the ‘Root Motion’ property is enabled on the animation asset. The animation will then move the entity itself, instead of the skeleton’s root bone.
This is especially useful to import animations of lights, cameras or unskinned models, without the need to bind them to the bones of a skeleton.

The FBX importer will now also import animations of various camera parameters (near-plane, far-plane, field of view) and apply them to the CameraComponent of the animated entity. More properties may be supported in the future.

<img src="http://doc.xenko.com/1.5/rn_images/RootMotionProperty.png" align="center" />

## New animation update system

The animation system now internally uses a new UpdateEngine to update objects. This allows us to animate arbitrary properties of entities, while accessing them in a highly efficient way.
It will be the foundation for a future animation curve editor inside the GameStudio.

The new ‘Animated Properties’ sample demonstrates how to create animations of any property from a script.


## Simple Profiling system
It is now possible to visualize profiling information of all the game systems and custom profilers directly within your running games.
To get started, use the Game Profiler built-in script, attach it to an entity and when the game is running press LCtrl-LShift-P.

<img src="http://doc.xenko.com/1.5/rn_images/profiler.png" align="center" />

## Physic debug shapes at runtime
It is now possible to enable the rendering of physics collider shapes during runtime.
The debug shapes are normal entities and they must be enabled for each physics shape that requires it.
The best way to start with this feature is to use the Physics Shapes Render built-in script and attach the script to any entity that has a Physics Component and when the game is running press LCtrl-LShift-P.

<img src="http://doc.xenko.com/1.5/rn_images/phys-debug.png" align="center" />

## Asset View
The Asset view has been improved to help you better organize and manage your assets.

### New ‘view options’ menu
The view options are gathered in a single menu accessible from the asset view toolbar.

<img src="http://doc.xenko.com/1.5/rn_images/AssetViewOptions.png" align="center" />

You can display all the assets in the current folder only, in the current folder and its sub-folder. The third option let you display the assets and the sub folders.

You can also sort your assets by name, order, type or modification date. 

### New asset filter bar
With the new asset filter bar, you can filter your assets by name, tag, type or a combination of those. Each ‘filter tag’ can be disabled by a single click or removed from the active filters.
<img src="http://doc.xenko.com/1.5/rn_images/AssetFilterBar.png" align="center" />


To add a filter, type in the filter bar and matching filters will be displayed. Click on the one you want to add it to the list of active filters.
<img src="http://doc.xenko.com/1.5/rn_images/AddingAssetFilter.png" align="center" />

Only the assets matching the active filters will be displayed in the asset view. Note that type filters are inclusive, while name and tag filters are exclusive.

### Folder support in asset view
If the ‘Assets and folder in selected folder’ options is selected, the first level of sub-folder will be displayed in the asset view. You can drag and drop assets inside them. You can also copy/paste complete folder structure.
<img src="http://doc.xenko.com/1.5/rn_images/FolderSupport.png" align="center" />

## Copy-paste assets with their dependencies
You have now the ability to copy assets with their dependencies. To do that use the new entry ‘Copy with dependencies’ from the asset view context menu, or press Ctrl+Shift+C.
<img src="http://doc.xenko.com/1.5/rn_images/CopyAssetWithDependencies.png" align="center" />
For example, if you copy/paste a model with its dependencies, you will get a copy of this model along with a copy of all its dependencies (skeleton, materials, textures)

## Border and Center support in sprite sheet editor
For ‘Sprite2D’ sprites, you can move the position of the center by selecting the <img src="http://doc.xenko.com/1.5/rn_images/SpriteCenterIcon.png" /> in the toolbar of the sprite editor. Grab and move the cross to the desired position.

For ‘UI’ sprites, you can change the borders by selecting the <img src="http://doc.xenko.com/1.5/rn_images/SpriteBorderIcon.png" /> in the toolbar of the sprite editor. You can then resize each border (left, top, right and bottom) separately in the same way as the texture region, by grabbing and moving one of them. Note that the <img src="http://doc.xenko.com/1.5/rn_images/SpriteBorderLockIcon.png" /> lets you ‘lock’or ‘unlock’ the sprite borders while resizing the texture region.

## New built-in scripts
We added a few more built-in scripts with this release such as an FPS camera script and First player controller script. To use them, just click on “New Asset”, “Script source code”, select the desired script and attach it to an adequate entity.

<img src="http://doc.xenko.com/1.5/rn_images/built-in_Scripts.png" />

## Precompiled Sprite Fonts
Font rights are quite restrictive and it is quite common that only some persons of the project have access to the font files. This was preventing some people to build the game. 
To solve this problem, we created a new type of asset, the precompiled sprite fonts. It is an asset taking as input an image and containing all the glyph information required to render the set of character specified. Inside your games you can used it exactly like a standard sprite font.
To generate a precompiled sprite font, the owner of the original font file just have to right click on an existing static font and choose “Generate Precompiled Font”.

<img src="http://doc.xenko.com/1.5/rn_images/PrecompiledSpriteFont.png" />

# Version 1.5.0-beta
Release date: 2015/12/17


## Enhancements

### Launcher

- Add a ‘reconnect’ button, in case the launcher was started in offline mode.

### Game Studio

- The asset creation menu always displays all possible assets to create, and switches to a proper location when the currently selected location is invalid for the chosen asset type.
- Improve animation thumbnail and preview. Automatically detect and use the corresponding model.
- Improve asset filtering in the asset view. Filter tag can be added, disabled or removed at any time.
- Folders are displayed in the asset view.
- Assets can be sorted by last modification date.
- Add ability to copy/paste assets with their dependencies.
- Improve the sprite sheet editor. Resizing borders or moving the texture region behaves correctly, especially when reaching the borders of the image. Background outside of the selected texture region can be darkened.
- Sprite sheet preview can be displayed while the sprite sheet is being edited.
- Change message dialog style. Some confirmation dialogs (e.g. deleting an asset) can be disabled in the settings (under Interface/Ask confirmation…).

### Games

- Use the application icons as window icon on windows
- Use AssamblyProductAttribute.Product as window title on windows

### Graphics

- Add support for Gif load and jpeg save for Android
- Add the possibility to load images and textures as sRGB
- Add a static field in GraphicDevice to be able to get the current graphic platform
- Add optimized native code in SpriteBatch

### Engine

- Use Color4 instead of Color in sprite components.
- Add support for toot motion on the TransformComponent
- Expose AnimationComponent.PlayingAnimations to the editor to be able to set entity initial animation easily.
- Make connection to editor for shader compilation fail if there is no connection back within 5 seconds

### UI

- Add a tint color to the UI ImageElement.

## Issues fixed

### Assets

- Fix compiler regression that was taking more than 5s to complete compilation of assets
- Fix the log message displaying the name of missing referenced assets during asset compilation
- Fix crash in the asset compilation when Xenko installation path contains a '#' character.
- Fix shadow asset remaining after resolving asset naming collision.

### Engine

- Prevent an exception to be thrown at each frame when the Model property of a ModelComponent is null.
- Use the ShaderProfile from GameSettings instead of the graphic device level as it is likely the profile used to compile shaders at build time.

### Game Studio

- Fix a crash when trying to fetch the target asset of a reference that is null.
- Fix a bug in the edition of SpriteFont properties that was preventing to properly use system font
- Fix thumbnails of SpriteFont when using system font.
- Fix a crash when duplicating an entity in the scene editor.
- Fix renaming issue when duplicating an entity in the scene editor.
- Fix the problem dark thumbnails for textures in HDR mode.
- Fix gizmo settings not saved/reloaded properly.
- Fix copy/paste of folders in the solution explorer.
- Fix a crash in the sprite sheet editor when a source image was modified in an external editor.
- Fix a potential crash when the texture region is outside of the image.
- Fix a bug preventing to create a frame in the sprite editor when dropping a file.
- Fix a bug preventing to drop asset in an empty folder.
- Fix error when attempting to import animation from a model that doesn’t have any.
- Fix incorrect size of full screen window when screen resolution has changed.
- Fix package dependency issue when removing a dependent package.

### Rendering

- Fixed disappearing shadows due to wrong cascade distance calculation

# Breaking changes

# Known Issues

- iOS has an outstanding crash issue after a few second, especially on recent devices (iPhone 6s). This is currently under investigation.