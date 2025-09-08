# Fixing the SteamVR Sandbox Issue on Linux

This document outlines the solution to a common issue on Linux where SteamVR displays a black screen in the VR headset.

## The Problem

When using SteamVR on Linux, the VR headset may show a black screen, even though the connection to the PC is stable and data is being streamed. This is often accompanied by a black settings window or other UI issues.

## The Cause

The issue is caused by the **SteamVR Linux Runtime Scout (SLR1) sandbox**. SteamVR runs its `vrcompositor` component within this sandbox for compatibility across different Linux distributions. However, this sandbox can prevent custom Vulkan layers from loading. These layers are essential for some VR applications and drivers, like ALVR, to intercept rendering commands and send them to the headset. Without the Vulkan layer, the rendered frames never reach the headset, resulting in a black screen.

## The Solution

The workaround is to partially disable the sandbox for `vrcompositor` to allow the necessary Vulkan layer to load. This is achieved by modifying the launch options for SteamVR.

### 1. Modify SteamVR's Launch Options

1.  Open the Steam client.
2.  Navigate to your **Library**.
3.  Find **SteamVR**, right-click on it, and select **Properties**.
4.  In the **General** tab, you will find a **Launch Options** text box.
5.  Prepend the following command to the launch options:

```
DRI_PRIME=1 /home/youruser/.steam/steam/steamapps/common/SteamVR/bin/vrmonitor.sh %command%
```

**Note:**
*   Replace `/home/youruser/` with the actual path to your home directory.
*   The `DRI_PRIME=1` part is used to select a specific GPU, which might be necessary for systems with multiple GPUs.
*   This command ensures that SteamVR launches outside the restrictive sandbox.

### 2. Update ALVR Launcher Configuration

If you are using ALVR, the ALVR launcher might warn you to put the same launch options (including `DRI_PRIME=1`) into both the SteamVR and your game launchers.

### 3. Clean Configuration Files (Optional)

If you are also experiencing a black settings window or other UI issues, it might be helpful to delete the following files and folders and then restart Steam:

*   `~/.local/share/Steam/config/vrappconfig` (folder)
*   `~/.local/share/Steam/config/steamvr.vrsettings` (file)

## Community Tips

*   **Double-check file paths:** Ensure that the path in your launch options is correct for your system.
*   **Consider the AppImage version of ALVR:** Some users have found that the AppImage version of ALVR works more reliably than distro packages or AUR builds.
