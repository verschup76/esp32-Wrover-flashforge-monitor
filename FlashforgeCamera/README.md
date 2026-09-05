# Flashforge Camera Monitor

This folder is now a single Arduino sketch combining:

- ESP32 camera initialization using the pin map in `board_config.h`
- The Espressif camera web server from `app_httpd.cpp`
- The Flashforge AD5X monitor dashboard and printer telemetry
- Multi-printer and IFS settings stored in NVS

## Build target

The supplied pin map is the classic ESP32/WROVER-style camera layout, matching the ESP32-D0WD-V3 camera board. It is not an ESP32-S3 target.

Arduino board settings:

- Board: ESP32 Wrover Module / `esp32:esp32:esp32`
- PSRAM: Enabled
- Flash mode: DIO
- Partition scheme: Custom
- Custom partition file: `partitions.csv`

Install the ArduinoJson library before compiling.

## Runtime URLs

After boot, the serial monitor reports the assigned IP:

- Camera control/snapshot server: `http://<board-ip>/`
- MJPEG camera stream: `http://<board-ip>:81/stream`
- Flashforge monitor dashboard: `http://<board-ip>:8081/`
- SD-card browsing is intentionally not included; the board is not assumed to have an SD card.

The monitor dashboard's printer management screen is used to enter the printer name and IP address. Printer control commands remain on the local printer TCP port 8899.

## Files

- `FlashforgeCamera.ino` — combined application, camera initialization, monitor server, and printer telemetry
- `app_httpd.cpp` — camera control, snapshot, and stream handlers
- `board_config.h` — active camera pin map
- `camera_index.h` — camera web UI assets
- `camera_pins.h` — reference camera pin maps
- `partitions.csv` — custom partition layout
- `CameraWebServer.ino.disabled` — preserved original camera-only sketch; not compiled

The previous folder state is preserved at:

`/ASTRO7/ESP32/FlashforgeCamera.before-camera-monitor-merge-20260905`

Wi-Fi credentials are still present in the sketch for compatibility with the existing working setup. They should be moved to a protected local secrets file and rotated if this folder is ever shared outside the trusted network.
