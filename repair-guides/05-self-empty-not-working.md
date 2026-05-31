# Guide 05 — Self-Empty Not Working

[← Repair guides index](README.md) | [← Repository index](../README.md)

![Difficulty: Easy to Hard](https://img.shields.io/badge/Difficulty-Easy%20to%20Hard-orange) ![Time: 10–45 min](https://img.shields.io/badge/Time-10–45%20min-blue) ![Tools: Scissors, flashlight, clean cloth](https://img.shields.io/badge/Tools-Scissors%2C%20flashlight%2C%20cloth-lightgrey)

---

## Symptoms

- Robot docks after cleaning but the **loud auto-empty fan cycle (~10 seconds) is never heard**.
- Robot's **dustbin remains full** after every dock session.
- App shows **Error 9** (dust bag/filter missing or full) or **Error 10** (filter blocked).
- App notification: "Please check the dust bag" or "Auto-empty failed."
- Suction performance during cleaning appears unaffected, but dust never transfers to the dock's bag.

---

## How auto-empty works

When the robot docks after a cleaning run, the Omni Station's auto-empty system activates a dedicated 530 W high-suction fan. This fan creates a strong airflow that evacuates debris from the robot's dustbin through a sealed suction channel into the dock's 2.5 L dust collection bag. A typical cycle lasts approximately 10 seconds.

```mermaid
flowchart LR
    ROBOT_BIN[Robot Dustbin<br/>outlet port]:::input
    SEAL[Rubber Dock-Robot<br/>seal / gasket]:::compute
    CHANNEL[Dock suction<br/>channel / pipe]:::data
    FAN[Auto-empty Fan<br/>530 W motor]:::compute
    FILTER[Dock HEPA filter<br/>downstream of bag]:::compute
    BAG[2.5 L Dust<br/>Collection Bag]:::output
    EXHAUST[Clean air<br/>exhaust]:::output

    ROBOT_BIN -->|debris + air| SEAL
    SEAL -->|sealed airflow| CHANNEL
    CHANNEL --> BAG
    BAG -->|filtered air| FILTER
    FAN -.->|suction force| CHANNEL
    FILTER --> EXHAUST

    classDef input   fill:#ffe0b2,stroke:#e65100,stroke-width:2px,color:#000
    classDef data    fill:#bbdefb,stroke:#0d47a1,stroke-width:2px,color:#000
    classDef compute fill:#ffcdd2,stroke:#b71c1c,stroke-width:2px,color:#000
    classDef output  fill:#b2ebf2,stroke:#006064,stroke-width:2px,color:#000
```

*Auto-empty airflow path from robot dustbin through the dock's sealed channel into the collection bag.*

![HEPA filter illustration](https://upload.wikimedia.org/wikipedia/commons/thumb/3/30/HEPA_Filter_diagram.svg/480px-HEPA_Filter_diagram.svg.png)
*HEPA filter cross-section — the dock filter sits downstream of the bag and must be kept clean. Source: [Wikimedia Commons](https://commons.wikimedia.org/wiki/File:HEPA_Filter_diagram.svg)*

---

## Error codes

| Code | Meaning | First action |
|------|---------|-------------|
| **9** | Dust bag missing, door not closed, or bag full | Replace / reseat bag; close door firmly |
| **10** | Dock HEPA filter blocked | Clean or replace dock filter |

---

## Root causes

| # | Cause | Likelihood |
|---|-------|-----------|
| A | Dust bag full (reached capacity — ~75-day life at daily use) | High |
| B | Dust bag not installed or bag door not fully closed | High |
| C | Clog in robot dustbin outlet port or dock suction channel | Medium |
| D | Rubber seal between robot dustbin port and dock inlet damaged / missing | Medium |
| E | Dock HEPA filter clogged (triggers Error 10) | Medium |
| F | Auto-empty fan motor fault | Low |

---

## Troubleshooting decision tree

```mermaid
flowchart TD
    START([Symptom: auto-empty<br/>fan not audible /<br/>dustbin stays full]):::action

    Q1{Error code shown<br/>in app?}:::control
    E9[Error 9: check bag<br/>— go to Fix A]:::action
    E10[Error 10: check filter<br/>— go to Fix E]:::action

    Q2{Dust bag installed<br/>and door closed?}:::control
    A_BAG[Install new bag<br/>or reseat existing;<br/>close door until click]:::action

    Q3{Auto-empty fan<br/>audible after<br/>bag fix?}:::control

    Q4{Visible clog at<br/>robot dustbin outlet<br/>or dock channel?}:::control
    A_CLOG[Clear clog with<br/>scissors and cloth<br/>— Fix C]:::action

    Q5{Rubber seal between<br/>robot and dock<br/>intact?}:::control
    A_SEAL[Inspect and reseat<br/>or replace seal<br/>— Fix D]:::action

    Q6{Fan audible after<br/>seal fix?}:::control
    SERVICE([Contact Xiaomi support<br/>— fan motor fault]):::fail
    SOLVED([Issue resolved]):::ok

    START --> Q1
    Q1 -->|Error 9| E9 --> Q3
    Q1 -->|Error 10| E10 --> Q3
    Q1 -->|No error| Q2
    Q2 -->|NO| A_BAG --> Q3
    Q2 -->|YES| Q4
    Q3 -->|YES| SOLVED
    Q3 -->|NO| Q4
    Q4 -->|YES| A_CLOG --> Q6
    Q4 -->|NO| Q5
    Q5 -->|NO| A_SEAL --> Q6
    Q5 -->|YES| SERVICE
    Q6 -->|YES| SOLVED
    Q6 -->|NO| SERVICE

    classDef action  fill:#fff9c4,stroke:#f57f17,stroke-width:2px,color:#000
    classDef control fill:#c8e6c9,stroke:#1b5e20,stroke-width:2px,color:#000
    classDef ok      fill:#a5d6a7,stroke:#1b5e20,stroke-width:2px,color:#000
    classDef fail    fill:#ef9a9a,stroke:#b71c1c,stroke-width:2px,color:#000
```

---

## Fixes

### Fix A — Replace or reseat the dust collection bag

The 2.5 L dust bag has an expected life of approximately **75 days** at one cleaning cycle per day. A full bag triggers Error 9 and prevents auto-empty from running regardless of other conditions.

1. Open the Omni Station's dust compartment door (top lid or front panel depending on configuration).
2. Grasp the dust bag by its cardboard collar and pull it straight out. The collar seals the opening automatically to prevent dust release.
3. Dispose of the bag in a bin — do not try to empty and reuse a disposable bag.
4. If installing a new bag: slide the new bag's collar into the dock compartment until it clicks into the inlet port. The collar arrow or alignment indicator should face forward.
5. Close the dust compartment door firmly until it clicks. Confirm it is flush with the dock body.
6. Trigger an auto-empty cycle from the Xiaomi Home app (**Device > Auto-empty > Run now**) or by re-docking the robot.

**Verification:** The fan runs audibly for approximately 10 seconds; the robot's dustbin is empty after the cycle.

---

### Fix B — Close the dust bag door properly

Error 9 is also triggered when the bag door is not fully latched — the dock's lid sensor detects an open door and disables the fan as a safety measure.

1. Press the dust compartment door firmly at both the top and bottom edges until you hear a definite click.
2. Check that no bag collar tab is caught in the door hinge.
3. Trigger an auto-empty cycle and confirm the fan activates.

---

### Fix C — Clear a clog in the suction channel

Clogs most commonly form at two points: the robot's dustbin outlet port (a rectangular or oval opening on the robot's rear/underside), and the dock's suction channel (the internal pipe that connects the robot's outlet to the bag).

1. Remove the robot from the dock.
2. Open the robot's dustbin and inspect the outlet port at the base — look for compressed hair, string, or debris blocking the opening. Use scissors to cut through tangled hair and remove it with tweezers or a cloth.
3. Shine a flashlight into the dock's suction inlet (the recessed opening the robot's dustbin port mates with). If debris is visible, use a thin bottle brush or a folded cloth on a stick to dislodge it. A vacuum cleaner nozzle held to the opening can also extract loose clogs.
4. Check the dock's internal channel as far as is accessible (do not force tools further than the visible channel).
5. Wipe all surfaces with a dry cloth.
6. Replace the robot in the dock and trigger an auto-empty cycle.

**Verification:** Audible fan cycle; dustbin empties completely.

---

### Fix D — Inspect and reseat the rubber seal

The rubber gasket between the robot's dustbin port and the dock inlet creates an airtight seal that is essential for generating sufficient suction. If the seal is torn, missing, or out of position, air bypasses the channel and suction collapses.

1. Remove the robot from the dock.
2. Inspect the rubber seal around the dock's suction inlet — it should be a continuous ring with no tears, cracks, or compressed flat spots.
3. If the seal has slipped out of its groove, press it firmly back in with your fingers, working around the circumference.
4. If the seal is torn or missing, contact Xiaomi support or your retailer for a replacement part — this seal is not user-serviceable with improvised materials.
5. Re-dock the robot and trigger an auto-empty cycle.

**Verification:** The connection point between robot and dock should feel tight with no air gap visible; fan cycle completes successfully.

---

### Fix E — Clean the dock HEPA filter (Error 10)

The HEPA filter downstream of the dust bag captures fine particles that pass through. When it is clogged, static back-pressure prevents the fan from evacuating the dustbin and triggers Error 10.

1. Open the dust compartment and remove the dust bag.
2. Locate the HEPA filter behind or beneath the bag chamber (a flat, pleated filter panel — typically grey or white).
3. Remove the filter by sliding it out or unlatching its frame.
4. Tap the filter gently over a bin to dislodge loose dust. Do not wash the HEPA filter with water unless the filter is specifically labelled as washable.
5. If the filter is heavily loaded or deformed, replace it with a genuine Xiaomi replacement filter.
6. Reinstall the filter, replace the dust bag, close the door, and trigger an auto-empty cycle.

**Verification:** Error 10 clears; fan runs without unusual noise.

---

## Preventive tips

- Replace the dust bag every 60–75 days, or when the app shows the bag at 80% capacity, whichever comes first.
- Clean the dock HEPA filter every 2–3 bag changes, or when Error 10 appears.
- Inspect the robot's dustbin outlet port and the dock's suction seal monthly — hair and string accumulate at this junction.
- After picking up unusually large amounts of debris (e.g., after renovations or pet shedding season), run an immediate manual auto-empty cycle to prevent the channel from compacting.
- Use only genuine Xiaomi dust bags — third-party bags may have poorly fitting collars that break the seal and trigger Error 9.

---

## Related guides

- [Guide 04 — Mop not wetting floor](04-mop-not-wetting-floor.md) — if the robot's mop system is the problem area.
- [Guide 06 — Water leak from dock](06-water-leak-from-dock.md) — if water is also escaping from the dock simultaneously.

---

## Sources

- Xiaomi error codes 9 and 10: referenced in Xiaomi Home app in-app help.
- Hjalp.ai — Xiaomi Robot Vacuum troubleshooting general reference: [hjalp.ai/article/xiaomi-robot-vacuum-water-tank-not-working](https://www.hjalp.ai/article/xiaomi-robot-vacuum-water-tank-not-working/)
- Xiaomi Robot Vacuum 5 Pro product image: [cdn.webshopapp.com/shops/210536/files/485685171/1652x1652x2/xiaomi-xiaomi-robot-vacuum-5-pro-eu.jpg](https://cdn.webshopapp.com/shops/210536/files/485685171/1652x1652x2/xiaomi-xiaomi-robot-vacuum-5-pro-eu.jpg)
