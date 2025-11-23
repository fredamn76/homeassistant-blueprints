# Home Assistant Blueprints

A collection of robust automation blueprints for Home Assistant. These blueprints are designed to handle edge cases, unavailable entities, and ensure consistent behavior across iOS and Android.

## 📦 Included Blueprints

### 1. 🔋 Battery Monitor (Smart Alert)
*File: `automation/battery_monitor.yaml`*

A comprehensive battery monitoring solution that avoids spamming notifications.
* **Threshold Triggers:** Alerts only when devices drop below your set percentage.
* **Reliable Icons:** Uses the standard `mdi:battery-alert` icon for the system notification badge to ensure visibility on all devices.
* **Custom Branding:** Attaches your custom logo (or a default warning image) as the **large banner image** in the notification.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ffredamn76%2Fhomeassistant-blueprints%2Fblob%2Fmain%2Fautomation%2Fbattery_monitor.yaml)

### 2. 📍 Person & Zone Tracker (Life360-style)
*File: `automation/person_zone_tracker.yaml`*

Advanced location tracking designed to replicate the best features of Life360 within Home Assistant.
* **Rich Notifications:** Shows who arrived/left, where, and for how long.
* **Smart Fallback Logic:** 1. Uses the Person's **Profile Picture** if available.
    2. Falls back to your **Custom Brand Logo** if no profile picture exists.
* **Click Actions:** Direct links to the Map or Person History dashboard.
* **Quiet Hours:** Suppress notifications during night or specific times.
* **Android Optimized:** Uses the standard `mdi:account` icon for the status bar to prevent rendering errors on Android devices.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ffredamn76%2Fhomeassistant-blueprints%2Fblob%2Fmain%2Fautomation%2Fperson_zone_tracker.yaml)

---

## 🎨 Notification & Branding Logic

To ensure maximum compatibility (especially with Android's stricter notification standards), these blueprints use a **Hybrid Notification Approach**:

| Visual Element | Source | Why? |
| :--- | :--- | :--- |
| **Small Icon** (Status Bar) | **MDI Icons** (`mdi:battery-alert`, `mdi:account`) | Using custom URLs here often fails on Android. Standard icons guarantee the notification is delivered and categorized correctly. |
| **Large Image** (Expanded) | **Your Custom Logo** | This is where your branding shines. The blueprint attaches your logo URL as the feature image. |

### Configuration
To change the default branding logo for all blueprints, edit the `default` value in the YAML files or override it in the automation UI:

```yaml
notification_logo: "[https://raw.githubusercontent.com/your-repo/main/images/logo.jpg](https://raw.githubusercontent.com/your-repo/main/images/logo.jpg)"
