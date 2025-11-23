# 📍 Ultimate Person & Zone Tracker Suite

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/fredamn76/homeassistant-blueprints/graphs/commit-activity)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Blueprints-blue)](https://www.home-assistant.io/)

<p align="center">
  <img src="https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/logo.jpg" width="150" alt="Logo">
</p>

A complete, **privacy-first** and fully local alternative to Life360 for Home Assistant. This suite provides advanced location tracking with rich notifications and ensures your devices stay powered up.

---

## 1. 🌍 Person & Zone Tracker (Core)
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

<br>

[![Import Person Tracker](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/person_zone_tracker.yaml)

---

## 2. 🔋 Battery Monitor (Smart Add-on)
Reliable tracking requires power. This "Smart Alert" blueprint monitors your devices and warns you before they go dark.

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

<br>

[![Import Battery Monitor](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/battery_monitor.yaml)

---

## 📱 Bonus: Dashboard View
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

## 🛠️ Installation & Usage

1. **Install Companion App:** Ensure the Home Assistant Companion App is installed on your devices for location reporting.
2. **Import Blueprints:** Click the badges above to import the automations directly into Home Assistant.
3. **Create Automations:** Set up your person/zone tracker and battery monitor using the imported blueprints.
4. **(Optional) Dashboard:** Copy the dashboard YAML code to a new view in your Lovelace dashboard.

---
*Developed with ❤️ and 🤖 using AI-assisted coding & QA.*


[![Import Battery Monitor](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/battery_monitor.yaml)

---

## 🛠️ Installation & Requirements

1. Ensure the **Home Assistant Companion App** is installed on your devices.
2. Click the **"Import Blueprint"** badges above.
3. Create an automation from each blueprint.
4. **(Optional):** The blueprints will automatically use the hosted logo. You can override this in the blueprint settings if you prefer your own image.

---

## 📱 Bonus: Dashboard View
We have included a pre-configured dashboard view (YAML) tailored for this tracker suite. It features a status overview, battery monitoring, timeline, and a Google Map history view.

### Preview
![Dashboard Preview](https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/dashboard-preview.png)

**Requirements (HACS):**
* [Google Maps Card](https://github.com/kreativ-monkey/hass-google-map-card) (Required for history map)
* [card-mod](https://github.com/thomasloven/lovelace-card-mod) (Required for text styling)

**Download:**
[View Dashboard YAML](https://github.com/fredamn76/homeassistant-blueprints/blob/main/dashboards/person_tracker_view.yaml)

*Note: You need your own Google Maps API Key for the map card to work.*


---
*QA-Tested on Home Assistant Core 2024.x and Android/iOS Companion Apps.*

## 🤖 Acknowlegements
This project was developed in collaboration with AI tools to ensure high code quality, robust error handling, and comprehensive documentation.

