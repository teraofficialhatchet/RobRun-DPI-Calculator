RobRun:

# RobRun DPI Calculator

![Download](https://img.shields.io/badge/Download-Release-e11d48?style=plastic&logo=code&logoColor=white)
&nbsp;&nbsp;![Version](https://img.shields.io/static/v1?label=Version&message=1.2.3&color=brightgreen&style=flat-square&logo=github&logoColor=white)
&nbsp;&nbsp;![Size](https://img.shields.io/static/v1?label=Size&message=3.4MB&color=orange&style=flat&logo=zip&logoColor=white)
&nbsp;&nbsp;![License](https://img.shields.io/static/v1?label=License&message=MIT&color=blue&style=for-the-badge&logo=open-source-initiative&logoColor=white)
&nbsp;&nbsp;![Platform](https://img.shields.io/static/v1?label=Platform&message=Windows+%26+Linux&color=purple&style=plastic&logo=linux&logoColor=white)

---

## Overview

The **RobRun DPI Calculator** is a lightweight companion that converts raw DPI readings from any input device into a calibrated, game‑ready configuration for the *RobRun* series. By loading preset profiles and adjusting sensitivity curves, the calculator eliminates guesswork and ensures consistent aiming across hardware changes. The repository bundles three core configuration files – ``, ``, and `` – alongside a flexible `` template that users can extend for advanced tweaking.

---

## Core Features

- **Structured profile system** – separate files for base defaults, visual feedback, and player‑specific settings keep configurations tidy.
- **Preset workflow** – five ready‑made presets cover common DPI ranges (800, 1200, 1600, 2400, 3200).
- **Precision calculation** – the engine uses a double‑precision algorithm to compute the exact `sensitivity` and `acceleration` values required for a target click‑through rate.
- **Cross‑platform support** – Windows, Linux, and macOS binaries are available; the same configuration files work on all.
- **Extensible scripting hooks** – `` can reference Lua scripts to apply conditional logic, such as day/night mode adjustments.

---

## Installation & Usage

1. Download the latest bundle from the **Download** badge above or visit the release page.
2. Extract the archive to a folder of your choosing (e.g., `C:\RobRun\DPI`).
3. Locate the `config` subfolder; it contains:
   * `` – base sensitivity, acceleration, and general constants.
   * `` – color, cursor shape, and visual aids.
   * `` – player‑specific overrides (e.g., preferred aim mode).
   * `` – an optional blank file for user extensions.
4. Launch the **RobRun DPI Calculator** executable.
5. On the main screen, load the preset that matches your hardware DPI.
6. The calculator will display the recommended `sensitivity`, `acceleration`, and `click‑through` values.
7. Copy the values into the appropriate sections of the target configuration file (usually ``).
8. Restart *RobRun* to apply the new settings.

The calculator’s GUI offers a real‑time preview slider. Adjusting the slider instantly recalculates all dependent values, allowing fine‑tuned experimentation.

---

## Detailed Table of Configuration Parameters

| File | Parameter | Purpose | Typical Value | Notes |
|------|-----------|---------|---------------|-------|
| `` | `sensitivity` | Base click sensitivity | `1.5` | Adjust for baseline DPI. |
| `` | `acceleration` | Mouse acceleration curve | `0.8` | Should be consistent across devices. |
| `` | `cursor_shape` | Cursor icon | `arrow` | Optional: `crosshair`, `dot`. |
| `` | `color_scheme` | UI color palette | `dark` | Matches game theme. |
| `` | `aim_mode` | Preferred aim style | `sniper` | `rifle`, `pistol`. |
| `` | `reticule_size` | Aim reticle dimension | `0.04` | Scales with sensitivity. |
| `` | *user* | Script hook reference | `daynight.lua` | Optional. |

---

## Frequently Asked Questions

**Q1: Why do my click‑through values differ after switching DPI presets?**
A1: The calculator recalculates based on the new DPI. Make sure you replace *all* values in the configuration files, not just sensitivity, to keep acceleration and reticle size in sync.

**Q2: Can I use the calculator on a device that reports DPI in non‑standard units?**
A2: Yes. The algorithm internally normalises any DPI input to a 1‑to‑1 mapping, so long‑range or ultra‑high‑resolution devices will still produce accurate results.

**Q3: Where do I find the script examples?**
A3: Look in the `scripts/` directory. The included Lua files demonstrate how to toggle between day and night visual profiles based on system time.

**Q4: Is the calculator safe for use on multiplayer servers?**
A4: The utility merely adjusts sensitivity and visual settings; it does not alter any in‑game mechanics. No advantage is gained beyond a smoother aim experience.

**Q5: I only want to tweak sensitivity, not acceleration. Can I lock acceleration?**
A5: Open `` and set `acceleration` to `0`. The calculator will respect this constant while recomputing the rest of the parameters.

---

## Troubleshooting

- **Issue:** Configuration file not updated after applying changes.
  **Fix:** Verify that the path to the configuration folder in *RobRun* matches the one you modified. Restart *RobRun* to force a reload.

- **Issue:** Unexpected crash on startup.
  **Fix:** Delete the existing `` and re‑run the calculator to regenerate the file.

- **Issue:** Visual reticle appears too large or small.
  **Fix:** Adjust `reticule_size` in `` by ±0.01 increments until it matches your visual preference.

---

## Contributing

Feel free to open issues for feature requests or bugs. Pull requests that improve the precision algorithm, add new preset files, or expand scripting examples are welcome. Please keep changes within the scope of the existing configuration structure and avoid adding external dependencies.

---

## 📁 Configuration System

```text
configs/
├── default.cfg
├── visual.cfg
├── player.cfg
└── custom.cfg
```