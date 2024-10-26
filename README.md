# M5Env - M5Stack NanoC6 + ENV IV

This repository provides an ESPHome configuration for the M5Stack NanoC6 Dev Kit and the M5Stack ENV IV unit. This setup enables Bluetooth functionality, Wi-Fi connectivity, and environmental monitoring sensors (temperature, humidity, and pressure) for remote monitoring and integration with Home Assistant.

## M5Stack Hardware

This setup is designed to work with the following M5Stack components:

- [M5Stack NanoC6](https://shop.m5stack.com/products/m5stack-nanoc6-dev-kit)
- [M5Stack ENV IV Unit](https://shop.m5stack.com/products/env-iv-unit-with-temperature-humidity-air-pressure-sensor-sht40-bmp280)

## Configuration

The `m5env.yaml` configuration includes:

- **ESP32**: Configured specifically for the M5Stack NanoC6 board with ESP-IDF framework settings. Using `esp32-c6-devkitc-1` with 4MB flash size.
- **Wi-Fi**: Configures the device to connect to a specified SSID with RRM and BTM enabled for improved network performance.
- **Bluetooth Proxy**: Bluetooth Proxy functionality is enabled to allow seamless Bluetooth device integration in Home Assistant.
- **I²C Sensors**:
  - **SHT4x Sensor**: Measures temperature and humidity.
  - **BMP280 Sensor**: Measures atmospheric pressure.
- **API and OTA**: Securely connect and update your device over Wi-Fi.

## Solved Issues

This configuration includes several custom settings and known issues:

- **Bluetooth Compilation**: As of October 2024, ESPHome requires the dev build for Bluetooth functionality. This is needed for the Bluetooth module to compile without issues.
- **Wi-Fi and Bluetooth Interoperability**: For reliable Bluetooth scanning and Wi-Fi performance, the configuration enables BLE scanning only when Wi-Fi is connected (on_connect). When disconnected, BLE scanning is disabled to reduce power and interference issues.
- **I²C Scan Disabled**: The I²C bus scan is disabled to avoid boot loops.

## Installation

As of October 2024, ESPHome requires the dev build for Bluetooth functionality. This is needed for the Bluetooth module to compile without issues

```bash
pip install git+https://github.com/esphome/esphome
```

## Compile & Upload

```bash
esphome compile m5env.yaml
esphome upload m5env.yaml
```
