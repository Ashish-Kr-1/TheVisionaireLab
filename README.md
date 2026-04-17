# VirtualRoboticsLab — Hackathon Project

A mobile VR robotics laboratory built with Unity 6 and Google Cardboard, targeting Android. Users can explore a 3D robotics lab environment in immersive stereoscopic VR using just a smartphone and a Google Cardboard headset.

---

## Description

VirtualRoboticsLab places the user inside a virtual robotics lab — complete with machinery, structural elements, and an industrial environment — viewable in 6DoF-inspired 3D space with gyroscope-driven head tracking. The project targets Android devices and renders in Google Cardboard stereo mode, making it accessible with low-cost VR hardware.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Engine | Unity 6 (6000.4.2f1) |
| Render Pipeline | Universal Render Pipeline (URP 17.4.0) |
| XR Plugin | Google Cardboard XR Plugin for Unity 1.33.0 |
| XR Management | Unity XR Plugin Management 4.x |
| Input | Unity Input System + Legacy XR Input |
| Scripting Backend | IL2CPP |
| Target Architecture | ARM64 |
| Target Platform | Android (min API 26 / Android 8.0) |
| Tested Device | Realme RMX3869 (Android API 34) |

---

## Features

- **Stereoscopic VR rendering** via Google Cardboard XR Plugin
- **Gyroscope head tracking** — rotate the phone to look around the lab
- **3D lab environment** imported from a custom `.fbx` model (`finalLab.fbx`)


## Android Build Configuration

- **Activity**: `UnityPlayerActivity` (required by Cardboard — GameActivity not supported)
- **Graphics API**: OpenGLES3 only (Vulkan disabled — required by Cardboard)
- **Min SDK**: API 26 (Android 8.0) — enforced by GfxPluginCardboard
- **Permissions**: `CAMERA`, `INTERNET`, `VIBRATE`
- **Orientation**: Landscape

---

## Scene Hierarchy

```
CameraRig                    ← VRController (movement)
└── Camera (MainCamera)      ← HeadTracking, VRDebug3D, CardboardStartup
Directional Light
Global Volume
lab                          ← Imported robotics lab geometry
```

---

## Setup & Build

1. Open project in **Unity 6 (6000.4.2f1)**
2. Install **Android Build Support** (IL2CPP + Android SDK/NDK tools)
3. Ensure **CMake 3.22.1** is installed via Android SDK Manager
4. Set build target: `File → Build Settings → Android`
5. Connect Android device with USB Debugging enabled
6. `Build and Run`

> **SDK Note:** Unity requires `cmdline-tools/latest` to be present in your Android SDK path. CMake 3.22.1 is required for IL2CPP compilation.

---

## Known Issues / In Progress

- Head tracking via `InputDevice` feature enumeration is under active debugging — Cardboard XR registers the HMD device but tracking state requires further investigation
- `Input.gyro` is intercepted by the Cardboard XR subsystem when active
- `OnGUI` does not render in Cardboard stereo mode — debug output uses 3D world-space TextMesh

---

## Hackathon Progress Log

| Stage | Status |
|---|---|
| Android SDK + build pipeline setup | ✅ Done |
| Google Cardboard XR plugin integration | ✅ Done |
| App builds and deploys to device | ✅ Done |
| Stereo VR rendering (split screen) | ✅ Done |
| Head tracking (gyro / XR) | 🔧 In Progress |

---

## Author

**Ashish Kr** — [@Ashish-Kr-1](https://github.com/Ashish-Kr-1)
