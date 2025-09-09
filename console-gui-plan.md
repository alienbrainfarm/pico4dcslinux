# Console GUI Setup Plan

**Objective**: Get console GUI working on tty7 without breaking RDP session

## Current Status (Session Recovery Information)
- **RDP/VNC Session**: Running on localhost:10.0 (Xvnc :13) - WORKING
- **Console Session**: User logged in on tty7 (session 11) - Wayland session active
- **GDM3**: Running and managing both greeter (tty1) and user session (tty7)
- **NVIDIA GPU**: Accessible from console session (confirmed)

## Current Issue
Console GUI session shows up in `who` and `loginctl` but may not be displaying properly on physical console.

## Step-by-Step Plan

### Phase 1: Verify Console GUI Status
1. Check if console session is actually displaying on physical monitor
   - Use `sudo fgconsole` to confirm current console
   - Check if Ctrl+Alt+F7 switches to GUI session
   - Verify if monitor is connected and detected

### Phase 2: Console Display Investigation  
1. Check physical display connection
   - `ls /sys/class/drm/` - look for connected displays
   - `xrandr` from console session context
   - Check if system is running headless or has monitor

### Phase 3: Console Session Environment
1. Get proper display environment from tty7 session
   - Extract environment from process 22186 (gnome-session on tty7)
   - Test GUI applications in console context
   - Verify Wayland display is functional

### Phase 4: Test Console GUI Functionality
1. Launch test GUI application on console
   - Try `gnome-calculator` or similar
   - Test with proper session environment
   - Confirm GPU acceleration working

### Phase 5: Verify RDP Session Intact
1. Ensure RDP/VNC session remains unaffected
   - Test VNC connection still works
   - Verify applications still launch in RDP session
   - Confirm both sessions can coexist

## Fallback Options
- If console GUI doesn't work: Focus on RDP-based VR setup
- If displays conflict: Configure separate X servers for each session
- If Wayland issues: Switch console session to X11

## Success Criteria
- Console tty7 shows working GNOME desktop
- RDP session on localhost:10.0 continues working
- Both sessions can run GUI applications simultaneously
- NVIDIA GPU accessible from console session

## Commands to Execute (will be logged)
All commands will be logged to `command-log.md` as executed.

**Last Updated**: 2025-09-09 12:31 CEST