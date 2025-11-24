# 📍 Ultimate Person & Zone Tracker Suite & Utilities

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/fredamn76/homeassistant-blueprints/graphs/commit-activity)
[![Home Assistant](https://imgshields.io/badge/Home%20Assistant-Blueprints-blue)](https://www.home-assistant.io/)

<p align="center">
  <img src="https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/logo.jpg" width="150" alt="Logo">
</p>

A collection of advanced, **QA-verified** Blueprints and configuration templates for Home Assistant, designed for robustness and maintainability.

---

## 🌍 PERSON & ZONE TRACKER SUITE

The complete, **privacy-first** and fully local alternative to Life360 for Home Assistant. This suite provides advanced location tracking with rich notifications and ensures your devices stay powered up.

### 1. 🌍 Person & Zone Tracker (Core Blueprint)
The heart of the system. An advanced automation blueprint designed to track arrivals and departures with precision, style, and reliability.

**Key Features:**
* 📸 **Dynamic Notifications:** Displays the user's profile picture (with smart fallback to a brand logo).
* 📍 **Clickable Maps:** Open the location map directly from the notification action.
* ⏱️ **Duration Logging:** Tracks time spent at a location (e.g., "Left Work after 8h 30m").
* 🛡️ **Defensive Logic:** Handles GPS drift ("flapping") and gracefully ignores unavailable/unknown states.
* 🤫 **Privacy & Quiet Mode:** Configurable quiet hours to mute notifications at night.

<details>
<summary>📋 <b>Click to view Configuration Variables</b></summary>

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `persons_to_track` | List of person entities to monitor. | ✅ | - |
| `zones_to_track` | List of zones that trigger notifications. | ✅ | - |
| `notify_primary` | Primary notification service (e.g., `notify.mobile_app_iphone`). | ✅ | - |
| `home_zone_alias` | Friendly name for Home (e.g., "Home" or "Hemma"). | ❌ | "Home" |
| `stability_delay` | Seconds to wait before confirming zone change (prevents false alarms). | ❌ | `0` |
| `use_quiet_hours` | Enable to mute notifications during night. | ❌ | `false` |
| `branding_logo` | URL to fallback image if user has no profile picture. | ❌ | (Included) |
| `click_url` | Action when clicking "Map" button. | ❌ | `/lovelace/map` |

</details>


[![Import Person Tracker](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/person_zone_tracker.yaml)

---

### 2. 🔋 Battery Monitor (Required Add-on)
Reliable tracking requires power. This blueprint monitors the devices used by the **Person Tracker Suite** and warns you before they go dark.

**Key Features:**
* 🧠 **Anti-Spam Logic:** Intelligently alerts only **once** per discharge cycle (prevents constant nagging).
* 📱 **Unified Branding:** Uses the same visual identity and logo as the Tracker.
* ⚙️ **QA-Verified:** Optimized `parallel` execution to handle multiple devices reporting simultaneously without errors.

<details>
<summary>📋 <b>Click to view Configuration Variables</b></summary>

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `battery_sensors` | List of battery sensors to monitor. | ✅ | - |
| `threshold` | Percentage level to trigger alert. | ❌ | `15%` |
| `notify_service` | Notification service to send alerts to. | ❌ | (Empty) |
| `notification_logo` | URL for the notification icon/image. | ❌ | (Included) |
| `actions` | Additional actions to run (e.g., TTS, light flash). | ❌ | `[]` |

</details>


[![Import Battery Monitor](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/battery_monitor.yaml)


---

### 3. 📱 Tracker Dashboard View
We have included a pre-configured dashboard view (YAML) tailored for this tracker suite. It features a status overview, battery monitoring, timeline, and a Google Map history view.

### Preview
![Dashboard Preview](https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/dashboard-preview.png)

### ⚙️ Configuration Guide
When you copy the [dashboard YAML code](dashboards/person_tracker_view.yaml), you must replace the following placeholders with your specific entities:

| Placeholder | Description | Example |
| :--- | :--- | :--- |
| `person.your_name` | The main person entity you want to track on the map. | `person.philip` |
| `sensor.your_device_battery_level` | The battery sensor of the tracked device. | `sensor.pixel_9_battery_level` |
| `sensor.your_device_geocoded_location` | Sensor providing the address text (from Companion App or integration). | `sensor.pixel_9_geocoded_location` |
| `YOUR_GOOGLE_MAPS_API_KEY` | **Required.** Your personal API Key from Google Cloud Platform. | `AIzaSyD...` |

**Requirements (HACS):**
* [Google Maps Card](https://github.com/kreativ-monkey/hass-google-map-card) (Required for history map)
* [card-mod](https://github.com/thomasloven/lovelace-card-mod) (Required for text styling)

**Download:**
[View Dashboard YAML](https://github.com/fredamn76/homeassistant-blueprints/blob/main/dashboards/person_tracker_view.yaml)

---

### 4. 🛠️ Installation & Usage (Tracker Suite)

1. **Install Companion App:** Ensure the Home Assistant Companion App is installed on your devices for location reporting.
2. **Import Blueprints:** Click the badges above to import the automations directly into Home Assistant.
3. **Create Automations:** Set up your person/zone tracker and battery monitor using the imported blueprints.
4. **(Optional) Dashboard:** Copy the dashboard YAML code to a new view in your Lovelace dashboard.

---

### 5. ❓ Troubleshooting (Location Tracking Focus)

**Issue: History or Logbook is empty/inconsistent.**
If your person entity updates are missing from the logbook, it is often due to phone battery optimizations killing the Home Assistant app in the background.

**Fix for Android (Pixel/Samsung):**
1. Go to **Settings** -> **Apps** -> **Home Assistant**.
2. Tap **Battery**.
3. Change setting to **Unrestricted** (or "Don't optimize").
4. Ensure **Location** permission is set to **"Allow all the time"**.

---
---

## ⏰ ADVANCED ALARM CLOCK (Standalone Utility)

### 6. Advanced Alarm Clock (Light & Sound)
This is a complex, multi-user alarm clock blueprint designed as a separate, powerful utility. It simulates a natural sunrise while providing dynamic media playback (e.g., via Music Assistant / MASS).

**Key Features:**
* ☀️ **Sunrise Simulation:** Dynamic light fade-in over a user-defined period (minutes).
* 🔊 **Dynamic Media:** Plays local media files at a custom volume (set per alarm).
* 👤 **Multi-User Ready:** Designed to be easily cloned for multiple people using a simple prefix and template system.
* 📆 **Schedule Control:** Day-of-week activation is controlled via dashboard toggles (Input Booleans).

<details>
<summary>📋 <b>Click to view Configuration Variables (Blueprint Inputs)</b></summary>

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `person_entity` | Entity of the person to check (alarm only runs if person is 'home'). | ✅ | - |
| `alarm_time_entity` | `input_datetime` helper for the main sound alarm time. | ✅ | - |
| `alarm_enabled_entity` | `input_boolean` master toggle for the alarm. | ✅ | - |
| `target_light` | The light entity used for the sunrise fade effect. | ✅ | - |
| `light_offset_entity` | `input_number` defining the duration of the light fade (in minutes). | ✅ | - |
| `media_player_select` | `input_select` helper containing the available speaker entity IDs. | ✅ | - |
| `media_file_select` | `input_select` helper listing the available media filenames. | ✅ | - |
| `day_monday`...`day_sunday` | Individual `input_boolean` helpers used to enable/disable the alarm per day. | ✅ | - |

</details>

### Preview
![Advanced Alarm Clock Dashboard Preview](https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/alarm-clock-preview.png)

### Helper & Dashboard Configuration

This Blueprint requires external helpers to function. Use the provided templates for easy setup.

| Asset Type | File Path | Purpose |
| :--- | :--- | :--- |
| **Helper Template** | [packages/advanced_alarm_clock_template.yaml](packages/advanced_alarm_clock_template.yaml) | **Required.** YAML template to quickly create all necessary `input_*` helpers (`input_boolean`, `input_number`, etc.). Requires replacing the `[PREFIX]` placeholder. |
| **Dashboard View** | [dashboards/advanced_alarm_clock_dashboard_template.yaml](dashboards/advanced_alarm_clock_dashboard_template.yaml) | YAML for a customized Lovelace view designed to control all helper entities easily. Requires replacing `[[PREFIX]]` and `[[NAME]]` placeholders. |


[![Import Advanced Alarm Clock](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/advanced_alarm_clock_mass.yaml)


---
*Developed with ❤️ and 🤖 using AI-assisted coding & QA.*
