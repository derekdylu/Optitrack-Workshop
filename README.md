# Optitrack Workshop Template

This is a Unity project template for using the Optitrack motion capture system in NTU CSIE Make Reality Space (學新館 R523). This guide provides comprehensive instructions for setting up and using the Optitrack system with Unity.

> **Note:** The software versions specified in this guide are based on this template repository and have been tested for compatibility.

## Table of Contents
- [System Requirements](#system-requirements)
- [Hardware Setup](#hardware-setup)
- [Software Setup](#software-setup)
- [System Preparation](#system-preparation)
- [Calibration Process](#calibration-process)
- [Tracking Objects](#tracking-objects)
- [Unity Integration](#unity-integration)
- [Troubleshooting](#troubleshooting)

## System Requirements

### Software Versions
- Unity 2022.3.10f1
- Optitrack Plugin 1.4.0 ([Download Page](https://optitrack.com/support/downloads/plugins.html), under previous releases)

### Related Documents
- [Workshop Presentation](https://docs.google.com/presentation/d/11aD-HxLk-XhHdVrZEUAQN0n-gB6hjiFcsz3grq77rik/edit?usp=sharing)
- [Meta Quest Troubleshooting Guide](https://docs.google.com/document/d/1T4O1uPJrNyjCdtW5sRuQncF0N8v_rSiHEUfBRHRzMuM/edit?usp=sharing)
- [Lab Documentation (2023)](https://docs.google.com/document/d/1BuHK9xWxZrF7RBsJuCJxzwdELC0IGPYcNBGZhsFszzM/edit?usp=sharing)
- [OptiTrack Official Documentation](https://docs.optitrack.com/)
- [Optitrack Unity Plugin Documentation](https://docs.optitrack.com/plugins/optitrack-unity-plugin)

## Hardware Setup

### OptiTrack Prime x13 Cameras
- High-performance tracking cameras operating at 240-1000 fps
- System tracks objects by detecting reflective markers
- 3D coordinates are calculated when multiple cameras detect the same marker
- Positioned strategically around the tracking volume

### Markers
- Essential components for object tracking
- Use 3M 7610 reflective tape for optimal performance
- Various marker combinations available in the lab
- Custom markers can be created for specific requirements
- Must be properly placed and maintained for accurate tracking

### Motion Capture Suit
- Specialized breathable suit for full-body motion capture
- Equipped with attachable X-shaped markers
- Markers must be placed at specific anatomical points
- Ensures consistent and accurate motion tracking

### Calibration Tools
1. **CW-500 Calibration Wand Kit**
   - Used for system calibration
   - Helps establish camera positions and orientations
   - Essential for accurate tracking setup

2. **CS-200 Calibration Square**
   - Used to reset coordinate system origin
   - Establishes ground plane reference
   - Critical for proper spatial alignment

## Software Setup

### Motive Software
- Pre-installed on lab computers
- Requires hardware dongle for operation
- Primary software for:
  - System calibration
  - Real-time tracking
  - Data recording and playback
  - Rigid body and skeleton tracking

## System Preparation

### Environment Setup
1. **Clear Tracking Volume**
   - Remove all reflective objects
   - Clear camera field of view
   - Ensure unobstructed camera views

2. **Lighting Conditions**
   - Maintain consistent lighting
   - Avoid direct sunlight
   - Minimize reflective surfaces

3. **Space Requirements**
   - Ensure adequate tracking volume
   - Clear walking paths
   - Remove potential obstacles

## Calibration Process

### Initial Setup
1. Launch Motive software
2. Navigate to Layout / Calibrate
3. Clear existing masks
4. Hide all markers in the environment
5. Click "Mask Visible" to block unwanted reflections

### Wanding Process
1. **Preparation**
   - Assemble CW-500 calibration wand
   - Ensure all cameras are powered on
   - Clear tracking volume

2. **Calibration Steps**
   - Click "Start Wanding" in the Wanding section
   - Wave the wand throughout the tracking space
   - Follow these guidelines:
     - Cover the entire tracking volume
     - Aim for 1000-4000 samples per camera (max 10000)
     - Move slowly and vary positions
     - Monitor Camera Preview for coverage
     - Watch for blue (tracking) and green (recorded) indicator lights

### Calibration Quality
- Calculate calibration after sufficient samples
- Quality levels (from lowest to highest):
  - Poor
  - Fair
  - Good
  - Great
  - Excellent
  - Exceptional
- Apply and save if satisfied with results

### Ground Plane Setup
1. Click "Ground Plane" under Camera Calibration
2. Place CS-200 on the ground
3. Select the three markers in Perspective View
4. Click "Set Ground Plane"
5. **Coordinate System**:
   - Right angle is at origin (0,0,0)
   - Long edge aligns with Z-axis
   - Short edge aligns with X-axis

## Tracking Objects

### Rigid Body Tracking
- **Requirements**:
  - Minimum 4 markers per rigid object
  - Markers must be fixed to the object
  - Object must maintain its shape

- **Marker Placement Guidelines**:
  - Ensure visibility from multiple cameras
  - Use asymmetric patterns for better angle tracking
  - Create distinct patterns for multiple objects
  - Consider object size and shape
  - Account for potential occlusions

### Skeleton Tracking
- **Features**:
  - Built-in tracking modes for full/half body capture
  - Real-time motion capture
  - Customizable tracking points

- **Setup**:
  - Use Motion Capture Suit
  - Place markers at specified anatomical points
  - Follow calibration procedures

## Unity Integration

### Initial Setup
1. **Plugin Installation**
   - Download Unity plugin (version 1.4.0)
   - Install in Unity 2022.3.10f1 project
   - Verify installation in Unity Package Manager

2. **Motive Configuration**
   - Open streaming settings
   - Configure network settings:
     - Local Interface: Loopback (same computer) or 192.168.x.x (network broadcasting)
     - Transmission Type: Unicast (recommended, more stable) or Multicast (more compatible)

### Unity Configuration
1. **Streaming Client Setup**
   - Add Optitrack Streaming Client to empty GameObject
   - Configure IP settings based on setup:

   **Same Computer Configuration**:
   ```ini
   Motive Local Interface: loopback
   Unity Optitrack Streaming Client
    Server Address: 127.0.0.1
    Local Address: 127.0.0.1
   ```

   **Network Configuration**:
   ```ini
   Motive Local Interface: 192.168.x.x
   Unity Optitrack Streaming Client
    Server Address: 192.168.x.x
    Local Address: [check with ipconfig in terminal]
   ```

2. **Object Tracking Setup**
   - Add Optitrack Rigid Body to tracked GameObjects
   - Connect to Streaming Client
   - Set correct tracking ID
   - Verify tracking in runtime

## Troubleshooting

### Common Issues
1. **Tracking Problems**
   - Restart applications or computers
   - Verify plugin version compatibility
   - Check object IDs match between Motive and Unity
   - Ensure Motive is tracking the object

2. **Calibration Issues**
   - Recalibrate system
   - Check camera positions
   - Verify marker visibility
   - Clear tracking volume

3. **Unity Integration**
   - Verify network settings
   - Check plugin installation
   - Confirm GameObject setup
   - Review streaming client configuration

4. **Meta Quest Integration**
   - Refer to [Meta Quest Troubleshooting Guide](https://docs.google.com/document/d/1T4O1uPJrNyjCdtW5sRuQncF0N8v_rSiHEUfBRHRzMuM/edit?usp=sharing)
