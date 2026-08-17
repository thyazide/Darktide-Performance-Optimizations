
# Darktide Performance Optimizations

# Table of Contents

- [Mods](https://github.com/thyazide/Darktide-Performance-Optimizations#mods)
	- [Forward about mods](https://github.com/thyazide/Darktide-Performance-Optimizations#forward-about-mods)
	- [Mod installation instructions](https://github.com/thyazide/Darktide-Performance-Optimizations#mod-installation-instructions)
	- [Keeping mods up to date](https://github.com/thyazide/Darktide-Performance-Optimizations#keeping-mods-up-to-date)
	- [Commonly used Archive programs](https://github.com/thyazide/Darktide-Performance-Optimizations#commonly-used-archive-programs)\
	- [Config File Importing (optional)](https://github.com/thyazide/Darktide-Performance-Optimizations#config-file-importing-optional)
	- [Necessary Mods](https://github.com/thyazide/Darktide-Performance-Optimizations#necessary-mods)
	- [Lua Memory Management](https://github.com/thyazide/Darktide-Performance-Optimizations#lua-memory-management)
	- [Optional Mods](https://github.com/thyazide/Darktide-Performance-Optimizations/tree/main#optional-mods)
	- [Launcher Skip](https://github.com/thyazide/Darktide-Performance-Optimizations#launcher-skip)
- [INI & config file changes optimize the game engine](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#ini--config-file-changes-optimize-the-game-engine)
	- [`settings_common.ini`](https://github.com/thyazide/Darktide-Performance-Optimizations#settings_commonini)
	- [`win32_settings.ini`](https://github.com/thyazide/Darktide-Performance-Optimizations#win32_settingsini)
	- [`Launcher.exe.config`](https://github.com/thyazide/Darktide-Performance-Optimizations#launcherexeconfig)
- [Increase Nvidia Shader Cache Size](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#increase-nvidia-shader-cache-size)
- [Nvidia App Settings](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#nvidia-app-settings)
- [AMD Software: Adrenalin Edition software settings](https://github.com/thyazide/Darktide-Performance-Optimizations#amd-software-adrenalin-edition-software-settings)
	- [Tessellation Mode setting](https://github.com/thyazide/Darktide-Performance-Optimizations#tessellation-mode-setting)
	- [Enable FSR Redstone](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#enable-fsr-redstone)
- [Additional Linux Optimizations](https://github.com/thyazide/Darktide-Performance-Optimizations#additional-linux-optimizations)
- [In-Game settings](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#in-game-settings)
- [Restore defaults for `application_settings`, and `Launcher.exe.config`](https://github.com/thyazide/Darktide-Performance-Optimizations#restore-defaults-for-application_settings-and-launcherexeconfig)
- [File locations](https://github.com/thyazide/Darktide-Performance-Optimizations#file-locations)
- [Using DDU to cleanly remove and reinstall your drivers](https://github.com/thyazide/Darktide-Performance-Optimizations?tab=readme-ov-file#using-ddu-to-cleanly-remove-and-reinstall-your-drivers)
- [List of attributions](https://github.com/thyazide/Darktide-Performance-Optimizations#list-of-attributions)

# Mods
## Forward about mods

Mods are not required, but are highly advisable as they can provide a sizable performance gain over all. You can skip them and go directly to the INI edits and other changes in this document. Though as I advise their use, instructions for installing/enabling them are front and center. 
## Mod installation instructions

These instructions are fairly abstract as the programs you can use to extract the archives and the operating systems individuals choose to use are varied. Though it should be easy enough to follow if you are somewhat familiar with the process of extracting archives. If you have any questions or issue please feel free to contact me either through [Github](https://github.com/thyazide/Darktide-Performance-Optimizations/issues), or via the [Darktide Discord](https://discord.gg/darktide), or the [Darktide Modding Discord](<https://discord.gg/rKYWtaDx4D>).

There are other ways of handling mod support in Darktide, [Vortex](https://www.nexusmods.com/about/vortex) for example, can be used to install and manage mods, this is simply the way I handle them personally. 

**Instructions:**

1. Create a [Nexus Mods Account](https://users.nexusmods.com/register), or not, downloads will be slower and capped if you do not. 

	- Download [Darktide Mod Loader](https://www.nexusmods.com/warhammer40kdarktide/mods/19) (referred to as DML from here on out).
	- Download [Darktide Mod Framework](https://www.nexusmods.com/warhammer40kdarktide/mods/8) (referred to as DMF from here on out).
	- Download [Auto Mod Loading and Ordering](https://www.nexusmods.com/warhammer40kdarktide/mods/246) (referred to as AML from here on out).

2. Use the [Archive program of your choice](https://github.com/thyazide/Darktide-Performance-Optimizations#commonly-used-archive-programs) to extract DML to your Darktide folder:

	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`

3. Extract DMF to: 

	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\`

4. Extract AML to: 

	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\`

	Tell your archive program to overwrite any existing files, as AML is a patch for DML that enables mods to be automatically loaded by the game on start up. 

5. To enable mods after installing DMF, DML, and AML open the Darktide folder:

	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`

	Then double click the `toggle_darktide_mods.bat`, this will enable mods. This will need to be repeated after each patch to re-enable mods. Also if you need to disable mods at any time you can double click the batch file again and follow the on screen prompt to disable them. 

6. Once mods are enabled, you can extract any mods you wish into the mods folder: 

	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\`

	They will be automatically sorted and listed in the game's of the mod settings page. 

**AML notes:**

If DML is updated at any point after the initial install is finished you will need to download and extract AML into the mods folder to re-enable AML so mods can be loaded automatically. 

**Enable mods automatically after each patch Linux/Windows:** 

If you want to have mods automatically enabled after each update you can use [dtkit-patch](https://www.nexusmods.com/profile/manshanko/mods?gameId=4943) .

1. Extract the archive into the Darktide folder:
	 
	`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`
	
3. Make `toggle_dt_mod_autopatch.cmd` executable if you're using Linux. If you are on windows skip to the next step.
4. Then double click `toggle_dt_mod_autopatch.cmd`, or run the file from the terminal of your choice (Linux) to enable mods. 

Do this after finishing the instructions above for enabling mods.

- [DMF Docs official mod installation guide](https://dmf-docs.darkti.de/#/installing-mods) 
- [Install Darktide Mods Fast](https://youtu.be/xQtXFlxPiho) - **Video guide** 
## Keeping mods up to date

If you have opted to create a [Nexus Mods Account](https://users.nexusmods.com/register) your previous downloads will be tracked and tagged with a `check mark` to denote they have been downloaded. They will also display an `Update available` marker if they have been updated. You can then click on them and `download > extract them` to the mods folder, `overwriting the existing files`. You can make a bookmark in your browser [for this page](https://www.nexusmods.com/games/warhammer40kdarktide/mods?timeRange=14&sort=updatedAt). It will show you any mods that have been updated in the last two weeks. This is extremely helpful at times when large game updates are released. It also shows a list of mods that were added to the site within that same period. 
## Commonly used Archive programs

- [Winrar](https://www.win-rar.com/download.html?&L=0)
- [Peazip](https://peazip.github.io/)
- [7-Zip](https://www.7-zip.org/download.html)
- [Windows native extraction](https://support.microsoft.com/en-us/windows/zip-and-unzip-files-8d28fa72-f2f9-712f-67df-f80cf89fd4e5)
- [Ark for KDE](https://apps.kde.org/ark/)
- [File-Roller for Gnome](https://flathub.org/en/apps/org.gnome.FileRoller)
## Config File Importing (optional)

[Darktide Mod Settings Editor](https://www.nexusmods.com/warhammer40kdarktide/mods/989) - A lightweight, standalone Windows app for editing the mod settings stored in your Fatshark user_settings.config — no more hand-editing SJSON and hoping you didn't break the file.

**Usage**
1. Extract to the darktide folder `*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`
2. Start the mod editor by opening `DarktideModEditor 989 1.0.1 2026-07-06T18-40Z EGv9eGJBy.exe`
3. In the upper right click `Open...`
4. Find the folder `*/users/steamuser/AppData/Roaming/Fatshark/Darktide/` in Windows this is usually located on drive `C:\`
5. Open the file `user_settings.config`
6. You should see the left side populate with any mods you have installed that already have confgurations created. You can click through them and make changes. Then save those changes by clicking the `Save` button at the top. 
7. You can Import settings as well from the settings I've provided here: 

- https://github.com/thyazide/Darktide-Performance-Optimizations/tree/main/modconfigchunks

8. Right click on the .config files on the list and click `Save Link As...` or whatever equivent your browser uses. These instructions are based on Firefox for reference.
9. Once you have saved the `.config` files you wish to import, go back to the settings editor window and click `Import` then find the `.configs` you saved and import them.
10. Once you're done editing/importing, click `Save`

I've linked to the specific `.config` files I created for each mod that has one in the mods section as `Config file export` you can right click on them choose `Save Link As...` to download them individually. 

**Linux**

This works with Wine in Linux as well, you'll need to find your pfx folder for darktide:
`*/SteamLibrary/steamapps/compatdata/1361210/pfx/drive_c/users/steamuser/AppData/Roaming/Fatshark/Darktide/`

Then follow the usage instructions above. 
## Necessary Mods

[Impact VFX Limiter](https://www.nexusmods.com/warhammer40kdarktide/mods/424) - Allows the user to limit the maximum amount of flesh/armor impact VFX and surface impact VFX that can be played per frame for better performance.  

Also allows the user to simplify the blood decal casting behavior and the VFX of enemy fire attacks to be more performance friendly.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/FXlimiter.export.config)

```
Set the limiter to 2.
```  

[VFX Swapper](https://www.nexusmods.com/warhammer40kdarktide/mods/678) - Default options are fine, this limits VFX in-game to help with frame rate and clarity.

[Less Dot](https://www.nexusmods.com/warhammer40kdarktide/mods/521) - This removes effects from enemy characters in-game that chew up a lot of resources thus improving frame rate. More importantly, it keeps framerate stable as large amounts of effects happening simultaneously tanks framerate.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/LessDoT.export.config) 

```
Set all settings to OFF.
```

[Clear Smoke](https://www.nexusmods.com/warhammer40kdarktide/mods/517) - Keep default settings. This removes the smoke effect from veteran grenades and replaces it with an area marker.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/clear_smoke.export.config) 

[I Wanna See](https://www.nexusmods.com/warhammer40kdarktide/mods/371) - Removes Psyker bubble fx, but retains the large circle on the ground. Also is able to remove a lot of effects that can hurt performance from the rest of the Psykers kit, fire, lighting etc.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/i_wanna_see.export.config)

I Wanna See
```
Remove Inferno Staff Effects = on
Remove Smite Lightning Effects = off
Remove Electro Staff Lightning Effects = off
Remove Zealot Flamer Effects = on
```

Psyker Shield Settings
```
Remove Psyker Shield Effects = on
Remove Psyker Shield Soudns = off
Display an AoE Radius on the Floor = on
Shield AoE Radius (red) = 0
Shield AoE Radius (green) = 0
Shield AoE Radius (blue) = 255
<display_shield_health> = on
```

[Clean Force Blocking](https://www.nexusmods.com/warhammer40kdarktide/mods/104) - Removes Psyker Shield VFX.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/CleanForceBlocking.export.config)

```
Remove Blocking Visual Effect = on
Remove Pushing Visual Effect = on
Remove Push Attack Visual Effect = on 
Remove Blocking Sound Effect = off
```


[Enemies Improved (Healthbars - Debuffs - Outlines and more)](https://www.nexusmods.com/warhammer40kdarktide/mods/809 ) - Highly customizable replacement for the visual indicators of debuffs, status effects, health bars of enemies. Along with a host of other nice to have features. You'll need this to replace the VFX removed by Less dot. 

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/enemies_improved.export.config)

[Alf's DMF (Mod Settings) Extensions](https://www.nexusmods.com/warhammer40kdarktide/mods/864) - Required for running Enemies Improved. 

## Lua Memory Management

>There are 4 memory management mods available. The first three listed here are stand alone, pick one of them and install it by itself. The 4th option has fixes for the game which maybe useful and it has its own lua memory managment bundle built in. You can install it and then disable its built in manager, either with my config file export, or by manually disabling it in the mod options menu. Then you can use the fixes, and another one of the first 3 memory management mods together. 


[Memory Leak Fix](https://www.nexusmods.com/warhammer40kdarktide/mods/406) - Helps by trimming the memory space used by mods to keep it from reaching critical mass as quickly and causing crashing.

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/MemLeakFix.export.config)

```
GC Pause Time = 1.0
GC step multiple = 5.0
```

[SMOG Cleaner](https://www.nexusmods.com/warhammer40kdarktide/mods/847) - Alternative to Memory Leak Fix, does the same job but in a different way. Considering MLF hasn't been updated since 01/25, this might be a better way moving forward provided it gets better support by the creator. 

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/SMOG.export.config)

[Fps_Cleaner_Memory_FpsDoctor_LuaHeapCleaner](https://www.nexusmods.com/warhammer40kdarktide/mods/932) - Yet Another memory leak 'fixing' mod. Please note only one of these types of mods should be used at any one time. 

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/FpsDoctor.export.config)

[Tertium Fixes](https://www.nexusmods.com/warhammer40kdarktide/mods/1187)- Client-side fixes for the problems that kept getting in the way: stuck menus, missed inputs, wrong HUD and talent info, leaked audio and effects, stale buff state, and avoidable Lua memory pressure. No balance changes or reduced visual/audio quality.

>This is the 4th of the memory leak cleaning mods. Though this one provides a lot of fixes for other things. You can simply run it by itself, but if you would like to run this in conjunction with one of the other lua memory mods above you can do so by disabling its in-built lua heap cleaning feature. My config file export for this mod has the lua heap cleaning disabled as I use one of the other listed mods. 

- [Config file export](https://github.com/thyazide/Darktide-Performance-Optimizations/blob/main/modconfigchunks/TertiumFixes.export.config)
## Optional Mods

[Zealot Fire Particle Swap](https://www.nexusmods.com/warhammer40kdarktide/mods/230) - Allows you to configure the particle effects for Zealot fire grenades to make them distinct from bomber grenades. 

```
Particle Type = Nurgle Goo
```

[More Graphics Options - Performance boost](https://www.nexusmods.com/warhammer40kdarktide/mods/236) - Possibly useful for users with minimum spec PCs. 

[Granular Settings](https://www.nexusmods.com/warhammer40kdarktide/mods/38) - Has no configurable settings in mod options. Allows for greater control of mouse speed, and FOV. The following was taken and reformatted from the Granular Settings page on nexus mods. 

| Setting                              | Values                                                                            |
| ------------------------------------ | --------------------------------------------------------------------------------- |
| set_look_scale                       | Sets all 3 sensitivity values to the same value. Valid values range from 0 to 10. |
| set_look_scale_ranged                | sets only ranged sensitivity.                                                     |
| set_look_scale_ranged_alternate_fire | Sets only alternate fire sensitivity.                                             |
| set_vertical_fov                     | Sets fov measured vertically. Valid values range from 0 to 180 exclusive.         |
| set_horizontal_fov                   | Sets fov measured horizontally. Valid values range from 0 to 180 exclusive.       |

Commands are entered into the system via the chat dialog box.

	Example: 
	/set_look_scale 0.394
	/set_look_scale_ranged_alternate_fire 0.394 

**Recommendations:**
Use the same sensitivity value for all 3 sliders. The game correctly scales sensitivity by the tangent of `FOV/2` by default. This is opposed to many games simply scaling by `FOV/2`. Zoom is the ratio of focal lengths, not fields of view. Scaling sensitivity by the tangent of `FOV/2` properly emulates the ratio of focal lengths.

[Clean Kills](https://www.nexusmods.com/warhammer40kdarktide/mods/979) - Removes corpses for higher fps. Good for minimum spec PCs. 
## Launcher Skip

[Launcher Skip](https://www.nexusmods.com/warhammer40kdarktide/mods/131) - instructions for usage taken from the nexus mods page, reformatted for clarity, below.

Note:  `LauncherSkip.exe` will not try to start Steam/Game Pass for you so ensure they are already running before attempting to start the game. 

**Installation:**
1. Right-click `LauncherSkip.exe` > `click copy` then `paste` into your launcher folder. By default it is stored in:
- Steam:   
`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\launcher` 
-  Game Pass:   
`*\XboxGames\Warhammer 40,000- Darktide\Content\launcher`

2. Create shortcut/s:  
	Right-click `LauncherSkip.exe` in the launcher folder and select (any or all) options:  
	- Start Menu: Pin to Start
	- Taskbar: Pin to Taskbar
	- Desktop: Send to > Desktop (Create Shortcut)  

**Replace Original Launcher:**

You can also replace the Original Launcher entirely, this will allow you to launch the game from Steam/Game Pass Launcher directly. 

1. Right click `Launcher.exe` 
2. Click `Rename`
3. Set the name to `Launcher-original.exe`
4. Right click `LauncherSkip.exe`
5. Click `Rename` 
6. Set the name to `Launcher.exe`

When you open the game from Steam/Game Pass Launcher it will open the game directly. You will need to re-do these steps after any updates as the original launcher will be restored by Fatshark. So I would recommend keeping a copy of the `LauncherSkip.exe` in a safe location so it can be moved back into the launcher folder and renamed later. 
# INI & config file changes optimize the game engine

Tabbing and spacing are important when editing these files or the game will not work. These changes will need to be reapplied after every game update. They need to be done manually, as these files are updated by Fatshark after each patch/hotfix. If something gets broken, you can always [run an integrity check on the game in Steam](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB), doing so will remove any changes you’ve made and disable mods. You’ll need to re-run the `toogle_darktide_mods.bat`, re-edit the INI files and the `launcher.exe.config` once the integrity check has completed. Or you can restore the original settings, they are included [here](https://github.com/thyazide/Darktide-Performance-Optimizations#default-settings-for-edited-files).  

These settings work for AMD and Nvidia users.
# `settings_common.ini`

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\bundle\application_settings`

Tabbing and spacing are important when editing these files or the game will not work. These changes will need to be reapplied after every game update. They need to be done manually, as these files are changed after each update by Fatshark.

The following settings were taken from a recent updates to Vizra's config (v3) on Vizra's Discord Server. 

Find and replace the `feedback_streamer_settings` and `streaming_buffer_size` settings with the settings below:

```
feedback_streamer_settings = {
	feedback_buffer_size = 4
	max_age_out_tiles_per_frame = 16 
	max_streaming_tiles_per_frame = 16 
	max_texture_pool_size = 1024
	max_write_feedback_threshold = 0.009
	min_write_feedback_threshold = 0.005
	staging_buffer_size = 4
	threaded_streamer = true
	tile_age_out_time_ms = 5000
	tile_staging_buffer_size = 128 
`````

```
streaming_buffer_size = 32
streaming_max_open_streams = 38 
streaming_texture_pool_size = 1024
surface_properties = "application_settings/global"
texture_streamer_settings = {
	streaming_buffer_size = 128 
	streaming_texture_pool_size = 1024 
```
# `win32_settings.ini`

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\bundle\application_settings/
```

Find and replace the following two lines with `win32_settings.ini`:

```
		fullscreen = true
```

```
	streaming_texture_pool_size = 1024
```
# `Launcher.exe.config`

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\launcher
```

This will extend the amount of memory available in game to mods.

Find and replace the `ExeArgs` lines with the settings below:

```
<setting name="ExeArgs" serializeAs="String">  
		<value>--bundle-dir ../bundle --ini settings --lua-heap-mb-size 2048</value>
```

**Linux - Generating the launcher.exe.config, and shader cache:**

The `Launcher.exe.config` file should be generated by running the darktide launcher at least once. Use the latest verison of Steam Proton at least once before swapping to another version of proton and the file should appear normally, then it can be edited. 

The shader cache is also generated at runtime of the launcher. Ensure that you run the launcher at least once before changing to antoher version of Proton. 

Swapping back to Steam Proton will always regenerate the shader cache and `Launcher.exe.config` file. If you do this, ensure that you re-apply the ExeArgs line above to increase the memory available to mods in-game. 

# Increase Nvidia Shader Cache Size 
[AMD Software: Adrenalin Edition software settings](https://github.com/thyazide/Darktide-Performance-Optimizations#amd-software-adrenalin-edition-software-settings)￼
In some instances increasing the `Nvidia Shader Cache Size` can assist with reducing or eliminating stuttering in games. 

Normally the `Nvidia Control Panel` can be found in the `Windows Control Panel`. If its not there, or not installed you can [grab it from here.](https://apps.microsoft.com/detail/9nf8h0h7wmlt?hl=en-US&gl=US) 

1. Right Click the `Windows Desktop`. 
2. Click `Show more options`.
3. Click `Nvidia Control Panel`. 
4. Click `Manage 3D settings` on the left of the `Nvidia Control Panel` window.
5. On the right Click on the `Global Settings` tab.
6. Below in the settings section find `Shader Cache Size`.
7. On the right change the setting to `100GB`. 
8. Click `Apply`.
9. Exit the `Nvidia Control Panel`.
10. Reboot.

Once enabled this will increase the amount of disk space that can be used to store shaders created/used by games for the Nvidia Drivers. It won't take up the whole `100GB` of storage space at once, but will only trim unused shaders once the cache hits the `100GB` limit. This should keep games from stuttering when loading shaders as the drivers are not having to re-cache them after each run of a different title. 
# Nvidia App Settings

The introduction of DLSS 4.5 cause FPS loss for GPUs below the 5000 series as it contains FP8 calculations. Those calculations don't run as efficiently on older Nvidia GPUs. Sticking to the older 4.0 model, `PRESET K`, if your card is below the 5000 series. 

I would highly recommend testing 4.0 vs 4.5 on your specific setup as the performance hit for the 4000 series may not be as large as the gains in visual fidelity. Nvidia has stated that the performance loss for the 5000 series is around 3% give or take. 

1. Open `Nvidia App` settings.
2. Click `Graphics` on the left. 
3. Under `Program Settings` find the list of games, scroll down and click `Warhammer 40k Darktide`.
4. On the right scroll down to the bottom of the list to `Driver Settings`. 
5. Find `DLSS Override - Model Presets`. 
6. To the right of `DLSS Override - Model Presets`, click `Global - Use 3d app settings`.
7. On the pop up window click `Latest` for 5000 series and up graphics cards.
   A) Or click `Custom` near the top of the pop up window. 
   B) To the right of `Super Resolution` click the on the drop down menu and choose `Preset K` off the list if you are using 4000 series and below. You can also choose `Preset L` or `Preset M.` They process the [output image differently.](https://www.digitalfoundry.net/features/dlss-4-5-preset-l-tested-how-good-can-a-4k-upscale-from-720p-look)
8. Click `Apply`.

- [Video Guide for 4.5 and beyond.](https://youtu.be/1lAMbO0saAw?t=44])

**Linux:**

You can add an environment variable to enable the DLSS 4.5 upgrade system wide so you don't need to add it to every title in steam. 

Open a `Terminal` window, for my purposes I'm using `Konsole` in `KDE`. 

1. Type `sudo nano /etc/environment`, or copy and paste the command and hit enter. 
2. Enter your sudo password.
3. Add a new line `PROTON_DLSS_UPGRADE=1`.
4. Save an exit the file.
5. Reboot.

After the reboot any title you run and enable `DLSS` in will automatically upgrade to `DLSS 4.5` with the default `Preset M`. More info on Passing additional settings on a per-game basis can be found on the [DXVK Wiki](https://github.com/jp7677/dxvk-nvapi/wiki/Passing-driver-settings). 

# AMD Software: Adrenalin Edition software settings
## Tessellation Mode setting

1. Open AMD Software: Adrenalin Edition
2. Click Gaming 
3. Click Darktide off the list of games
4. Scroll down to the `Advanced` section
5. Set `Tessellation Mode` to `Use Application Settings`
## Enable FSR Redstone 

**Windows:**

1. Open `AMD Software: Adrenalin Edition`
2. Click the `Gaming` tab at the top of the window. 
3. Below the `Gaming` tab click `Graphics` tab
4. On the `Graphics` menu find `Amd FSR Upscaling`, click the `Enable` toggle. 
5.  Find `AMD FSR Frame Generation`, click the click the `Enable` toggle. (If you have a 7000 or below card this will be missing.)

You can now close the `AMD Software: Adrenalin Edition`. In any game title you have that has `AMD FSR 3.1` enabled will now automatically enable `FSR Redstone`. If the game already supports `AMD FSR 4.1.X` or higher choose that option instead. 

**Linux:**

You can add an environment variable to enable the FSR4/Redstone upgrade system wide so you don't need to add it to every title in steam. 

Open a `Terminal` window, for my purposes I'm using `Konsole` in `KDE`. 

1. Type `sudo nano /etc/environment`, or copy and paste the command and hit enter. 
2. Enter your sudo password.
3. Add a new line `PROTON_FSR4_UPGRADE=1`, or `PROTON_FSR4_UPGRADE="4.1.1"`.
4. Save an exit the file.
5. Reboot.

After the reboot any title you run and enable `FSR 3.1` in will automatically upgrade to `FSR4/Redstone`. In Darktides video settings enable `FSR 4.1.1`. 

There is another way to enable this with out using environtment variables, see the next section for details. 

# Additional Linux Optimizations

These optimizations are for AMD Graphics cards with AMD Processors. Your mileage may vary using these with other processors/cards. 

Current systems specs:


```
OS: CachyOS x86_64
Kernel: Linux 7.1.8-1-cachyos
DE: KDE Plasma 6.7.4
CPU: AMD Ryzen 7 9800X3D (16) @ 5.27 GHz
GPU: AMD Radeon RX 9070 XT
Memory: 62.47 GiB
```

You can use the new `PROTON_USE_OPTISCALER=1` layer that is nested inside Proton-CachyOS to enable `NVIDIA Reflex` in Darktide. Install `proton-cachyos-11.0-20260703-slr-x86_64` or later using `Protonqt-up` or `Proton Plus`. Then select the new proton version in steam for your compatibility layer.

You'll have multiple choices for latency reduction using optiscaler:

- [low_latency_layer](https://github.com/Korthos-Software/low_latency_layer) - A C++23 implicit Vulkan layer that reduces click-to-photon latency by implementing both AMD and NVIDIA's latency reduction technologies.
- [Xe Low Latency (XeLL)](https://github.com/intel/xess) - Minimizes input lag for a more responsive gaming experience; available on discrete and integrated Intel® Arc™ GPUs, as well as non-Intel GPUs when combined with XeSS-FG.
- [Latecy Flex](https://github.com/ishitatsuyuki/LatencyFleX) - Vendor agnostic latency reduction middleware. An alternative to NVIDIA Reflex.

`Low Latency Layer` is implemeneted directly into the mesa drivers for amd and intel gpus on linux via this command: `ENABLE_LAYER_MESA_ANTI_LAG=1` If this is not in your launch options or environment variables then the layer will be off by default. When not enabled, optiscaler will default to using XeLL. Or you can set the "Force LatencyFlex" setting in optiscaler to use LatencyFlex. I've included screenshots links with the launch options below 

- [Low Latency Layer](/images/Optiscaler-antilag2.png) launch options:
```
PROTON_FSR4_INDICATOR=1 ENABLE_LAYER_MESA_ANTI_LAG=1 PROTON_USE_OPTISCALER=1 PROTON_FSR4_UPGRADE="4.1.1" PROTON_ENABLE_WAYLAND=1 %command%
```

- [XeLL](/images/Optiscaler-Xell.png) and [LatencyFlex](/images/Optiscaler-latencyflex.png) launch options: 
```
PROTON_FSR4_INDICATOR=1 PROTON_USE_OPTISCALER=1 PROTON_FSR4_UPGRADE="4.1.1" PROTON_ENABLE_WAYLAND=1 %command%
```

For any of the configuration types open the VRR Frame Cap Calculator and click `Set as FPS Limit` then click `Apply Limit`. This is important as it helps to properly pace frames going out to your monitor using VRR. Then save settings at the bottom fo the Optiscaler window. 

Change the `FOV & Camera Values` adjust the `Vert. FOV` to the value you use in game. 

`PROTON_ENABLE_WAYLAND=1` Disables steam input and the steam overlay. Remove this if you need to use steam input. The game itself has its own friends list where you can invite people to party, or you can alt+tab to the steam friends list on the desktop to send invites there. This will help increase framerate and 1% lows in game as well as lower latency.

**In-Game Video Options:**
1. Hit Escape 
2. Open `Options` 
3. Open `Video` 
4. Set `Nvidia DLSS` to `OFF` 
5. Set `Nvidia Reflex Low Latency` to `Enabled + BOOST` 
6. Set `AMD FSR Upscaling Performance` to whatever level you are comfortable with. I use Performance. 
7. Set `FSR Upscaling Version` to `4.1.1 *`

`PROTON_FSR4_INDICATOR=1` Shows proof that the upscaler is using 4.1.1. (using the Psykhanium, or the hub. Once you are satisfied that things are working correctly in game. You can remove it from the launch options. 

**Scheduler changes**

I would also recommend using something like [Falcond-gui](https://github.com/PikaOS-Linux/falcond), or [sched-ext](https://wiki.cachyos.org/configuration/sched-ext/) to swap schedulers, currently I'm using [cosmos](https://wiki.cachyos.org/configuration/sched-ext/#scx_cosmos). Configured these settings using Falcond-gui: 

![Falcond-gui](/images/Falcond-darktide-config.png)

If you are on CachyOS you can use `Sched-Ext GUI Manager` with these options:

```
scx_cosmos
Gaming
-c 0 -p 0
```

![Schext-gui](/images/Schext-gui.png)

# In-Game settings

**Nvidia:**
Resolution should be set to whatever you use. You can use whatever setting for up-scaling is available, looks best, and provides the best performance for you. `Automatic` will change the internal render resolution dynamically, though it may cause stuttering. I use `performance` at 4K and it runs well and looks good. 

If your card has the option to enable `Nvidia Reflex+Boost` do so. 

**AMD Radeon:**
On AMD Radeon Based system enable `FSR 3.1` under the `Performance` section and set it to your desired upscaling setting. I use `Performance` on my 9070XT at 4k and it looks good and runs well. Though I would recommend finding the specific setting that works best for your hardware and has the desired fidelity. 

```
Framerate Cap = unlimited
Raytraced Reflections = off
RTX Global Illumination = off
Texture Quality = high
Mesh Quality = 2.0
Ambient Occlusion Quality = low
Lighting Quality = extreme
Volumetric Fog Quality = medium
Depth of Field = off
Global Illumination = high
Bloom = on
Skin Sub-surface Scattering = on
Motion Blur = off
Screen Space Reflections = off
Lens Quality = off (turns off all below it)
Lens Flares  = off
Scatter Density = 0.00
Max Ragdolls = 12
Max Weapon Impact decals = 15
Max Blood Decals = 25
Decal Lifetime = 30
Blood Decals = on
Gibbing = on
Enemy Wounds = on
Ragdoll Interactions = on
```

## Restore defaults for `application_settings`, and `Launcher.exe.config`

1. Open your Steam Library 
2. right-click Warhammer 40,000 Darktide
3. Click `Properties`
4. Click `Installed Files` on the left menu 
5. Click `Verify integrity of game files` on the right

This will remove the DMF changes that enable mods, so you will need to renable them. You will also need to re-edit the ini files, and the `Launcher.exe.config` as new copies of these files will be created.  
# File locations

You can open the Darktide base folder via the steam library:
1. Open Steam 
2. Click Library at the top of the page
3. On the left in your list of games, right-click on "Warhammer 40,000: Darktide"
4. Click Properties
5. Click Installed files 
6. On the right, click "Browse"

Darktide base folder: 

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\
```
- Default installation folder for Steam.  
- Location of `toggle_darktide_mods.bat` and `toggle_dt_mod_autopatch.cmd`

Darktide Launcher folder: 

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\launcher\
```
- The game launcher folder. 
- Location of `Launcher.exe.config`

Darktide mods folder:

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\
```
- Mod folders/files.

Darktide application_settings folder: 

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\bundle\application_settings\
```
- Stores INI files that govern settings for the game engine. 
- Location of `Settings_common.ini` and `Win32_settings.ini`.

# Using DDU to cleanly remove and reinstall your drivers

Using DDU (Display Driver Uninstaller) can help you cleanly remove the AMD, NVIDIA, and Intel display drivers from the system. This can help if you are having issues with crashing related to your GPU Drivers themselves. If you choose to use DDU, you will need to re-enable the [shader cache changes](https://github.com/thyazide/Darktide-Performance-Optimizations#increase-nvidia-shader-cache-size) (if you've made them) within the Nvidia Drivers. 

- [DDU Download Page.](https://www.guru3d.com/download/display-driver-uninstaller-download/)
- [The DDU Usage tutorial from the developers website.](https://www.wagnardsoft.com/content/How-use-Display-Driver-Uninstaller-DDU-Guide-Tutorial)

# List of attributions

Some attributions may not appear within the body of the document as I have time to write my own version of them. I am keeping them here for posterity.

- [How to fix AMD GPU stutters and improve clarity | Streaming settings config fix - Performance Feedback - Fatshark Forums](https://forums.fatsharkgames.com/t/how-to-fix-amd-gpu-stutters-and-improve-clarirty-streaming-settings-config-fix/108373) -Vizra
- [Fullscreen Optimizations are not enabled for Darktide (fix included) - Performance Feedback - Fatshark Forums](https://forums.fatsharkgames.com/t/fullscreen-optimisations-are-not-enabled-for-darktide-fix-included/103471) -Vizra
- [I fixed stutter and textures not loading in! (Texutre streaming config file change)](https://forums.fatsharkgames.com/t/i-fixed-stutter-and-textures-not-loading-in-texutre-streaming-config-file-change/102199) -Vizra
- [Better FPS & Graphic Options - Darktide Performance Guide](https://www.youtube.com/watch?v=tJ11KfVsG_c) -ItalianSpartacus
- [Darktide modding Discord](https://discord.gg/rKYWtaDx4D)
- [DMF Docs official mod installation guide](https://dmf-docs.darkti.de/#/installing-mods)
- [Guide for installing Darktide mods from /u/ruderalis1 on reddit.](https://old.reddit.com/r/DarkTide/comments/11cod2i/guide_how_to_install_mods_in_darktide_w_gifs/) -ruderalis1
- [Install Darktide Mods Fast](https://youtu.be/xQtXFlxPiho) -Janotil
- [Darktide Mod Loader](https://www.nexusmods.com/warhammer40kdarktide/mods/19) -Aussiemon
- [Darktide Mod Framework](https://www.nexusmods.com/warhammer40kdarktide/mods/8) -Aussiemon
- [Auto Mod Loading and Ordering](https://www.nexusmods.com/warhammer40kdarktide/mods/246) -Altarion
- [Impact VFX Limiter](https://www.nexusmods.com/warhammer40kdarktide/mods/424) -fugsystem
- [Less Dot](https://www.nexusmods.com/warhammer40kdarktide/mods/521) -SanctionedPsyker
- [Clear Smoke](https://www.nexusmods.com/warhammer40kdarktide/mods/517) -leerH
- [I Wanna See](https://www.nexusmods.com/warhammer40kdarktide/mods/371) -d3fallt
- [Memory Leak Fix](https://www.nexusmods.com/warhammer40kdarktide/mods/406) -PaimonKawaii
- [Clean Force Blocking](https://www.nexusmods.com/warhammer40kdarktide/mods/104) -deluxghost
- [Debuff Indicator](https://www.nexusmods.com/warhammer40kdarktide/mods/137) -Zombine04
- [Granular Settings](https://www.nexusmods.com/warhammer40kdarktide/mods/38) -Skwuruhl
- [Zealot Fire Particle Swap](https://www.nexusmods.com/warhammer40kdarktide/mods/230) -JCaleb
- Direct storage DLL update -pttgo
- [More Graphics Options - Performance boost](https://www.nexusmods.com/warhammer40kdarktide/mods/236) -yakuzadeso
- [Winrar](https://www.win-rar.com/download.html?&L=0)
- [Peazip](https://peazip.github.io/)
- [7-Zip](https://www.7-zip.org/download.html)
- [Windows native extraction](https://support.microsoft.com/en-us/windows/zip-and-unzip-files-8d28fa72-f2f9-712f-67df-f80cf89fd4e5)
- [Ark for KDE](https://apps.kde.org/ark/)
- [File-Roller for Gnome](https://flathub.org/en/apps/org.gnome.FileRoller)
- [Direct Storage Nupkg](https://www.nuget.org/packages/Microsoft.Direct3D.DirectStorage)
- [dtkit-patch](https://www.nexusmods.com/profile/manshanko/mods?gameId=4943) - manshanko
- [How to Enable Dlss 4.5 - Huge Visual Upgrade](https://www.youtube.com/watch?v=1lAMbO0saAw) -Benchmark Boy
- [VFX Swapper](https://www.nexusmods.com/warhammer40kdarktide/mods/678) -tdopz, with original mod credit going to leerH
- [NoCorpses](https://www.nexusmods.com/warhammer40kdarktide/mods/689) -7878949696
- [Nvidia Control Panel](https://apps.microsoft.com/detail/9nf8h0h7wmlt?hl=en-US&gl=US) 
- [How-use-Display-Driver-Uninstaller-DDU-Guide-Tutorial](https://www.wagnardsoft.com/content/How-use-Display-Driver-Uninstaller-DDU-Guide-Tutorial) 
- [DDU Download Page.](https://www.guru3d.com/download/display-driver-uninstaller-download/)
- [Vizra's Darktide Configs](https://discord.gg/TE6YwF5sWQ)
- [Darktide Mod Autopatcher](https://www.nexusmods.com/warhammer40kdarktide/mods/709) -manshanko
- [Digital Foundry](https://www.digitalfoundry.net/features/dlss-4-5-preset-l-tested-how-good-can-a-4k-upscale-from-720p-look)
- [Alf's DMF (Mod Settings) Extensions](https://www.nexusmods.com/warhammer40kdarktide/mods/864)
- [Enemies Improved (Healthbars - Debuffs - Outlines and more)](https://www.nexusmods.com/warhammer40kdarktide/mods/809 ) -Alfthebigheaded
- [SMOG Cleaner](https://www.nexusmods.com/warhammer40kdarktide/mods/847) -xxBellatrix
- [Fps_Cleaner_Memory_FpsDoctor_LuaHeapCleaner](https://www.nexusmods.com/warhammer40kdarktide/mods/932) -Artem228337
- [Clean kills](https://www.nexusmods.com/warhammer40kdarktide/mods/979) -marnhorn
- [Falcond-gui](https://github.com/PikaOS-Linux/falcond)
- [sched-ext](https://wiki.cachyos.org/configuration/sched-ext/) 
- [cosmos](https://wiki.cachyos.org/configuration/sched-ext/#scx_cosmos)
- [low_latency_layer.](https://github.com/Korthos-Software/low_latency_layer#low_latency_layer)
- [Darktide Mod Settings Editor](https://www.nexusmods.com/warhammer40kdarktide/mods/989) - iboxful
- [Tertium Fixes](https://www.nexusmods.com/warhammer40kdarktide/mods/1187) -Chronos

Thank you to everyone on this list, without their hard work and dedication this document would not be possible. 
