# 📍 Ultimate Person & Zone Tracker Suite

[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/fredamn76/homeassistant-blueprints/graphs/commit-activity)
[![Home Assistant](https://img.shields.io/badge/Home%20Assistant-Blueprints-blue)](https://www.home-assistant.io/)

<p align="center">
  <img src="https://raw.githubusercontent.com/fredamn76/homeassistant-blueprints/main/images/logo.jpg" width="150" alt="Logo">
</p>

En komplett, helt lokal ersättare till Life360 för Home Assistant. Denna svit av blueprints ger dig avancerad platsövervakning med snygga notiser och hjälper dig samtidigt att hålla koll på enheternas batterinivåer.

---

## 1. 🌍 Person & Zone Tracker (Main)
Detta är kärnan i systemet. En avancerad automation som håller koll på vem som kommer och går, med fokus på integritet och design.

**Funktioner:**
* 📸 **Dynamiska Notiser:** Visar profilbild på den som kommer/går (med fallback till logotyp).
* 📍 **Klickbara Kartor:** Öppna direkt kartan för att se var personen är.
* ⏱️ **Tidsloggning:** "Var borta i 4h 20m" vid avfärd.
* 🛡️ **Smart Logik:** Hanterar "flapping" (GPS-drift) och ignorerar enheter som är otillgängliga.
* 🤫 **Privacy & Quiet Mode:** Stäng av notiser på natten.

[![Import Person Tracker](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/person_zone_tracker.yaml)

---

## 2. 🔋 Battery Monitor (Smart Add-on)
För att tracking ska fungera måste telefonen ha ström. Denna "Smart Alert" varnar dig innan det är för sent.

**Funktioner:**
* 🧠 **Spam-skydd:** Varnar endast en gång per urladdningscykel (inte var 5:e minut).
* 📱 **Anpassad Branding:** Använder samma logotyp och designspråk som trackern.
* ⚙️ **QA-Säkrad:** Fungerar även om många enheter rapporterar samtidigt.

[![Import Battery Monitor](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://github.com/fredamn76/homeassistant-blueprints/blob/main/automation/battery_monitor.yaml)

---

## 🛠️ Installation & Krav

1. Se till att du har **Home Assistant Companion App** installerad på telefonerna.
2. Klicka på "Import blueprint"-knapparna ovan.
3. Skapa en automation från respektive blueprint.
4. (Valfritt) Ladda upp en egen logotyp eller använd vår standard.

---
*QA-Tested on Home Assistant Core 2024.x and Android/iOS Companion Apps.*
