# LDR Interfacing — Arduino UNO R4 WiFi

Short project: read an LDR (light-dependent resistor) with an Arduino UNO R4 WiFi and report values over the serial monitor.

## Project structure
- `platformio.ini` — PlatformIO project configuration (board, environment, monitor speed).
- `src/main.cpp` — Main sketch (application logic).
- `lib/` — Place any additional libraries here (currently unused).

## Quick checklist (what this README covers)
- Using CLion (how to open and run the project)
- Recommended IDE version and PlatformIO tooling
- Where the code lives and how to build/upload
- Libraries & dependencies (PlatformIO & Arduino core)
- Hardware components and wiring
- Author and contact
- Software and hardware requirements

## Using CLion
1. Install CLion (see "Software requirements" below).
2. Open CLion and choose `Open` → select this project folder (the folder that contains `platformio.ini`).
3. Recommended workflow:
   - Use the integrated Terminal for PlatformIO CLI commands (recommended):
     - Build: `pio run`
     - Upload: `pio run -e uno_r4_wifi -t upload`
     - Serial monitor: `pio device monitor -p COM11 -b 9600` (adjust COM port as needed)
   - If you prefer an IDE integration, install PlatformIO Core (CLI) and use the PlatformIO CLion plugin if available. Note: plugin availability/compatibility may vary; using the CLI is the most reliable approach.

## Recommended IDE and versions
- CLion 2022.3 or newer is recommended (newer is fine). If you use older CLion versions, prefer using the PlatformIO CLI in Terminal.
- PlatformIO Core (CLI) — latest stable (PlatformIO Core 6.x or newer recommended).
- Python 3.8 or newer (for PlatformIO Core).

Note: If you have a specific CLion version you must use, replace the above with your preferred version.

## Code — where and how to build/run
- Main source: `src/main.cpp`.
- Build with PlatformIO (from project root):
  - `pio run` — build the default environment
  - `pio run -e uno_r4_wifi -t upload` — build and upload to the UNO R4 WiFi board
  - `pio device monitor -p <PORT> -b <BAUD>` — open serial monitor (project `platformio.ini` uses `monitor_speed = 9600` and `COM11` by default)

Replace `<PORT>` with your actual COM port (e.g., `COM11`) and `<BAUD>` with `9600` (or the baud rate set in your sketch).

## Libraries & Dependencies
- This project uses the Arduino framework (configured in `platformio.ini`):
  - `platform = renesas-ra`
  - `board = uno_r4_wifi`
  - `framework = arduino`
- No extra third-party PlatformIO libraries are required by default. If you add libraries, declare them in `platformio.ini` under `lib_deps` or put them into the `lib/` folder.

## Components (hardware used)
- Arduino UNO R4 WiFi (board)
- LDR (photoresistor)
- 10 kΩ resistor (recommended for voltage divider)
- Breadboard and jumper wires
- USB cable for power/programming

Wiring (voltage divider):
1. Connect one leg of the LDR to 5V.
2. Connect the other leg of the LDR to the Analog input pin (A0) and to the top of the 10 kΩ resistor.
3. Connect the bottom of the 10 kΩ resistor to GND.
4. This makes a voltage divider; measure the middle node at A0.

Pin notes: the UNO R4 WiFi exposes standard Arduino analog pins (A0, A1, ...). Adjust `src/main.cpp` if you use a different analog pin.

## Software & Hardware Requirements
- OS: Windows, macOS, or Linux (this repository was prepared on Windows).
- CLion 2022.3+ (recommended) or any editor + PlatformIO CLI
- PlatformIO Core (CLI) installed: https://platformio.org/install/cli
- Python 3.8+
- USB drivers for your board (Windows: ensure the correct COM driver is installed)
- Arduino UNO R4 WiFi board and components listed above

## Author
- Author: Your Name <you@example.com>

(Replace with your actual name and contact information.)

## Quick start (example)
1. Connect the UNO R4 WiFi via USB.
2. Open terminal in project root.
3. Build: `pio run`
4. Upload: `pio run -e uno_r4_wifi -t upload`
5. Monitor serial output: `pio device monitor -p COM11 -b 9600`

## Troubleshooting
- If upload fails, confirm the correct COM port and that no other program (e.g., another serial monitor) holds the port.
- If serial output is empty, confirm `monitor_speed` in `platformio.ini` and the baud rate in `src/main.cpp` match.
- If the board is not detected, install/update USB drivers and make sure the board is powered.

## Next steps / Improvements
- Add a circuit diagram image into `assets/` and reference it here.
- Add a sample data-logging script or a web dashboard using UNO R4 WiFi network features.

---
License: Add a `LICENSE` file if you want to publish this project (e.g., MIT).
