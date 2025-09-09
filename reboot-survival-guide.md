# Reboot Survival Guide - VNC + Console GUI Setup

**Last Updated**: 2025-09-09 15:03 CEST  
**Status**: Both VNC and Console GUI sessions working

## Current Working Setup Summary

### Services Running
- **GDM3**: `systemctl status gdm` - Display Manager for console GUI (static service)
- **XRDP**: `systemctl status xrdp` - RDP service for remote connections (enabled)

### Active Sessions
- **VNC Session**: User `swim` on `:10` (Xvnc process, 3440x1440)
- **Console GUI**: User `jpvr` on `tty7` (Xorg :0, physical display)

### Key Components
```bash
# X Servers Running
swim    5758  - Xvnc :10 (VNC session)
jpvr   14338  - Xorg :0 vt7 (Console GUI)

# Display Manager
root   13872  - /usr/sbin/gdm3

# User Sessions  
SESSION 16: jpvr on seat0/tty7 (Console GUI)
SESSION 7:  swim on pts/1 (SSH/VNC)
```

## What Survives Reboot Automatically

✅ **XRDP Service**: Enabled, will start automatically  
✅ **GDM3**: Static service, managed by systemd  
✅ **User jpvr**: Account exists with proper permissions  
✅ **DCS Installation**: Located at `/home/jpvr/wine-prefixes/dcs` (219GB)  

## What Requires Manual Restart After Reboot

❌ **VNC Session for user 'swim'**: Must be started manually  
❌ **Console Login for jpvr**: Must log in manually to tty7  
❌ **Wine/Steam Applications**: Must be launched manually  

## Step-by-Step Recovery Process

### 1. After Reboot - Verify Services
```bash
# Check that core services started
systemctl status gdm
systemctl status xrdp

# Should show both as "active (running)"
```

### 2. Re-establish VNC Session (if needed)
```bash
# SSH into system as user 'swim'
ssh swim@[your-system-ip]

# VNC should auto-start via xrdp when connecting with RDP client
# Connect to: [system-ip]:3389 (RDP protocol)
```

### 3. Console GUI Login
```bash
# Physical console access or switch to tty7
# Login as user: jpvr
# Password: [jpvr's password]

# Console should show GNOME desktop on physical display
```

### 4. Verify GPU Access
```bash
# From jpvr console session:
nvidia-smi  # Should show RTX 4090
glxinfo | head -5  # Should show OpenGL info
```

### 5. Start VR Applications
```bash
# From jpvr console session:
cd /home/jpvr/wine-prefixes/
WINEPREFIX=/home/jpvr/wine-prefixes/dcs wine /home/jpvr/wine-prefixes/dcs/drive_c/Program\ Files/Eagle\ Dynamics/DCS\ World/bin/DCS.exe
```

## Critical File Locations

### User Accounts
- **swim**: Primary user, owns VNC session and RDP access
- **jpvr**: VR user, owns console GUI and DCS installation

### DCS Installation
```bash
/home/jpvr/wine-prefixes/dcs/  # 219GB DCS Wine prefix
/home/jpvr/wine-prefixes/dcs/drive_c/Program Files/Eagle Dynamics/DCS World/
```

### System Configuration
```bash
/etc/X11/default-display-manager  # Points to /usr/sbin/gdm3
/lib/systemd/system/gdm.service   # GDM service definition
/lib/systemd/system/xrdp.service  # XRDP service definition
```

## Troubleshooting Common Issues

### Issue: No Console GUI After Reboot
```bash
# Check GDM status
systemctl status gdm

# If not running:
sudo systemctl start gdm

# If running but no display, check X server
ps aux | grep Xorg
```

### Issue: VNC/RDP Not Working
```bash
# Check XRDP service
systemctl status xrdp

# If not running:
sudo systemctl start xrdp

# Test VNC connection
vncviewer localhost:5910  # Direct VNC connection
```

### Issue: jpvr Cannot Access GPU
```bash
# From jpvr session, test GPU access:
nvidia-smi
# If fails, check user is in video group:
groups jpvr
# Should include 'video' group
```

### Issue: Console Shows Black Screen
```bash
# Switch between TTYs to recover:
Ctrl+Alt+F1  # Text console
Ctrl+Alt+F7  # GUI console (jpvr session)

# If still black, restart GDM:
sudo systemctl restart gdm
```

## Service Dependencies

```bash
# Service start order (important for reboot):
1. systemd-logind.service
2. gdm.service 
3. xrdp.service
4. User sessions (manual login)
```

## Network Access Points

- **RDP**: Port 3389 (primary remote access)  
- **SSH**: Port 22 (fallback remote access)  
- **VNC**: Port 5910 (direct VNC if needed)  

## Storage Requirements

- **System**: ~40GB for OS and applications
- **DCS**: 219GB at `/home/jpvr/wine-prefixes/dcs`
- **Free Space**: 580GB available (sufficient for updates)

## Commands to Log Everything

```bash
# Add to command-log.md after reboot recovery:
echo "# POST-REBOOT RECOVERY - $(date)" >> command-log.md
systemctl status gdm xrdp >> command-log.md
ps aux | grep -E "(Xorg|Xvnc)" >> command-log.md  
loginctl list-sessions >> command-log.md
echo "# Recovery completed successfully" >> command-log.md
```

## Emergency Recovery Mode

If GUI completely fails:
1. Boot to single user mode (hold Shift during boot, select recovery)
2. SSH access should still work: `ssh swim@[system-ip]`
3. Restart display services: `sudo systemctl restart gdm xrdp`
4. Check logs: `journalctl -u gdm -u xrdp --since "10 minutes ago"`

**Note**: Always test recovery procedures in non-critical scenarios first.