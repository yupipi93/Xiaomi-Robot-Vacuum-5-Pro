[← Repository index](../README.md)

# Error Codes Reference — Xiaomi Robot Vacuum 5 Pro

Error codes appear in two places:

- **Xiaomi Home app** — a banner or push notification with a numeric code and short description. Tap the notification for a built-in help snippet.
- **Voice prompt** — the robot speaks the error number in the configured language (e.g. "Error 5, please check the main brush").

> **5 Pro note on pump and tank faults:** The 5 Pro's docking-station pump and water-tank errors are often surfaced as **app notifications or status alerts** rather than a discrete numeric code. If you see an alert about the dirty-water tank, clean-water level, or pump without a numeric code, go directly to [Guide 01](01-station-not-pumping-dirty-water.md) or [Guide 02](02-dirty-water-tank-false-level.md).

---

## Error code table

| Code | Meaning | Likely cause | What to do | Related guide |
|------|---------|--------------|------------|---------------|
| **1** | LiDAR obstruction | LiDAR lens dirty; object too close to turret; turret physically blocked | Wipe LiDAR lens and turret with a dry microfibre cloth; remove any object within 0.5 m of the robot top | [14 — Sensors](14-sensors-dirty-errors.md) |
| **2** | Collision sensor / bumper jammed | Debris wedged in bumper gap; bumper physically compressed | Press and release the bumper along its full length; clear any debris caught in the gap | [14 — Sensors](14-sensors-dirty-errors.md) |
| **3** | Drive wheel suspended or stuck | Robot placed on uneven surface, step, or low-clearance area; wheel mechanism jammed | Move robot to a flat, clear surface; check wheels turn freely by hand | [14 — Sensors](14-sensors-dirty-errors.md) |
| **4** | Cliff sensor dirty | Underside IR cliff sensors fouled with dust, pet hair, or carpet fluff | Clean the four underside IR sensor windows with a dry microfibre cloth | [14 — Sensors](14-sensors-dirty-errors.md) |
| **5** | Main brush clogged or jammed | Hair / thread wrapped around axle; bearing seized | Remove main brush, cut and clear all entangled debris, clean axle and end-cap bearings | [07 — Main brush](07-main-brush-tangle.md) |
| **6** | Side brush obstructed or stalled | Debris caught under side-brush mount; bristles bent into mount hole | Remove side brush (1 Phillips screw), clear debris, reinstall | [08 — Side brush](08-side-brush-obstruction.md) |
| **7** | Drive wheel entangled | Cable, string, or hair wrapped around wheel axle | Remove robot from dock, turn upside down, remove wheel cover and clear entanglement | [14 — Sensors](14-sensors-dirty-errors.md) |
| **8** | Insufficient clearance / robot stuck | Robot wedged under furniture or in a tight corridor | Clear the area; add a virtual wall in the Xiaomi Home app to prevent re-entry | [11 — Navigation](11-navigation-lost-low-clearance.md), [14 — Sensors](14-sensors-dirty-errors.md) |
| **9** | Dust bag / filter missing or full | Station bag not installed or at capacity; HEPA filter absent | Install or replace the station bag; confirm filter is seated correctly | [05 — Self-empty](05-self-empty-not-working.md), [09 — Suction](09-suction-loss.md) |
| **10** | Filter clogged | HEPA filter blocked with fine dust | Remove filter, rinse under cold water, air-dry for at least 24 hours, then reinstall | [09 — Suction](09-suction-loss.md) |
| **11** | Virtual wall / magnetic-strip interference | Robot stopped by a magnetic boundary strip that is mispositioned or damaged | Move or remove the conflicting magnetic tape; use app-based virtual walls instead | — |
| **12** | Battery critically low | Battery discharged below safe threshold | Return robot to dock immediately; do not interrupt the charge cycle | [15 — Battery](15-battery-degradation.md) |
| **13** | Charging contact issue | Contacts on robot underside or dock plate dirty or oxidised | Wipe both contact sets with a dry cloth or isopropyl-alcohol swab; let dry before docking | [10 — Charging](10-charging-failure.md) |
| **14** | Battery temperature fault / battery error | Battery too hot or too cold to charge safely; persistent hardware fault | Allow robot to rest at room temperature (15–35 °C) for 30 minutes, then retry. If error persists, inspect battery health | [10 — Charging](10-charging-failure.md), [15 — Battery](15-battery-degradation.md) |
| **15** | Wall / PSD (proximity) sensor dirty | Side-wall proximity sensor window fouled | Wipe the PSD sensor window on the robot's right side with a dry microfibre cloth | [14 — Sensors](14-sensors-dirty-errors.md) |
| **16** | Uneven surface / unstable footing | Robot started on a rug edge, threshold, or incline it cannot self-level on | Move robot to a flat hard-floor surface and restart the cleaning cycle | — |
| **17** | Side brush malfunction | Side brush motor fault or brush not spinning after clearing debris | Reset the robot (hold power button 5 s); if error returns after clearing debris, motor may need replacement | [08 — Side brush](08-side-brush-obstruction.md) |
| **18** | Suction fan error | Fan impeller blocked by debris; motor overcurrent | Reset robot; check suction inlet for blockage. If error persists the fan module requires service | [09 — Suction](09-suction-loss.md) |
| **19** | No current at charging base | Dock power adapter unplugged or failed; power outlet dead | Check dock power cord and wall outlet; test outlet with another device; try a replacement adapter | [10 — Charging](10-charging-failure.md) |
| **20** | Water tank / pump error *(older models)* | On older Mi Robot models this is a water-tank or pump fault. **On the 5 Pro**, this fault typically surfaces as an app notification rather than code 20. | See app alert text; follow pump/tank troubleshooting | [01 — Pump](01-station-not-pumping-dirty-water.md), [02 — Level sensor](02-dirty-water-tank-false-level.md) |
| **21** | LiDAR physically pressed or interfered | Object resting on top of robot pressing the LiDAR turret; low ceiling | Remove any object from the robot top; ensure ceiling height above robot exceeds 30 cm | [14 — Sensors](14-sensors-dirty-errors.md) |
| **22** | Charging contact contamination | Dock contact plate heavily soiled or corroded | Wipe dock contact area with isopropyl-alcohol swab; let dry fully before next docking attempt | [10 — Charging](10-charging-failure.md) |
| **23** | Dock infrared signal blocked | Object in front of dock blocking homing beam; direct sunlight hitting dock IR windows | Clear a 0.5 m radius in front of dock; move dock away from windows or strong light sources | [10 — Charging](10-charging-failure.md) |

---

## Quick lookup by symptom area

| If the robot... | Likely codes | Primary guide |
|-----------------|-------------|---------------|
| Stops during cleaning with voice alert | 1, 2, 3, 4, 7, 8, 15, 16, 21 | [14 — Sensors](14-sensors-dirty-errors.md) |
| Reports a brush or fan fault | 5, 6, 17, 18 | [07](07-main-brush-tangle.md), [08](08-side-brush-obstruction.md), [09](09-suction-loss.md) |
| Will not charge or shows battery error | 12, 13, 14, 19, 22, 23 | [10 — Charging](10-charging-failure.md), [15 — Battery](15-battery-degradation.md) |
| Reports a filter or bag fault | 9, 10 | [05 — Self-empty](05-self-empty-not-working.md), [09 — Suction](09-suction-loss.md) |
| App notification about pump or water tank (no numeric code) | — | [01 — Pump](01-station-not-pumping-dirty-water.md), [02 — Level sensor](02-dirty-water-tank-false-level.md) |

---

## Sources

- Error code definitions: <https://finderrorcode.com/xiaomi-mi-vacuum-cleaner-error-codes.html>
- Official Xiaomi support FAQ: <https://www.mi.com/global/support/faq/details/KA-617911/>

---

## Related resources

- [Repair Guides index](README.md)
- [Common Problems Overview](common-problems-overview.md)
- [Architecture Overview](../docs/architecture-overview.md)
- [Technical Specifications](../docs/technical-specifications.md)
- [Replacement Guides](../replacement-guides/README.md)
