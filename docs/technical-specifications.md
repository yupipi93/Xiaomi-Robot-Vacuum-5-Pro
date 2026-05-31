# Xiaomi Robot Vacuum 5 Pro — Technical Specifications

[← Back to repository index](../README.md)

This document is the comprehensive specification sheet for the **Xiaomi Robot Vacuum 5 Pro** robot vacuum and its **Omni Station** self-maintenance dock. All figures are taken from Xiaomi's official global specifications and corroborated by independent reviews; where the official figure and the measured figure differ, both are stated with an explanation. For the system architecture (subsystem diagrams, water circuits, dock cycle), see [architecture-overview.md](./architecture-overview.md).

![Xiaomi Robot Vacuum 5 Pro robot seated in its white Omni Station dock, front three-quarter view](https://cdn.webshopapp.com/shops/210536/files/485685171/1652x1652x2/xiaomi-xiaomi-robot-vacuum-5-pro-eu.jpg)
*Xiaomi Robot Vacuum 5 Pro with Omni Station. Source: [retailer product image](https://cdn.webshopapp.com/shops/210536/files/485685171/1652x1652x2/xiaomi-xiaomi-robot-vacuum-5-pro-eu.jpg).*

---

## 1. Overview & model numbers

The Xiaomi Robot Vacuum 5 Pro launched globally in September 2025. It pairs a LiDAR-navigated robot with a triple-camera 3D obstacle-avoidance system (the headline differentiator of the *Pro* variant) and a fully automated **Omni Station** dock that empties dust, washes and hot-air-dries the mop pads, and recharges the robot.

| Attribute | Value |
|-----------|-------|
| Product name | Xiaomi Robot Vacuum 5 Pro |
| Robot model (global) | OV21GL |
| Robot model (EU) | BHR07WFEU |
| Dock model (Omni Station) | OV21-JZEU |
| Launch | September 2025 |
| Companion app | Xiaomi Home |
| Voice assistants | Amazon Alexa, Google Assistant |

> **Note:** This is the *Pro* model. It is distinct from the standard Robot Vacuum 5 and from the X-series and S-series. See [§10 Model disambiguation](#10-model-disambiguation).

---

## 2. Robot — full specification

| Specification | Value |
|---------------|-------|
| Diameter × height | Φ350 × 88 mm (106 mm with the LiDAR turret raised) |
| Weight | 3.97 kg |
| Suction power | 20,000 Pa |
| Suction modes | 4 — Silent / Standard / Strong / Turbo |
| Battery (nominal) | 5,200 mAh |
| Battery (rated) | 4,800 mAh |
| Battery chemistry / voltage | Li-ion, 14.4 V |
| Charge input voltage | 20 V DC |
| Rated power | 55 W |
| Runtime | Up to 140 min |
| Full charge time | ≤ 6 h rated (≈ 4 h measured) |
| Robot dustbin capacity | 290 mL |
| Internal mop water reservoir | 70–80 mL |
| Filter | E11 washable HEPA |
| Main brush | Dual-blade anti-tangle rubber |
| Side brush | Single extendable anti-tangle arm |
| Mop system | Dual rotating/oscillating microfiber pads on a retractable arm |
| Mop lift over carpet | 15 mm (triggered by ultrasonic carpet sensor) |
| Max climbable obstacle | 20 mm |
| Min under-furniture clearance | 9.5 cm |

> **Note:** With the LiDAR turret retracted the robot is 88 mm tall, which sets the practical clearance for sliding under low furniture; the 106 mm figure applies only while the turret is raised during navigation.

---

## 3. Omni Station (dock) — full specification

| Specification | Value |
|---------------|-------|
| Dock model | OV21-JZEU |
| Dimensions (with ramp) | 470 × 360 × 572 mm |
| Dimensions (without ramp) | 260 × 360 × 572 mm |
| Weight | ~11.5 kg |
| Dust bag capacity | 2.5 L (~75 days typical use) |
| Clean water tank | 4 L |
| Dirty water tank | 3.8 L (primary figure) |
| Hot-water mop wash temperature | 80 °C |
| Heating element power | 1,600 W |
| Hot-air mop drying | ~2 h |
| Drying + charging combined power | 85 W |
| Auto-empty power | 530 W |
| Auto-empty duration | ~10 s |
| Dock input | 220–240 V~, 50/60 Hz |
| Charging output | 20 V DC, 1.5 A |
| Wash tray | Detachable, with asynchronous floating dual scrapers |
| Ramp | Detachable |
| Dirty-water transfer | Negative-pressure **air** pump (not a liquid/peristaltic pump) |
| Full / removal detection | Sealed magnetic float in dirty-water tank |

> **Note (tank capacity discrepancy):** Some EU spec sheets round the dirty-water tank to **4 L**. The accurate figure is **3.8 L**; we state 3.8 L as primary and note the 4 L rounding so technicians are not surprised by either value.

> **Warning — water only:** Use plain water in the clean-water tank. Adding detergent or any cleaning agent damages the dock's pump. See the [Xiaomi support FAQ](https://www.mi.com/global/support/faq/details/KA-617911/).

---

## 4. Navigation & sensors

| Sensor / system | Type | Function |
|-----------------|------|----------|
| LiDAR turret | Retractable dToF (direct Time-of-Flight) | Primary room mapping & localization |
| LDS | Laser Distance Sensor | Distance/edge ranging |
| Gyroscope | Inertial | Heading & motion tracking |
| Front RGB camera | 5 MP HD | AI object recognition + 1080p remote home-view |
| IR stereo cameras | 2× infrared | Binocular 3D depth perception |
| IR 3D dot projector | Structured-light IR | 3D point cloud for obstacle shape/depth |
| PSD edge sensor | Position Sensitive Detector | Wall/edge following |
| Ultrasonic carpet detector | Ultrasonic | Detects carpet → lifts mop, boosts suction |
| Cliff sensors | IR drop sensors | Prevents falls down stairs |
| Front bumper | Mechanical | Physical contact detection |

The **5 Pro exclusive** obstacle-avoidance package combines the 5 MP front RGB camera, the two IR stereo cameras, and the IR 3D dot projector into a *triple-camera binocular 3D system*. The on-device AI recognizes **200+ object types** and **47 dirt types**, adjusting routing and cleaning intensity accordingly.

![Direct Time-of-Flight LiDAR principle — a laser pulse is timed on its round trip to measure distance](https://upload.wikimedia.org/wikipedia/commons/c/cc/20200501_Time_of_flight.svg)
*Time-of-flight ranging principle, as used by the robot's dToF LiDAR turret. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:20200501_Time_of_flight.svg).*

> **Note:** The 5 MP front camera doubles as a remote *home-view* feature in Xiaomi Home: 1080p live video, two-way audio, and night vision. Treat it as a privacy-sensitive component when servicing.

---

## 5. Cleaning system

### 5.1 Vacuum

| Item | Detail |
|------|--------|
| Peak suction | 20,000 Pa |
| Modes | Silent, Standard, Strong, Turbo |
| Main brush | Dual-blade anti-tangle rubber, full-width |
| Side brush | Single extendable anti-tangle arm (reaches into corners) |
| Onboard dustbin | 290 mL, auto-emptied at the dock |
| Filter | E11 washable HEPA |

### 5.2 Mop

| Item | Detail |
|------|--------|
| Pads | Dual rotating/oscillating microfiber pads |
| Mounting | Retractable arm |
| Carpet handling | Lifts 15 mm when ultrasonic sensor detects carpet |
| Onboard water | 70–80 mL internal reservoir, refilled at the dock |
| Wash / dry | Performed at the Omni Station (80 °C wash, ~2 h hot-air dry) |

![Microfiber mop pads, the same pad material used on rotating robot mop modules](https://upload.wikimedia.org/wikipedia/commons/4/4a/Microfiber_cloths.jpg)
*Microfiber pad material, representative of the robot's dual rotating mop pads. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Microfiber_cloths.jpg).*

---

## 6. Connectivity & app

| Feature | Detail |
|---------|--------|
| Wi-Fi | **2.4 GHz only** — 802.11 b/g/n/ax |
| Bluetooth | 5.2 |
| App | Xiaomi Home |
| Voice control | Amazon Alexa, Google Assistant |
| Remote camera | 1080p home-view, two-way audio, night vision |

> **Warning:** The robot connects to **2.4 GHz Wi-Fi only**. It will not join a 5 GHz-only SSID. On combined-band routers, ensure the 2.4 GHz band is enabled and reachable during setup.

---

## 7. Power & consumption

| Function | Power | Notes |
|----------|-------|-------|
| Robot rated power | 55 W | During cleaning |
| Robot charge input | 20 V DC | From dock contacts |
| Dock charging output | 20 V DC, 1.5 A | To robot |
| Dock mains input | 220–240 V~, 50/60 Hz | EU |
| Hot-water heater | 1,600 W | 80 °C mop wash |
| Auto-empty fan | 530 W | ~10 s per cycle |
| Hot-air dry + charge | 85 W | Combined, ~2 h drying |

### Noise

| Figure | Value | Context |
|--------|-------|---------|
| Official | 70 dB | Maximum (Turbo mode) |
| Measured (standard) | 38–44 dB(A) | Typical standard-mode cleaning |
| Measured peaks | 54 dB | Transient peaks during cleaning |
| Auto-empty | 61 dB | During the ~10 s dustbin emptying |

> **Note:** The 70 dB official rating is the worst-case Turbo figure. In everyday Standard mode the robot is far quieter (38–44 dB(A)); brief 54 dB peaks and a louder 61 dB auto-empty burst are normal and short.

---

## 8. Consumables & maintenance intervals

| Part | Recommended interval |
|------|----------------------|
| Main brush | Clean weekly; replace every 6–12 months |
| Side brush | Clean weekly; replace every 3–6 months |
| E11 HEPA filter | Wash monthly (dry fully); replace every 3–6 months |
| Mop pads | Wash after each cycle (automatic); replace every 1–3 months |
| Robot dustbin | Empty automatically at dock; rinse monthly |
| Dock dust bag (2.5 L) | Replace ~every 75 days (when full) |
| Clean water tank (4 L) | Refill as needed; rinse periodically |
| Dirty water tank (3.8 L) | Empty regularly; rinse to prevent odor |
| Wash tray + scrapers | Detach and rinse weekly |
| Sensors (cliff, PSD, cameras) | Wipe with dry/microfiber cloth monthly |
| Charging contacts | Wipe clean monthly |

> **Warning:** Wash the E11 HEPA filter with **water only** and let it dry completely (24 h) before reinstalling. Installing a damp filter promotes mold and reduces suction.

---

## 9. Box contents

| Item | Qty |
|------|-----|
| Robot Vacuum 5 Pro | 1 |
| Omni Station dock | 1 |
| Detachable ramp | 1 |
| Dust bag (pre-installed) | 1 |
| Main brush (pre-installed) | 1 |
| Side brush | 1 (+ spare in some regions) |
| Mop pads | 1 set |
| Power cable | 1 |
| User manual / quick-start guide | 1 |

> **Note:** Exact in-box spares (extra side brush, spare filter, spare dust bag) vary by region and retailer bundle.

---

## 10. Model disambiguation

The 5 Pro is frequently confused with adjacent Xiaomi models. Key distinctions:

| Model | Versus the 5 Pro |
|-------|------------------|
| Robot Vacuum **5** (non-Pro) | Lacks the triple-camera binocular 3D obstacle-avoidance system and the 5 MP home-view camera that define the *Pro*. |
| Robot Vacuum **X20 Max** | Different X-series platform/dock generation; not the OV21 hardware family. |
| Robot Vacuum **X10** | Earlier X-series model; lower suction and different navigation/dock. |
| Robot Vacuum **S10** | Entry/mid S-series; different suction class and no Omni Station with hot-water wash. |

> **Note:** When ordering parts, match the robot model **OV21GL / BHR07WFEU** and dock model **OV21-JZEU**. Parts from the non-Pro 5, X20 Max, X10, or S10 are not guaranteed to be compatible.

---

## 11. Sources

- [Xiaomi — Robot Vacuum 5 Pro official specifications](https://www.mi.com/global/product/xiaomi-robot-vacuum-5-pro/specs/)
- [Xiaomi support — care / water-only FAQ (KA-617911)](https://www.mi.com/global/support/faq/details/KA-617911/)
- [NotebookCheck — Xiaomi Robot Vacuum 5 Pro review](https://www.notebookcheck.net/Good-vacuuming-robot-with-minor-issues-Xiaomi-Robot-Vacuum-5-Pro-review.1208850.0.html)
- [MightyGadget — Xiaomi Robot Vacuum 5 review](https://mightygadget.com/xiaomi-robot-vacuum-5-review/)
- [Gizmochina — global launch coverage](https://www.gizmochina.com/2025/09/26/xiaomi-robot-vacuum-5-pro-launched-globally/)
- [SpecsVersus — Robot Vacuum 5 Pro](https://specsversus.com/items/xiaomi/robot-vacuum-5-pro)
