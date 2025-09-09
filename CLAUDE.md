# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This project explores getting DCS (Digital Combat Simulator) working on Pop!_OS Linux with VR functionality using the Pico 4 headset. This is currently a research and experimentation project in its early stages.

## Repository Structure

The repository currently contains:
- `notes.txt` - Project objectives and initial notes
- `command-log.md` - Execution log of all commands run during setup
- `console-gui-plan.md` - Current plan for console GUI setup

## Development Status

This project is in active development focusing on dual display setup (RDP + console GUI) for VR gaming compatibility research. Current phase is establishing working console GUI session alongside existing RDP session.

## Command Logging Requirements

**IMPORTANT**: Claude Code MUST log ALL commands executed to `command-log.md` to maintain session continuity across crashes.

### Logging Format:
```bash
echo "# [Description of action] - $(date)" >> command-log.md
echo "[command executed]" >> command-log.md 
echo "# Result: [brief result description]" >> command-log.md
```

### Commands to Always Log:
- System state checks (ps, systemctl status, who, loginctl)
- Display manager operations (GDM, X server operations) 
- Session switching and environment testing
- VR application launches and GPU access tests
- Any command that modifies system state

## Project Context

The goal is to achieve VR gaming compatibility specifically for:
- DCS (Digital Combat Simulator)
- Pop!_OS Linux distribution
- Pico 4 VR headset integration

Future development will likely involve researching and implementing solutions for Linux VR gaming, potentially including Wine/Proton configurations, VR runtime setup, and hardware compatibility layers.