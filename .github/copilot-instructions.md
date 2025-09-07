# GitHub Copilot Instructions

## Project Context

This project enables DCS (Digital Combat Simulator) VR gaming on Pop!_OS Linux with Pico 4 headset support. Focus on Linux VR compatibility, Wine/Proton integration, and hardware driver configuration.

## Code Style and Standards

- **Shell Scripts**: Use bash with proper error handling (`set -euo pipefail`)
- **Documentation**: Clear, step-by-step instructions for technical setup
- **Configuration Files**: Well-commented with inline explanations
- **Error Messages**: Specific and actionable for troubleshooting

## Technical Focus Areas

### VR and Gaming
- OpenXR runtime configuration
- SteamVR integration patterns
- Wine/Proton VR compatibility layers
- GPU driver optimization for VR
- Frame rate monitoring and performance tuning

### Linux System Integration
- Pop!_OS/Ubuntu package management
- Systemd service configurations
- udev rules for VR hardware
- Graphics driver setup (NVIDIA/AMD)
- Audio routing for VR headsets

### Hardware Support
- USB device detection and permissions
- Pico 4 headset driver integration
- Controller mapping and calibration
- Tracking system configuration

## Issue and PR Guidelines

### Bug Reports
- Always include system information (OS version, GPU, kernel)
- VR-specific details: headset model, runtime version, SteamVR status
- DCS version and Wine/Proton version
- Performance metrics when applicable

### Feature Requests
- Focus on VR gaming compatibility improvements
- Consider cross-platform compatibility
- Include technical feasibility assessment
- Reference existing Linux VR solutions

### Documentation
- Prioritize setup automation and user-friendly guides
- Include troubleshooting sections
- Validate instructions on clean systems
- Add screenshots for complex configuration steps

## Security and Safety

- Never include personal Steam/DCS credentials
- Sanitize logs before sharing (remove usernames, paths)
- Use secure download methods for drivers and dependencies
- Validate checksums for critical VR runtime components

## Testing Approach

- Test on clean Pop!_OS installations when possible
- Document hardware configurations used for testing
- Include frame rate benchmarks for VR performance
- Test with different DCS modules and scenarios

## Community Focus

- Prioritize solutions that work for diverse hardware setups
- Consider users with different VR headsets beyond Pico 4
- Make setup accessible to Linux gaming newcomers
- Engage with broader Linux VR gaming community