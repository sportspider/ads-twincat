# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.9.0] - 2026-02-12

### Added
- Binary Sensors: Monitor boolean PLC variables
- Sensors: Read numeric values from PLC with support for various data types (INT, UINT, DINT, REAL, LREAL, etc.)
- Switches: Control boolean PLC variables
- Lights: Control lights with optional brightness support
- Covers: Control blinds, shutters, and other covers with position support
- Valves: Control valve devices
- Select: Control enum/selection variables
- Support for multiple ADS data types including boolean, integer types, real numbers, strings, and time/date types
- Service `ads_twincat.write_data_by_name` for writing values to PLC variables
- Configuration via UI (config flow)
- YAML configuration support (legacy)
- HACS integration support

[0.9.0]: https://github.com/sportspider/ads-twincat/releases/tag/v0.9.0