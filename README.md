# 🏠 Home Assistant Blueprints

A collection of custom-made blueprints for a smarter home. Designed to be robust, family-friendly, and easy to install.

---

## 🤖 Automations

### 1. 📍 [Person & Zone Tracker (Life360 Alternative)](automation/person_zone_tracker.yaml)
*The ultimate privacy-focused alternative to Life360. Track family members with rich notifications, images, and history.*

**Features:**
* 📸 **Rich Notifications:** Displays the person's profile picture directly in the notification.
* ⏱️ **Duration Logging:** *"Left Work (was there for 8h 30m)"*.
* 🗺️ **Action Buttons:** Direct links to "Map" and "Person History".
* 🌙 **Quiet Hours:** Built-in privacy mode to stop notifications at night.
* 🏠 **Smart Naming:** Automatically handles the system "home" state and displays "Home" (or custom alias).

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ffredamn76%2Fhomeassistant-blueprints%2Fblob%2Fmain%2Fautomation%2Fperson_zone_tracker.yaml)

---

### 2. 🔋 [Battery Monitor (Smart Alert)](automation/battery_monitor.yaml)
*Get warned before phones or tablets run out of battery. Intelligent logic prevents spam.*

**Features:**
* 📉 **Custom Threshold:** Choose when you want to be warned (e.g., below 15%).
* 🛡️ **Anti-Spam:** Only sends one notification per discharge cycle (when threshold is crossed).
* 📱 **Simple Setup:** Just select the sensors you want to monitor.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint URL pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Ffredamn76%2Fhomeassistant-blueprints%2Fblob%2Fmain%2Fautomation%2Fbattery_monitor.yaml)

---

## 🚀 Installation

1. Click the **Import button** above for the blueprint you want.
2. Your Home Assistant instance will open and ask to import.
3. Click **Preview** and then **Import**.
4. Create a new automation using the blueprint!

---
*Created and maintained by @fredamn76.*
