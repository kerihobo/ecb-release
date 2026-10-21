
# ECBrowser

ECBrowser is a Windows viewer for exploring the models, animations, scenes, maps, and media in a local PC installation of **FINAL FANTASY VII EVER CRISIS**. It lets you inspect game content in an interactive viewer and export supported assets for your own lawful use. It is an independent community tool and is not affiliated with or endorsed by the game's publisher.

## Gallery

<table>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/2f592f63-94ec-4312-b2e8-f88b9bf7c0cd" alt="Screenshot 1" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/6ea4e0af-2a9a-4c1a-8b95-914a7975b233" alt="Screenshot 2" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/867e093f-01fd-4b00-9442-f8dd334610c9" alt="Screenshot 3" width="320" /></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/59eff3eb-d6b0-4a16-a2b6-a5979b6832c9" alt="Screenshot 4" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/dcbd104f-5fa1-4d25-9af0-732106f08183" alt="Screenshot 5" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/a6f4b26a-7d3d-4553-bbbb-5f3add616470" alt="Screenshot 6" width="320" /></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/e40f30df-1f80-4428-b7d1-bf7510cdd098" alt="Screenshot 7" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/139651a7-43ad-4d5e-950d-ea2863d1ab60" alt="Screenshot 8" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/606d0c75-00fe-4ef6-9f62-537efc9bf99f" alt="Screenshot 9" width="320" /></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/948f46da-5e6a-4253-85f6-00c35f2eb1d7" alt="Screenshot 10" width="320" /></td>
    <td><img src="https://github.com/user-attachments/assets/fb9dd228-1729-4b39-be8c-4e90494ce5f6" alt="Screenshot 11" width="320" /></td>
    <td></td>
  </tr>
</table>

## What you can explore

- Characters, costumes, monsters, weapons, accessories, props, materials, and textures.
- Character actions and skills, with animation previews and localized skill names when the matching MasterData is available.
- Battle and environment scenes, including scene cameras, skyboxes, effects, collision outlines, and spawned characters. Arrange a scene, select character animations, and save or reload the scene setup.
- Dungeon maps, map scenes, and their Lua scripts.
- Sprites and UI images, plus standalone images, audio tracks, and videos.
- Story scripts and dialogue, with localized text and linked character information where data is available.
- Search across the asset catalogue, inspect bundle information, and generate thumbnails on your computer.

The viewer is still a work in progress. Some assets or labels may be missing, inconsistent, or incorrect, and some scenes may not behave exactly as they do in game. The project aims to make it practical to see models and animations and export supported content; it is not a complete game editor or a perfect recreation of the game.

## Download

Download the latest Windows build from the **Releases** page for this repository. The source project can also be opened with the Unity version recorded in `ProjectSettings/ProjectVersion.txt`.

ECBrowser does not include the game files. You need a working PC/Steam installation of FINAL FANTASY VII EVER CRISIS on the same computer. The app reads content from that installation, so it cannot show assets that are not present locally.

## First-time setup

On first launch, accept the usage notice and choose **EC installation**. Browse to the root of your game installation. For example:

```text
D:\SteamLibrary\steamapps\common\FINAL FANTASY VII EVER CRISIS
```

Choose the folder that contains `octo\v1` (and usually `FF7EC_Data`). Do not choose the `octo` folder or `FF7EC_Data` itself. In Steam, you can find this location from the game's **Manage → Browse local files** command.

Select **Build install cache** and let it finish, then save the choice. This builds a local index of the bundles installed on your machine; it does not modify the game installation. Rebuild the cache after a game update if content is missing. Bundles that have not been downloaded by the game are not available for ECBrowser to load.

### Documents MasterData

Choose the **Documents MasterData** folder separately in the content settings. The app can try to detect it, or you can browse to it. It is usually under your Windows Documents folder in a path like:

```text
C:\Users\<you>\Documents\My Games\FF7EC\Steam\<SteamID>\MasterData
```

Select the folder that directly contains `StoryEpisode.bin`. Its sibling `LocalizeText` folder should contain language folders such as `En`:

```text
...\<SteamID>\MasterData\StoryEpisode.bin
...\<SteamID>\LocalizeText\En\StoryEpisode.json
```

Replace `<you>` and `<SteamID>` with the names on your PC. The app can use MasterData inside the game installation as a fallback, but the Documents copy is preferred for localized names, story data, and related mappings.

An advanced **Custom Library** option is available for people who have already prepared a compatible library. It expects a parent folder containing `asset_bundles` and `bundle_dependency_index.json` (and can use `resources` for media). A Custom Library is not a substitute for the game installation unless it contains the content you want to browse.

## First launch and thumbnails

The app indexes a catalogue of about **112,000 bundle entries** when it starts. Let this initial indexing finish before expecting search and browsing to be fully ready. On the first run, ECBrowser also builds missing thumbnails from the locally installed content. That work can make the first load take a long time, especially on a large installation; keep the app open while it runs. Thumbnail generation continues in the background, prioritizes items currently visible in the tree, and saves its cache on your computer so later launches can reuse it. Some thumbnails may appear gradually as you browse.

## Using the viewer

Open **Asset Bundles** to search and browse the catalogue. Click a file to load it; expand folders to find related bundles. Use the **Show** filter to narrow the tree, and right-click a file or folder for actions such as export. The **Information** panel shows bundle details and load errors.

For models, drag to orbit, use the wheel to zoom, and middle-drag to pan. In scenes, use the scene camera controls and the **Cameras**, **Properties**, **Effects**, and **Skyboxes** panels. The `[` and `]` keys switch skyboxes. Select a scene character to choose its animation and weapons; save the scene to keep its setup for a later session.

Use the **Audio**, **Images**, and **Videos** browser tabs to view and play media. The story and dungeon panels show structured text and map data when the required content and MasterData are available.

## Export guide

Export actions are available from the relevant preview panels and from the asset tree's right-click menu. Exact options depend on the selected asset.

### Models, animations, and scenes

- **Model export:** `.gltf` or `.glb`, including supported meshes, skeletons, materials, and textures. Model export does not include animation clips.
- **Animation export:** `.gltf` or `.glb` with the model and eligible animation clips. Use the animation export action when you want clips included.
- **Texture storage:** choose a self-contained GLB or a glTF with external files, and choose whether textures are embedded or written as image files where offered.
- **Materials and textures only:** export the selected bundle's discovered materials and textures without exporting the model. Standalone builds write texture images and material-description JSON; the Unity Editor can also write native Unity assets.
- **Scene export:** glTF/GLB can include supported scene geometry, cameras, and lights, with collision geometry available as an option. In Unity Editor, an optional companion prefab and `.unitypackage` can preserve scene audio and particle systems for use in a compatible Unity project. Blender does not play those Unity audio sources or simulate those particle systems.

glTF/GLB export is **largely untested**, so inspect the result before relying on it. Blender can import `.gltf` and `.glb` using its glTF 2.0 add-on. To make animation selection easier:

1. In Blender, open **Edit → Preferences → Add-ons**, search for **glTF 2.0**, and enable the add-on's **Animation** UI/switcher option in its preferences.
2. Import the exported `.gltf` or `.glb`.
3. In the Dope Sheet, press **N** to open its sidebar. Use the animation switcher there to star/select the animation you want to play.

Blender may show the same named animation across multiple object tracks because an animation can affect several objects in the exported hierarchy. The add-on's animation switcher helps select the corresponding tracks together instead of toggling each one by hand. See the [Blender glTF 2.0 add-on manual](https://docs.blender.org/manual/en/latest/addons/scene_gltf2.html) for current importer options.

### Thumbnails and scene images

- **Thumbnail export:** save individual character, monster, quest-character, weapon, or accessory thumbnails as PNG. Options include size, pose, variant, background, and weapon attachment where available.
- **Thumbnail collages:** export multiple thumbnails as a sheet with configurable layout and spacing.
- **Scene image capture:** save a 16:9 PNG render of an environment scene using its camera and skybox, at one of the offered output widths.
- **Viewer capture:** use the capture control or `C` to save a PNG screenshot, with the configured background or transparency. Unity Editor Play Mode also offers video recording.

### Story, dungeon, and media exports

- **Story scripts:** export JSON, Excel `.xlsx`, and/or UTF-8 CSV. The export follows the selected story view and its filters/settings.
- **Dungeon Lua scripts:** export `.lua` files either stitched into one file per bundle or separated into individual text files. Localization tables can be included when present.
- **Audio:** export decoded audio as WAV.
- **Video:** export installed video as WebM, with options to include subtitles in the video, write `.srt` sidecar files, or omit subtitles.
- **Images:** copy image files in their original format. Folder exports can process supported media in batches while preserving folders.

## Legal and content note

Use ECBrowser only with game files you are legally entitled to access and process, and follow applicable laws and licence terms. ECBrowser does not grant rights to game content. Do not redistribute extracted game assets or other copyrighted material without permission or another lawful basis. The software is provided as-is, to the extent permitted by law. If you are a rights holder with a concern, please contact the project maintainers through this repository.
