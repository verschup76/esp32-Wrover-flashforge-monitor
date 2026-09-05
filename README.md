# ESP32 WROVER Flashforge Monitor

ESP32 web monitor for the Flashforge Adventurer 5M/5X with camera support.

The current combined camera + Flashforge monitor project is in [`FlashforgeCamera/`](FlashforgeCamera/). It is prepared for the classic ESP32-WROVER camera layout, not an ESP32-S3.

Hardware reference: ESP32-WROVER camera board.

Required Arduino libraries:

- WebServer
- ArduinoJson
- Preferences

The project uses a separate local `secrets.h` file for Wi-Fi credentials. Copy `FlashforgeCamera/secrets-example.h` to `FlashforgeCamera/secrets.h` and fill in the 2.4 GHz Wi-Fi credentials before compiling. `secrets.h` is excluded from Git.

Runtime URLs after upload:

- Camera control and snapshots: `http://<board-ip>/`
- MJPEG stream: `http://<board-ip>:81/stream`
- Flashforge monitor dashboard: `http://<board-ip>:8081/`

<img width="547" height="993" alt="image" src="https://github.com/user-attachments/assets/619f8fb7-6d2c-4266-9c8e-d37c20d5b8d1" />
