# Phase 1 Research Findings

## Research Status: Initial Investigation

This document captures research findings for Phase 1 of the Pico 4 DCS Linux project. Research is ongoing and this document will be updated as findings are gathered.

## Linux VR Ecosystem Analysis

### OpenXR Runtime Options

#### Monado - Open Source OpenXR Runtime
- **Status**: Active development, supports various headsets
- **Pico 4 Support**: Limited official support, community drivers possible
- **Pros**: Open source, actively maintained, designed for Linux
- **Cons**: Limited headset support, complex setup
- **Compatibility**: Good integration with Mesa drivers

#### SteamVR for Linux
- **Status**: Officially discontinued by Valve (2019)
- **Current State**: Some legacy functionality remains
- **Pico 4 Support**: None (requires workarounds)
- **Pros**: Mature VR platform, good game compatibility
- **Cons**: Discontinued, no official support

#### OpenComposite
- **Status**: Community project for OpenVR to OpenXR translation
- **Use Case**: Bridge between Steam VR games and OpenXR runtimes
- **Compatibility**: May enable some VR games to work with Monado

### Pico 4 Linux Compatibility

#### ALVR (Air Light VR)
- **Status**: Open source wireless VR streaming
- **Pico 4 Support**: Community support through Android APK
- **Pros**: Wireless operation, active community
- **Cons**: Latency concerns, requires WiFi 6 for best performance

#### OpenHMD
- **Status**: Open source HMD drivers
- **Pico 4 Support**: Limited, primarily older headsets
- **Future**: May add Pico 4 support with community effort

#### USB Connectivity
- **Pico 4 Link Cable**: Official cable support unknown on Linux
- **ADB Integration**: Android Debug Bridge for development access
- **USB HID**: Standard input device recognition

## DCS World Linux Compatibility

### Wine/Proton Status

#### DCS World on ProtonDB
- **Overall Rating**: Bronze (some tweaking required)
- **VR Status**: Limited reports, mostly negative for VR
- **Common Issues**: 
  - Audio problems
  - VR headset detection failures
  - Performance degradation

#### Wine VR Support
- **OpenVR Support**: Limited through wine-staging
- **OpenXR Support**: Experimental, not production ready
- **VR API Translation**: Significant performance overhead

### Known Technical Challenges

#### Graphics Performance
- **Wine Overhead**: 10-30% performance penalty typical
- **VR Requirements**: Need consistent 90+ FPS
- **GPU Utilization**: May not reach optimal utilization through Wine

#### Audio Routing
- **VR Audio**: Complex routing through Wine to VR headset
- **Spatial Audio**: 3D positioning may be degraded
- **Multiple Audio Devices**: Wine struggles with multiple audio outputs

## Software Compatibility Matrix

### Recommended Software Versions

| Component | Version | Status | Notes |
|-----------|---------|--------|-------|
| Pop!_OS | 22.04+ | Recommended | LTS base, good driver support |
| Linux Kernel | 6.0+ | Required | Modern VR device support |
| Wine | 8.0+ staging | Required | VR patches in staging branch |
| Mesa | 22.0+ | Recommended | Modern OpenGL/Vulkan support |
| NVIDIA Driver | 530+ | Required | VR-capable driver version |

### VR Runtime Matrix

| Runtime | Pico 4 Support | DCS Compatibility | Overall Viability |
|---------|----------------|-------------------|-------------------|
| Monado | Community only | Untested | Medium |
| SteamVR | None | Limited legacy | Low |
| ALVR | Yes (wireless) | Untested | Medium-High |

## Performance Considerations

### Hardware Requirements Refined

#### Minimum Specifications
- **CPU**: Intel i5-10400 / AMD Ryzen 5 3600 or better
- **GPU**: RTX 3070 / RX 6700XT or better (accounting for Wine overhead)
- **RAM**: 32GB recommended (16GB absolute minimum)
- **Storage**: NVMe SSD for DCS installation

#### Network Requirements (for ALVR)
- **WiFi**: WiFi 6 (802.11ax) strongly recommended
- **Bandwidth**: 100+ Mbps for high quality streaming
- **Latency**: <5ms network latency to VR headset

## Risk Assessment

### High Risk Items
1. **Wine VR API Support**: Limited and experimental
2. **Pico 4 Driver Availability**: No official Linux drivers
3. **Performance Overhead**: Wine + VR may be too slow
4. **DCS VR Integration**: Complex VR implementation may not translate

### Medium Risk Items
1. **Audio Complexity**: Multiple audio device routing
2. **Controller Input**: Game controller mapping through Wine
3. **Display Configuration**: Multi-monitor + VR setup complexity

### Low Risk Items
1. **Basic DCS Functionality**: DCS runs on Wine (non-VR)
2. **System Stability**: Pop!_OS is stable platform
3. **Community Support**: Active Linux gaming community

## Alternative Approaches

### Approach 1: Native Linux DCS
- **Viability**: Very low (no official support)
- **Community Efforts**: Some reverse engineering attempts
- **Timeline**: Years, if ever

### Approach 2: Windows VM with GPU Passthrough
- **Viability**: High for DCS, medium for VR
- **Complexity**: Very high setup complexity
- **Performance**: Near-native Windows performance
- **VR Challenges**: USB and display passthrough complexity

### Approach 3: Dual Boot Optimization
- **Viability**: High (guaranteed compatibility)
- **User Experience**: Poor (requires rebooting)
- **Maintenance**: Dual system maintenance overhead

## Next Steps for Phase 1

### Immediate Actions Required
1. Set up test environment with latest Wine-staging
2. Install and configure Monado OpenXR runtime
3. Test basic VR functionality with simple applications
4. Attempt DCS installation and basic (non-VR) functionality
5. Research ALVR setup and Pico 4 integration

### Research Questions to Answer
1. Can Pico 4 be detected and used with Monado?
2. Does Wine-staging VR support work with OpenXR?
3. What is the performance overhead of Wine + VR?
4. Are there any DCS-specific VR compatibility issues?

## Community Feedback Integration

*This section will be updated as community feedback is received and incorporated into research findings.*

---

**Last Updated**: Initial creation  
**Research Status**: Preliminary investigation  
**Next Review**: After initial testing phase