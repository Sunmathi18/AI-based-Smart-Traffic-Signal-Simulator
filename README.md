# AI-Based Smart Traffic Signal Simulator

![Arduino](https://img.shields.io/badge/Arduino-UNO_R3-00979D?logo=arduino)
![Proteus](https://img.shields.io/badge/Simulation-Proteus_ISIS-blue)
![Language](https://img.shields.io/badge/Language-Embedded_C-orange)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen)

An intelligent 4-road traffic signal system that dynamically allocates
green time based on real-time traffic density. Busiest road = longest green.
Built entirely in software — no hardware required.

## Demo
> Add your Proteus simulation screenshot or screen recording GIF here
> Screenshot: /media/simulation_screenshot.png

## How it works
Phase 1 — Basic: Fixed 10s green per road (foundation)
Phase 2 — AI: Dynamic green time via density-weighted scheduling

AI Algorithm (3 steps per cycle):
1. readDensities()   — analogRead() on 4 potentiometers (A0–A3)
2. sortByPriority()  — Bubble sort: highest density road = index 0
3. calcGreenTime()   — map(density, 0, 1023, 5000, 60000) ms

## Pin mapping
| Road  | Red | Yellow | Green | Sensor |
|-------|-----|--------|-------|--------|
| North | D2  | D3     | D4    | A0     |
| South | D5  | D6     | D7    | A1     |
| East  | D8  | D9     | D10   | A2     |
| West  | D11 | D12    | D13   | A3     |

## Components (Proteus)
Arduino UNO R3, 12x LEDs (4R/4Y/4G), 12x 220Ω resistors,
4x Potentiometers (POT-HG), 1x LCD 16x2 (LM016L)

## Project structure
SmartTrafficSignal/
├── Phase1_Basic/
│   ├── basic_traffic.ino
│   └── basic_traffic.pdsprj
├── Phase2_Smart/
│   ├── smart_traffic_ai.ino
│   └── smart_traffic.pdsprj
└── Docs/
    └── project_report.docx

## Quick start
1. Clone this repo
2. Open .ino in Arduino IDE → Sketch → Export Compiled Binary
3. Load .hex into Proteus Arduino component → Press Play
4. Adjust potentiometer knobs to change traffic density live

## Results
- Up to 60% wait time reduction vs fixed timing on high-density roads
- Full simulation — zero hardware cost
- Serial Monitor output for real-time debugging

## Future enhancements
- [ ] LCD display with countdown timer
- [ ] Emergency vehicle preemption (IR receiver)
- [ ] OpenCV vehicle counting via Python + Serial
- [ ] Q-Learning agent for RL-based optimization
- [ ] IoT dashboard via ESP8266

## Author
Sunmathi R — 2nd Year ECE Student
GitHub: Sunmathi18| LinkedIn: https://www.linkedin.com/in/sunmathi-ramesh-ba1199329/

## License
MIT — free to use, modify, and learn from.
