# Next Steps - VR Testing Phase

**Phase**: Environment Setup → VR Integration Testing
**Priority**: High - Core VR functionality

## 🎯 Immediate Next Steps (Phase 2)

### 1. Pico 4 Connectivity Setup
**Priority**: Critical
**Estimated Time**: 2-4 hours

#### Option A: ALVR (Air Light VR) - Wireless
```bash
# Test ALVR installation and configuration
# Requires Pico 4 ALVR client app
# WiFi network optimization for low latency
```

#### Option B: USB Connection
```bash
# Test USB debugging/connection modes
# Investigate ADB-based VR streaming
# USB 3.0+ required for bandwidth
```

**Success Criteria**: Pico 4 detected by OpenXR runtime

### 2. OpenXR Runtime Configuration
**Priority**: Critical
**Estimated Time**: 1-2 hours

```bash
# Switch from Monado dummy HMD to Pico 4
# Configure OpenXR environment variables
# Test basic VR scene rendering
openxr_runtime_list  # Should show Pico 4 instead of dummy
```

**Success Criteria**: OpenXR recognizes Pico 4 as active HMD

### 3. SteamVR Integration
**Priority**: High
**Estimated Time**: 2-3 hours

```bash
# Install SteamVR through Steam client
# Configure SteamVR for Linux OpenXR
# Test SteamVR room setup and tracking
```

**Success Criteria**: SteamVR shows Pico 4 in headset list

### 4. DCS VR Mode Testing
**Priority**: High
**Estimated Time**: 3-5 hours

```bash
# Launch DCS through Wine with VR enabled
WINEPREFIX=/home/jpvr/wine-prefixes/dcs wine DCS.exe --force_enable_VR
# Configure DCS VR settings
# Test basic VR functionality in DCS
```

**Success Criteria**: DCS launches in VR mode, basic head tracking works

## 🔧 Configuration Tasks

### A. VR Environment Setup
1. **Install VR-specific packages**
   ```bash
   # ALVR if using wireless
   # Additional OpenXR layers
   # VR testing tools
   ```

2. **Network optimization** (for ALVR)
   ```bash
   # Router QoS settings
   # WiFi 6 optimization
   # Latency measurement tools
   ```

3. **Performance optimization**
   ```bash
   # GPU scheduling priority
   # CPU governor settings
   # Memory allocation tuning
   ```

### B. Steam Configuration
1. **SteamVR setup**
   - Install SteamVR beta (Linux support)
   - Configure OpenXR runtime
   - Room scale calibration

2. **Steam Input configuration**
   - Pico 4 controller mapping
   - DCS control bindings
   - VR overlay settings

### C. DCS Optimization
1. **Wine VR configuration**
   - DXVK/VKD3D for Vulkan translation
   - VR-specific Wine registry settings
   - Performance monitoring

2. **DCS VR settings**
   - Resolution scaling
   - Render pipeline optimization
   - Control mapping for VR

## 🧪 Testing Protocol

### Phase 2.1: Basic VR Functionality
- [ ] Pico 4 connection established
- [ ] OpenXR runtime detects headset
- [ ] Basic head tracking functional
- [ ] Controllers recognized
- [ ] Play area setup complete

### Phase 2.2: SteamVR Integration
- [ ] SteamVR installs successfully
- [ ] Headset visible in SteamVR
- [ ] Room setup completed
- [ ] SteamVR overlay functional
- [ ] Performance metrics available

### Phase 2.3: DCS VR Integration
- [ ] DCS launches in VR mode
- [ ] Head tracking in cockpit works
- [ ] Acceptable frame rate (45+ FPS)
- [ ] Controller input functional
- [ ] No major visual artifacts

### Phase 2.4: Performance Optimization
- [ ] Frame rate analysis and optimization
- [ ] Latency measurement and tuning
- [ ] Visual quality vs performance balance
- [ ] Long session stability testing

## 🚫 Potential Blockers

### Technical Challenges
1. **Wine VR API Support**
   - OpenXR through Wine compatibility
   - DirectX VR translation issues
   - Performance overhead

2. **Pico 4 Linux Compatibility**
   - Limited official Linux support
   - ALVR dependency for wireless
   - Driver availability

3. **DCS VR Optimization**
   - Heavy GPU requirements
   - Wine performance penalty
   - VR-specific bugs in DCS

### Mitigation Strategies
- **Fallback Options**: Document alternative VR runtimes
- **Performance Monitoring**: Continuous FPS/latency tracking
- **Incremental Testing**: Test each component individually
- **Documentation**: Record all configuration steps

## 📊 Success Metrics

### Minimum Viable VR Setup
- **Connection**: Pico 4 recognized and stable
- **Tracking**: 6DOF head tracking functional
- **Performance**: 45+ FPS sustained
- **Controls**: Basic VR interaction working

### Optimal VR Experience
- **Performance**: 90+ FPS for smooth experience
- **Latency**: <20ms motion-to-photon
- **Stability**: 30+ minutes without crashes
- **Quality**: High visual fidelity maintained

### DCS-Specific Goals
- **VR Mode**: DCS launches successfully in VR
- **Cockpit**: Readable instruments and controls
- **Performance**: Playable frame rates in combat
- **Controls**: Full HOTAS integration in VR

## 📝 Documentation Requirements

### For Each Testing Phase
1. **Command logs** in `command-log.md`
2. **Configuration files** backed up
3. **Performance metrics** recorded
4. **Issue troubleshooting** documented
5. **Success/failure criteria** tracked

### Final Deliverable
- Complete VR setup guide
- Performance optimization recommendations
- Troubleshooting documentation
- Hardware compatibility matrix

---
**Ready to Begin**: ✅ Environment prepared for VR testing phase
**Next Action**: Connect and configure Pico 4 headset