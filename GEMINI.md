# Gemini Code Assistant Guidance

This document provides guidance for the Gemini code assistant when working with the `pico4dcslinux` repository.

## 1. Project Overview

This project aims to enable DCS (Digital Combat Simulator) VR gaming on Pop!_OS Linux using the Pico 4 VR headset. The goal is to research, implement, and document a stable and performant solution.

## 2. Current Development Status

**Phase 1: Research & Environment Setup - COMPLETE**

The initial research and environment setup phase is complete. Key achievements include:
- A complete end-to-end VR streaming infrastructure is operational.
- All necessary software components have been installed and configured:
    - **Wine-staging**: For running Windows applications (DCS).
    - **SteamVR**: As the primary VR platform.
    - **ALVR**: For wireless VR streaming to the Pico 4.
    - **Monado**: As the underlying OpenXR runtime.
- The Pico 4 headset connects successfully to the PC via ALVR.
- DCS World is installed within a Wine prefix.

**Current Blocker:** There is a known issue causing a black screen in the headset due to the SteamVR Linux Runtime Scout's sandboxing feature, which prevents the ALVR Vulkan layer from loading.

**Next Immediate Step:** Apply the documented fix for the SteamVR sandboxing issue.

## 3. Your Role and Primary Directives

Your primary role is to assist in completing the project's goals by providing technical support, writing code, and executing commands.

**Key Directives:**
- **Follow the Plan:** Adhere to the established implementation plans and action items. The project is well-documented; use the existing documents as your guide.
- **Consult Key Documents:** Before taking action, always refer to the following documents to understand the context and current status:
    - `docs/phase1-research-findings.md`: For the latest technical discoveries and status.
    - `docs/phase1-action-items.md`: For the immediate next steps.
    - `docs/phase1-implementation-plan.md`: For the detailed phase objectives.
    - `docs/PRD.md`: For the high-level project vision.
- **Prioritize the Blocker:** Your immediate priority is to resolve the current black screen issue by applying the fix identified in the research findings.
- **Execute Commands Safely:** When asked to run shell commands, explain the purpose of the command before execution, especially if it modifies the system or configuration.
- **Document Your Work:** If you make significant changes or discoveries, I may ask you to help update the relevant documentation, particularly the research findings.

## 4. Technical Focus Areas

- **Linux VR Ecosystem:** OpenXR, SteamVR, Monado, ALVR.
- **Windows Compatibility:** Wine/Proton, Winetricks, DXVK.
- **System Integration:** Pop!_OS/Ubuntu, NVIDIA drivers, udev rules, systemd.
- **Hardware:** Pico 4 headset, USB connectivity, wireless streaming.
- **DCS World:** Game-specific configurations and performance tuning.

## 5. How to Interact with Me

- I will provide you with specific tasks, often referencing the project's action items.
- I expect you to use the available tools to inspect the environment, modify files, and execute commands.
- When in doubt, ask for clarification. It is better to ask than to make an assumption that deviates from the project plan.
