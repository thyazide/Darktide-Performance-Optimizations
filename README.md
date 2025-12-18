# Darktide Performance Optimizations 

Mods are not required, but are highly advisable as they can provide a sizable performance gain over all. You can skip them and go directly to the INI edits and other changes in this document. Though as I advise their use,  instructions for installing/enabling them are front and center. 
# Mod installation instructions

These instructions are fairly abstract as the programs you can use to extract the archives and the operating systems individuals choose to use are varied. Though it should be easy enough to follow if you are somewhat familiar with the process of extracting archives. If you have any questions or issue please feel free to contact me either through [Github](https://github.com/thyazide/Darktide-Performance-Optimizations/issues), or via the [Darktide Discord](https://discord.gg/darktide), or the [Darktide Modding Discord]((<https://discord.gg/rKYWtaDx4D>).

There are other ways of handling mod support in Darktide, [Vortex](https://www.nexusmods.com/about/vortex) for example, can be used to install and manage mods, this is simply the way I handle them personally. 

**Instructions:**

Create a [Nexus Mods Account](https://users.nexusmods.com/register), or not, downloads will be slower and capped if you do not. 

Download [Darktide Mod Loader](https://www.nexusmods.com/warhammer40kdarktide/mods/19)

Download [Darktide Mod Framework](https://www.nexusmods.com/warhammer40kdarktide/mods/8)

Use the extraction program of your choice to extract Darktide Mod Loader (referred to as DML from here on out). To your Darktide folder:

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`

 Do the same with the Darktide Mod Framework (referred to as DML from here on out). Your Darktide folder: 

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`

Download [Auto Mod Loading and Ordering](https://www.nexusmods.com/warhammer40kdarktide/mods/246) (referred to as AML from here on out).

Extract it to the mods folder that was created by the DMF archive:

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\`

Tell your archive program to overwrite any existing files, as AML is a patch for DML that enables mods to be automatically loaded by the game on start up. 

Once AML is installed you can simply download and extract any mods you wish into the mods folder: 

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\mods\`

They will be automatically sorted and listed in the game's mod settings page. 

When DML is updated at any point after the initial install is finished you will need to download and re-apply AML in the mods folder to re-enable AML so mods can be loaded automatically. 

To enable mods after installing DMF, DML, and AML open the Darktide folder:

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`

Then double click the `toggle_darktide_mods.bat`, this will enable mods. This will need to be repeated after each patch to re-enable mods. Also if you need to disable mods at any time you can double click the batch file again and follow the on screen prompt to disable them. 

**Linux specific:** 
If you are on linux you can use [dtkit-patch](https://github.com/manshanko/dtkit-patch) to enable mods. Extract the archive into the Darktide folder (`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\`), make it executable. Then double click it, or run the file from the terminal of your choice to enable mods.  
# Commonly used Archive programs: 

[Winrar](https://www.win-rar.com/download.html?&L=0)
[Peazip](https://peazip.github.io/)
[7-Zip](https://www.7-zip.org/download.html)
[Windows native extraction](https://support.microsoft.com/en-us/windows/zip-and-unzip-files-8d28fa72-f2f9-712f-67df-f80cf89fd4e5)
[Ark for KDE](https://apps.kde.org/ark/)
[File-Roller for Gnome](https://flathub.org/en/apps/org.gnome.FileRoller)
# Necessary Mods

[Impact VFX Limiter](https://www.nexusmods.com/warhammer40kdarktide/mods/424) - Allows the user to limit the maximum amount of flesh/armor impact VFX and surface impact VFX that can be played per frame for better performance.  
  
Also allows the user to simplify the blood decal casting behavior and the VFX of enemy fire attacks to be more performance friendly.

```
Maximum impact effect per frame = 2
Performance Features set to = on
```

[VFX Limiter (grenades)](https://www.nexusmods.com/warhammer40kdarktide/mods/602) - Removes grenade effects, settings are personal preference.

[Less Dot](https://www.nexusmods.com/warhammer40kdarktide/mods/521) - This removes effects from enemy characters in-game that chew up a lot of resources thus improving frame rate. More importantly, it keeps framerate stable as large amounts of effects happening simultaneously tanks framerate.

```
Set all settings to OFF.
```

[Clear Smoke](https://www.nexusmods.com/warhammer40kdarktide/mods/517) - Keep default settings. This removes the smoke effect from veteran grenades and replaces it with an area marker.

[I Wanna See](https://www.nexusmods.com/warhammer40kdarktide/mods/371) - Removes Psyker bubble fx, but retains the large circle on the ground. Also is able to remove a lot of effects that can hurt performance from the rest of the Psykers kit, fire, lighting etc.

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

[Memory Leak Fix](https://www.nexusmods.com/warhammer40kdarktide/mods/406) - Helps by trimming the memory space used by mods to keep it from reaching critical mass as quickly and causing crashing.

```
GC Pause Time = 1.0
GC step multiple = 5.0
```

[Clean Force Blocking](https://www.nexusmods.com/warhammer40kdarktide/mods/104) - Removes Psyker shield vfx.

```
Remove Blocking Visual Effect = on
Remove Pushing Visual Effect = on
Remove Push Attack Visual Effect = on 
Remove Blocking Sound Effect = off
```

[Debuff Indicator](https://www.nexusmods.com/warhammer40kdarktide/mods/137) - User preference as there are multiple ways to set up how this mod displays itself in game. Needed as a replacement for the visual effects removed by less dot.

[Granular Settings](https://www.nexusmods.com/warhammer40kdarktide/mods/38) - Has no configurable settings in mod options. Allows for greater control over many aspects of the games settings. (*Optional mod.*)

[Zealot Fire Particle Swap](https://www.nexusmods.com/warhammer40kdarktide/mods/230) - Not really a performance enhancer but nice to have. (*Optional mod.*)

```
Particle Type = Nurgle Goo
```
# Launcher Skip 
[Launcher Skip](https://www.nexusmods.com/warhammer40kdarktide/mods/131) - instructions for usage taken from the nexus mods page below.

**Usage**
1. Copy LauncherSkip.exe to your launcher folder. By default:  
- Steam:   
`C:\Program Files (x86)\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\launcher` 
 
-  Game Pass:   
`C:\XboxGames\Warhammer 40,000- Darktide\Content\launcher`  
1. Create shortcut/s:  
  a) Right-click LauncherSkip.exe and select an option:  
	- Start menu: "Pin to Start"
	- Taskbar: "Pin to taskbar"
	- Desktop: "Send to" -> "Desktop (create shortcut)"  
 b) Copy LauncherSkip.exe, navigate to any folder, then right-click and select "Paste shortcut".  
It will not try to start Steam/Game Pass for you so they need to already be running. This is not a DMF mod and does not need to be copied to your mods folder.  

**Original launcher**

The original launcher has deliberately been left alone, so simply launch the game from Steam/Game Pass (without the shortcut) to view it.  
  
If you want to completely replace it, rename the original launcher to `Launcher-original.exe`, and `LauncherSkip.exe` to `Launcher.exe` (and replace any shortcuts to `LauncherSkip.exe`). You will need to redo this each time the game updates or you run "Verify integrity of game files" in Steam. 
# INI file edits to optimize the game engine

Tabbing and spacing are important when editing these files or the game will not work. These changes will need to be reapplied after every game update. They need to be done manually, as these files are updated by Fatshark after each patch/hotfix. If something gets broken, you can always [run an integrity check on the game in Steam](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB), doing so will remove any changes you’ve made and disable mods. You’ll need to re-run the `toogle_darktide_mods.bat`, re-edit the INI files and the `launcher.exe.config` once the integrity check has completed. Or you can restore the original settings, they are included at the [bottom of this document](https://github.com/thyazide/Darktide-Performance-Optimizations#original-settings-for-edited-files).  

These settings work for AMD and Nvidia users.
# Target file `Settings_common.ini`

`*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\bundle\application_settings`

Tabbing and spacing are important when editing these files or the game will not work. These changes will need to be reapplied after every game update. They need to be done manually, as these files are changed after each update by Fatshark.

By default `tile_staging_buffer_size` is set to `64` in the settings below. Values lower than 64 can cause rubbery looking textures on enemies until the texture fully loads. Here are suggestions for the value based on the amount of ram your card has. If your card has `16gb` of ram or higher you can use `16`, `32`, or `64`. 

Valid values for `tile_staging_buffer_size`: 

```
4, 8, 16, 32, 64
```

Here are some suggestions for values based on ram. You’ll need to adjust these settings based on your own experience in-game:

```
8gb can use tile_staging_buffer_size = 4  
10gb can use tile_staging_buffer_size = 8  
11gb can use tile_staging_buffer_size = 8  
12gb can use tile_staging_buffer_size = 16  
16gb can use tile_staging_buffer-_size = 64
```

You will need to correct the value for `tile_staging_buffer_size` after copying and pasting the values into the `Settings_common.ini`.

Find and replace the `feedback_streamer_settings` and `streaming_buffer_size` settings with the settings below:

```
feedback_streamer_settings = {  
        feedback_buffer_size = 16  
        max_age_out_tiles_per_frame = 16  
        max_streaming_tiles_per_frame = 16  
        max_texture_pool_size = 1024  
        max_write_feedback_threshold = 0.009  
        min_write_feedback_threshold = 0.005  
        staging_buffer_size = 8  
        threaded_streamer = true  
        tile_age_out_time_ms = 5000  
        tile_staging_buffer_size = 64  
  
streaming_buffer_size = 128  
streaming_max_open_streams = 32  
streaming_texture_pool_size = 1024  
surface_properties = "application_settings/global"  
texture_streamer_settings = {  
        streaming_buffer_size = 128  
        streaming_texture_pool_size = 1024
```
# Target file `Win32_settings.ini`

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\bundle\application_settings/
```

Find and replace the `renderer` settings with the settings below:

```
renderer = {  
               adapter_index = 0  
               aspect_ratio = -1  
               d3d_debug = false  
               d3d_gpu_validation = false  
               dlss_logging = 0  
               dred_pagefault = true  
               fullscreen = true  
               fullscreen_output = 0  
               gpu_crash_dumps = false  
               ray_tracing = true  
               screen_resolution = [ 1920 1080 ]
```
# Target file `Launcher.exe.config`

```
*\Steam\steamapps\common\Warhammer 40,000 DARKTIDE\launcher
```

This will extend the amount of memory- available in game to mods.

Find and replace the `ExeArgs` lines with the settings below:

```
<setting name="ExeArgs" serializeAs="String">  
       <value>--bundle-dir ../bundle --ini settings --lua-heap-mb-size 2048</value>
```
# Nvidia App Settings      

```
1. Open Nvidia App settings
2. Warhammer 40k darktide
3. Driver settings
4. DLSS Override - Model Presets    
5. Use different settings for each DLSS Technology
6. Super resolution
7. Latest
8. Click apply.
```

[Video Guide](https://youtu.be/0w7-N8y5b_k)
# In-Game settings

Resolution should be set to whatever you use. You can use whatever setting for up-scaling is available and looks best, and provides the best performance for you. Automatic will change the internal render resolution dynamically, though it may cause stuttering. I use performance at 4K and it runs well and looks good. 

If your card has the option to enable `Nvidia Reflex Low Latency` do so. 

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
# Original settings for edited files

Original settings from `win32_settings.ini`
```
renderer = {
        adapter_index = 0
        aspect_ratio = -1
        d3d_debug = false
        d3d_gpu_validation = false
        dlss_logging = 0
        dred_pagefault = true
        fullscreen = true
        fullscreen_output = 0
        gpu_crash_dumps = false
        ray_tracing = true
        screen_resolution = [ 1920 1080] 
        streaming_buffer_size = 64  
        streaming_texture_pool_size = 512
```

Original settings from `settings_common.ini` 
```
feedback_streamer_settings = {  
   feedback_buffer_size = 4  
   max_age_out_tiles_per_frame = 64  
   max_streaming_tiles_per_frame = 64  
   max_texture_pool_size = 1024  
   max_write_feedback_threshold = 0.009  
   min_write_feedback_threshold = 0.005  
   staging_buffer_size = 4  
   threaded_streamer = true  
   tile_age_out_time_ms = 5000  
   tile_staging_buffer_size = 4  

streaming_buffer_size = 32  
streaming_max_open_streams = 50  
streaming_texture_pool_size = 400  
surface_properties = "application_settings/global"  
texture_streamer_settings = {  
   streaming_buffer_size = 64  
   streaming_texture_pool_size = 512
```
# Direct Storage DLL Update 

Update the direct storage dll files

1. Download the [Direct Storage Nupkg](https://www.nuget.org/api/v2/package/Microsoft.Direct3D.DirectStorage/1.3.0)
2. Open it with [Peazip](https://peazip.github.io/index.html) 
3. Inside the archive open `/native/bin/x64/`
4. Extract `dstorage.dll` and `dstoragecore.dll` to some where you can locate it later
5. Open the darktide binaries folder `*/steam/steamapps/common/Warhammer 40,000 DARKTIDE/binaries/`
6. Find `dstoragecore.dll` and `dstorage.dll`, back them up else where in case you wish to undo these changes (or run a [file integrity verification in steam](https://help.steampowered.com/en/faqs/view/0C48-FCBD-DA71-93EB), note this will disable mods, so you will need to re-enable them using the batch file in the root darktide folder  `*/steam/steamapps/common/Warhammer 40,000 DARKTIDE/`).
7. Copy the `dstoragecore.dll` and `dstorage.dll` files from where you placed them earlier and place them into `*/steam/steamapps/common/Warhammer 40,000 DARKTIDE/binaries/`
# List of attributions

Some attributions may not appear within the body of the document as I have time to write my own version of them. I am keeping them here for posterity.

- [How to fix AMD GPU stutters and improve clarirty | Streaming settings config fix - Performance Feedback - Fatshark Forums](https://forums.fatsharkgames.com/t/how-to-fix-amd-gpu-stutters-and-improve-clarirty-streaming-settings-config-fix/108373) -Vizra
- [Fullscreen Optimisations are not enabled for Darktide (fix included) - Performance Feedback - Fatshark Forums](https://forums.fatsharkgames.com/t/fullscreen-optimisations-are-not-enabled-for-darktide-fix-included/103471) -Vizra
- [Better FPS & Graphic Options - Darktide Performance Guide](https://www.youtube.com/watch?v=tJ11KfVsG_c) -ItalianSpartacus
- [https://discord.gg/rKYWtaDx4D](https://discord.gg/rKYWtaDx4D) -Darktide modding Discord
- [Guide for installing darktide mods from /u/ruderalis1 on reddit.](https://old.reddit.com/r/DarkTide/comments/11cod2i/guide_how_to_install_mods_in_darktide_w_gifs/) -ruderalis1
- [Alternate guide for installing mods.](https://youtu.be/xQtXFlxPiho) -Janotil
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
- Direct storage dll update -pttgo