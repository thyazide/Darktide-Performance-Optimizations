# Virtual Display for Nobara, for use with Sunshine/Moonlight

We are going to use a hardware display out on the graphics card to create a virtual display. That means that we will be sacrificing the ability to plug a physical monitor into that slot in order to use it as a virtual display out for sunshine. Removing the `GRUB_CMDLINE_LINUX` changes we will install later from the `/etc/default/grub` file will remove the virtual display and allow physical hardware to be used in that port on the card. 

1. Find the name of a physical connector on your card you wish to use for the virtual display: 

This command prints the connectors available on your graphics card and their current state. 
```bash
for p in /sys/class/drm/*/status; do con=${p%/status}; echo -n "${con#*/card?-}: "; cat $p; done
```

This is the output for my 9070 xt.
```bash
DP-1: connected  
DP-2: connected  
DP-3: disconnected  
HDMI-A-1: disconnected  
Writeback-1: unknown
```

I'm going to use HDMI-A-1 for my virtual display leaving me with 3 display port (DP-1/2/3) connectors to use for physical monitors. Note I have 2 physical display port monitors connected, one disconnected and one disconnected HDMI. 

2. We need firmware!
	This is a [modified edid](https://github.com/Bloodhundur/steamdeckedid?tab=readme-ov-file) with added steam deck specific resolutions and refresh rates. It goes as high as 7860x4320 30hz, 4k at 120hz, etc. Whatever res you need its probably in there including HDR. You can clone the repository with this command. 
```bash
git clone https://github.com/Bloodhundur/steamdeckedid
```

3. Put the firmware in the folder.
```bash
cd steamdeckedid
sudo cp steamdeckedid /usr/lib/firmware/
```

4. Now that the firmware is in place we need to edit the grub config. 
```bash
sudo nano /etc/default/grub
```

Find the line `GRUB_CMDLINE_LINUX=` and add `firmware_class.path=/usr/local/lib/firmware drm.edid_firmware=HDMI-A-1:steamdeckedid video=HDMI-A-1:e` between the quotation marks. If there are other commands between the quotation marks simply add a space after the last command then paste the line in and make sure a quotation mark caps off the end of the command.  

*Example:

```bash
GRUB_CMDLINE_LINUX="firmware_class.path=/usr/local/lib/firmware drm.edid_firmware=HDMI-A-1:steamdeckedid.bin video=HDMI-A-1:e"
```

Exit out of nano and save changes `CTRL+X > Y > Enter`.

5. Update grub to incorporate the changes. 
```bash
sudo grub2-mkconfig -o /etc/grub2-efi.cfg && sudo grub2-mkconfig -o /etc/grub2.cfg
```

Now reboot, you should see the new display in `Settings > Display & Monitor > Display Configuration` in KDE. You can change the resolution and refresh rate and apply those changes even if the display is disabled. If you make changes in game, the virtual display should adjust to them properly and not produce black bars on your moonlight connected devices. 

Now we need to setup sunshine to disable your physical monitors and enable the virtual monitor, and vice versa when you end the stream. 
# Setup Sunshine for virtual display output. 

Right-click Sunshine icon in your tray and select "Open Sunshine" go to Configuration page. Once there click on the General tab and click + Add to put a "Do" and a "Undo Command".
## Explanation 

```
kscreen-doctor is a command-line tool for manipulating display settings on KDE Plasma desktops. It can enable/disable outputs, set rotation, scaling, resolution, refresh rate, position, and primary display status using a simple dot-notation syntax. Multiple output changes can be specified in a single command invocation. Changes take effect immediately without requiring a restart.
```

The command for enabling any physical connector on the video card is:
```
/usr/bin/kscreen-doctor output.<display connector>.enable
``` 

The command for disabling any physical connector on the video card is:
```
/usr/bin/kscreen-doctor output.<display connector>.disable
```

You'll need to construct your own do and undo commands. The ones below are examples of how my machine is setup. You can use `kscreen-doctor` to get the names of your display outputs. Run the command `kscreen-doctor -o | grep Output:`

```bash
··• kscreen-doctor -o | grep Output:  
Output: 1 DP-1 b663b323-648b-492f-8090-499a8ab70db9  
Output: 2 HDMI-A-1 26a1cf34-1dc6-4e0d-aff0-6e939f9c6f15  
Output: 3 DP-2 1e298e0e-3784-46af-ab11-68b477380276
```


# These are my example do and undo commands: 
## Do Command

Disables screens DP-1 and DP-2, and enables HDMI-A-1 where the virtual displays is tethered to the hardware HDMI port on my graphics card. 

```
/usr/bin/kscreen-doctor output.DP-1.disable && /usr/bin/kscreen-doctor output.DP-2.disable && /usr/bin/kscreen-doctor output.HDMI-A-1.enable
```

Adding `&&` between the commands runs the commands in sequence. So in human readable language the command says something like: DO - Turn off display port 1, and turn off display port 2, and turn on HDMI-A-1. 
## Undo Command

Re-enables DP-1 & DP-2 and Disables HDMI-A-1 (The virtual display.)

```
/usr/bin/kscreen-doctor output.DP-1.enable && /usr/bin/kscreen-doctor output.DP-2.enable && /usr/bin/kscreen-doctor output.HDMI-A-1.disable
```

This is the opposite command, its run when the stream ends: UNDO - Turn on display port 1, and turn on display port 2, and turn off HDMI-A-1. 

# Resources and links used to create this document:
https://gist.github.com/iamthenuggetman/6d0884954653940596d463a48b2f459c

https://github.com/Bloodhundur/steamdeckedid?tab=readme-ov-file

https://www.azdanov.dev/articles/2025/how-to-create-a-virtual-display-for-sunshine-on-arch-linux

https://edid.build/