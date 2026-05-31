# Guide 02 — Dirty-Water Tank Reports False Level

[← Repair guides index](README.md) | [← Repository index](../README.md)

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-green) ![Time: 10–20 min](https://img.shields.io/badge/Time-10–20%20min-blue) ![Tools: None required](https://img.shields.io/badge/Tools-None%20required-lightgrey)

---

## Symptoms

- App shows dirty-water tank as **FULL** even after emptying it.
- App shows dirty-water tank as **EMPTY** even when it contains water.
- Dock refuses to begin the mop-wash cycle because it believes the dirty tank is full.
- Mop-wash cycle starts but stops prematurely with a "dirty tank full" notification.

---

## How the float sensor works

The dirty-water tank contains a **sealed magnetic float** — a small buoy that rises with the water level. A reed or Hall-effect sensor in the dock housing reads the magnet's position through the tank wall without any direct contact with the water.

When residue, slime, or debris builds up inside the tank, the float can stick in the raised (FULL) or lowered (EMPTY) position, sending a false reading regardless of actual fill level.

```mermaid
flowchart LR
    FLOAT[Magnetic Float<br/>inside dirty tank]:::primary
    SENSOR[Reed / Hall Sensor<br/>in dock wall]:::compute
    MCU[Dock MCU]:::data
    APP[Xiaomi Home App<br/>level indicator]:::output

    FLOAT -->|magnetic field<br/>through tank wall| SENSOR
    SENSOR -->|digital level signal| MCU
    MCU -->|Wi-Fi / BLE| APP

    classDef primary fill:#ffffff,stroke:#000000,stroke-width:3px,color:#000
    classDef compute fill:#ffcdd2,stroke:#b71c1c,stroke-width:2px,color:#000
    classDef data    fill:#bbdefb,stroke:#0d47a1,stroke-width:2px,color:#000
    classDef output  fill:#b2ebf2,stroke:#006064,stroke-width:2px,color:#000
```

*Float-to-sensor signal path — the float never leaves the tank body.*

![Magnetic float switch schematic](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8b/Float_switch_diagram.svg/480px-Float_switch_diagram.svg.png)
*Generic magnetic float switch principle. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:Float_switch_diagram.svg)*

---

## Root causes

| # | Cause | Likelihood |
|---|-------|-----------|
| A | Float stuck in raised position due to biofilm / mineral scale on float or tank wall | High |
| B | Float stuck in lowered position due to debris wedging it down | Medium |
| C | Dirty-water tank not fully seated — sensor gap too large to read | Medium |
| D | Tank sealing ring missing, deformed, or pinched — tank slightly cocked when inserted | Low |
| E | Firmware glitch — sensor value not refreshed after tank removal | Low |

---

## Troubleshooting decision tree

```mermaid
flowchart TD
    START([Symptom: false level<br/>in dirty-water tank]):::action

    Q1{Did you just empty<br/>and reseat the tank?}:::control
    A_RESEAT[Remove tank, wipe rim<br/>and dock slot, reseat firmly<br/>until it clicks]:::action

    Q2{App still shows<br/>wrong level?}:::control
    A_REBOOT[Reboot dock via app<br/>or power-cycle for 30 s]:::action

    Q3{Still wrong after<br/>reboot?}:::control
    A_INSPECT[Remove tank, inspect<br/>float — can you see it move<br/>freely side to side?]:::action

    Q4{Float moves<br/>freely?}:::control
    A_RINSE[Float is free — check<br/>sealing ring; replace if<br/>deformed, reseat tank]:::action
    A_CLEAN[Float is stuck —<br/>go to Fix A]:::fail

    Q5{Sealing ring OK<br/>and tank clicks in?}:::control
    SOLVED([Issue resolved]):::ok
    SERVICE([Contact Xiaomi support<br/>— sensor fault]):::fail

    START --> Q1
    Q1 -->|NO| A_RESEAT --> Q2
    Q1 -->|YES| Q2
    Q2 -->|NO| SOLVED
    Q2 -->|YES| A_REBOOT --> Q3
    Q3 -->|NO| SOLVED
    Q3 -->|YES| A_INSPECT --> Q4
    Q4 -->|YES| A_RINSE --> Q5
    Q4 -->|NO| A_CLEAN
    Q5 -->|YES| SOLVED
    Q5 -->|NO| SERVICE

    classDef action  fill:#fff9c4,stroke:#f57f17,stroke-width:2px,color:#000
    classDef control fill:#c8e6c9,stroke:#1b5e20,stroke-width:2px,color:#000
    classDef ok      fill:#a5d6a7,stroke:#1b5e20,stroke-width:2px,color:#000
    classDef fail    fill:#ef9a9a,stroke:#b71c1c,stroke-width:2px,color:#000
```

---

## Fixes

### Fix A — Clean the float and tank interior (stuck float)

**Tools:** Warm water, soft bottle brush or sponge, white vinegar or citric acid solution (1 tsp per 500 mL water).

1. Remove the dirty-water tank from the dock by pressing the release tab and sliding it out.
2. Empty any remaining water down the sink.
3. Rinse the interior with warm water to remove loose debris.
4. Fill the tank one-quarter full with a citric acid or diluted white-vinegar solution to dissolve mineral scale.
5. Shake the tank gently for 30 seconds, then tilt it so the solution contacts all inner surfaces.
6. Locate the float (a small cylindrical or spherical buoy, usually white or grey, resting on a vertical guide rail or sliding freely along the tank wall). Push it up and down several times with a finger or the back end of a brush — it should slide without resistance.
7. If the float is still sticky, let the solution soak for 5–10 minutes, then repeat.
8. Rinse thoroughly with clean water at least three times until no vinegar odor remains.
9. Wipe the tank exterior, especially the sensor-contact window (typically a clear or thinned area on one face of the tank).
10. Dry the exterior completely before reinserting.

**Verification:** Reinsert the tank, open the Xiaomi Home app, navigate to Omni Station settings, and confirm the dirty-water level reads correctly. Fill with a small amount of water and re-check that the reading rises.

---

### Fix B — Reseat the tank properly

1. Remove the dirty-water tank fully.
2. Inspect the dock slot for debris or a buildup of fluff that could prevent full insertion.
3. Clean the dock slot rim with a dry cloth.
4. Inspect the tank's sealing ring (O-ring or gasket on the tank spigot/outlet). If it looks flattened, twisted, or cracked, refer to the replacement guide for the sealing ring.
5. Reinsert the tank with both hands, pressing firmly and evenly until you hear or feel a distinct click.
6. Attempt a manual mop-wash cycle from the app to confirm the dock recognizes the tank.

![O-ring cross-section diagram](https://upload.wikimedia.org/wikipedia/commons/thumb/2/27/O-Ring.svg/480px-O-Ring.svg.png)
*O-ring sealing principle — a deformed or missing ring prevents proper seating. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:O-Ring.svg)*

**Verification:** The app level indicator should update within 5 seconds of seating.

---

### Fix C — Firmware-glitch level reset

1. In Xiaomi Home, navigate to **Omni Station > Settings > Maintenance**.
2. Tap **Reset tank status** if available, or perform a **Reset dock** (this does not affect robot settings or maps).
3. Alternatively, unplug the dock power cable for 30 seconds, plug back in, and wait for the dock to complete its boot sequence (LED steady).
4. Remove and reinsert the dirty-water tank once more.

**Verification:** Confirm the level indicator updates immediately.

---

## Preventive tips

- Empty and rinse the dirty-water tank after every 2–3 cleaning sessions, or whenever the app shows it reaching 75% full.
- Use distilled or softened water in the clean-water tank to reduce mineral deposits that migrate into the dirty tank.
- Once a week, shake the dirty tank gently and verify the float moves freely before reinserting.
- Do not use detergents or cleaning agents in the dirty-water tank — doing so can leave a sticky residue that immobilises the float faster.

---

## Related guides

- [Guide 01 — Station not pumping dirty water](01-station-not-pumping-dirty-water.md) — if the pump itself is not moving dirty water out of the wash tray.
- [Guide 03 — No mop-wash water output at dock](03-no-mop-wash-water-output.md) — if no water flows onto the wash tray during the cleaning cycle.
- [Guide 06 — Water leak from dock](06-water-leak-from-dock.md) — if water is escaping from around the dirty-water tank area.

---

## Sources

- Xiaomi Global Support — FAQ KA-605084: [mi.com/global/support/faq/details/KA-605084](https://www.mi.com/global/support/faq/details/KA-605084/)
- Hjalp.ai — Xiaomi Robot Vacuum water tank troubleshooting: [hjalp.ai/article/xiaomi-robot-vacuum-water-tank-not-working](https://www.hjalp.ai/article/xiaomi-robot-vacuum-water-tank-not-working/)
