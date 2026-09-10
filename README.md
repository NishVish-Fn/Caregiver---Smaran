# Smaran Guardian â€” Real-Time Geofence Sentinel & Patient Safety Monitor (Caregiver App)

<p align="center">
  <img src="app/src/main/res/drawable/smaran_logo.png" alt="Smaran Logo" width="120" />
</p>

A modern Android caregiver application built with Kotlin, Jetpack Compose, and OpenStreetMap. Smaran Guardian serves as the dedicated caregiver companion app for the **Smaran** cognitive care platform, providing families, caregivers, and clinicians with real-time location monitoring, geofence boundary enforcement, and instant wander alerts for dementia and Alzheimer's patients.

---

## ðŸ“¦ Pre-Built Release APK

The production-ready, pre-compiled Guardian APK is included directly within this repository:

* **Download APK**: [release/Smaran-Guardian-v1.0.apk](release/Smaran-Guardian-v1.0.apk)
* **Package Name**: `net.kibotu.geofencerelay.guardian`
* **App Name**: Smaran Guardian
* **Version**: 1.0.0
* **Target Android Version**: Android 8.0 (API 26) through Android 14 (API 34)

---

## ðŸŒŸ Key Features & Architecture

### 1. ðŸ—ºï¸ Live OpenStreetMap (OSM) Sentinel
- **Real-Time GPS Telemetry**: Subscribes to live patient coordinates streamed over lightweight MQTT channels (`smaran/tracker/{patientId}/ping`).
- **Open-Source Mapping**: High-performance vector map rendering via OpenStreetMap (OSMDroid) without expensive proprietary cloud map billing or API keys.
- **Dynamic Breadcrumb Trail**: Tracks and displays historical movement points to see the path the patient has walked.
- **Recenter & Follow**: One-tap target locking to smoothly pan and zoom to the patient's current coordinates.

### 2. ðŸ›¡ï¸ Interactive Safe Zone Geofencing
- **Customizable Boundaries**: Set and adjust circular safe zones (50m to 5,000m radius) around homes, senior living facilities, or parks.
- **Visual Overlay**: Real-time translucent circle overlay on the map showing the active perimeter.
- **Geodesic Distance Math**: Computes exact Euclidean and Haversine distance from the patient to the safe zone centroid with millisecond accuracy.

### 3. ðŸš¨ Instant Breach Alerts & Loud Alarms
- **Immediate Breach Detection**: Detects perimeter breaches the instant coordinates fall outside the configured safe zone.
- **Vibrant Pulsating Alert Banner**: High-urgency visual warning banner with real-time distance and timestamp indicators.
- **Audible Siren System**: Triggers continuous alarm ringtones and vibration on the caregiver's device (`SoundPlayer.kt`) to ensure immediate caregiver wake-up and response.
- **High-Priority Notification**: System notification banner persistent even when the app is minimized.

### 4. ðŸ”‹ Remote Patient Telemetry & Health Diagnostics
- **Battery Health**: Real-time battery percentage display with low-power warning badges.
- **Movement Speed & Latency**: Real-time speed calculations (km/h) to distinguish between walking, running, and vehicular transport.
- **Signal Quality & Last-Seen**: Displays timestamp of the last received ping to immediately detect GPS blackout or device power-off.

### 5. âš¡ Quick Emergency Response Actions
- **ðŸ“ž Call Patient**: Instantly opens device dialer with the patient's emergency contact number.
- **ðŸ§­ Directions to Patient**: One-tap deep link opening Google Maps, OsmAnd, or external turn-by-turn navigation apps directly routed to the patient's latest GPS position.
- **ðŸ”Š Trigger Remote Alert**: Sends an MQTT command to the patient's phone to play a loud beacon tone if searching in a crowded or obscured public area.

### 6. ðŸ”’ Zero-Cloud Infrastructure Cost & Privacy
- **Public / Private MQTT Relay**: Communicates via lightweight MQTT brokers (`broker.hivemq.com` or private brokers) with zero cloud database subscription requirements.
- **Direct Device Pairing**: Devices pair securely using shared patient identifiers or Google Sign-In accounts.

---

## ðŸ› ï¸ Build & Development

### System Requirements
- Android SDK 34 (compileSdk 35, minSdk 26)
- JDK 17 or JDK 21
- Gradle 8.2+

### Building from Source

```powershell
# Build Guardian APK
.\gradlew.bat assembleGuardianDebug

# Run Guardian Unit Tests
.\gradlew.bat testGuardianDebugUnitTest
```

The compiled APK will be generated at:
`app/build/outputs/apk/guardian/debug/app-guardian-debug.apk`

---

## ðŸ“± Companion Patient App

For the patient-side application featuring the Apple iOS Assistive Access Springboard, 100% on-device Cognitive Performance Scoring (CPS) ML engine, 7 Northeast Region dialects, and lock-screen alarm wake-up screen, visit:
* [Patient Smaran Repository](https://github.com/NishVish-Fn/Patient---smaran)