# ADS TwinCAT

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)
[![GitHub Release](https://img.shields.io/github/v/release/sportspider/ads-twincat)](https://github.com/sportspider/ads-twincat/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Home Assistant custom integration for Beckhoff TwinCAT devices using the ADS (Automation Device Specification) protocol.

## Features

- **Binary Sensors**: Monitor boolean PLC variables
- **Sensors**: Read numeric values from PLC with support for various data types (INT, UINT, DINT, REAL, LREAL, etc.)
- **Switches**: Control boolean PLC variables
- **Lights**: Control lights with optional brightness support
- **Covers**: Control blinds, shutters, and other covers with position support
- **Valves**: Control valve devices
- **Select**: Control enum/selection variables

## Installation

### HACS (Recommended)

1. Make sure you have [HACS](https://hacs.xyz/) installed
2. Add this repository as a custom repository in HACS:
   - Go to HACS → Integrations → ⋮ (three dots menu) → Custom repositories
   - Add `https://github.com/sportspider/ads-twincat` as repository
   - Select "Integration" as category
3. Click Install
4. Restart Home Assistant

### Manual Installation

1. Download the latest release from [GitHub releases](https://github.com/sportspider/ads-twincat/releases)
2. Extract the `custom_components/ads_twincat` folder to your Home Assistant's `custom_components` directory
3. Restart Home Assistant

## Configuration

### Via UI (Recommended)

1. Go to Settings → Devices & Services → Add Integration
2. Search for "ADS TwinCAT"
3. Enter your TwinCAT device connection details:
   - **Device/Net ID**: The AMS Net ID of your TwinCAT device (e.g., `1.2.3.4.5.6`)
   - **Port**: The ADS port (default: 48898 for TwinCAT 3)
   - **IP Address**: (Optional) The IP address of the TwinCAT device

4. After the integration is set up, you can add entities through the integration options.

### YAML Configuration (Legacy)

You can also configure the integration via `configuration.yaml`:

```yaml
ads_twincat:
  device: "1.2.3.4.5.6"
  port: 48898
  ip_address: "192.168.1.100"  # Optional
```

## Supported Data Types

- `bool` - Boolean
- `byte` - Byte (8-bit)
- `int` - Integer (16-bit signed)
- `uint` - Unsigned Integer (16-bit)
- `sint` - Short Integer (8-bit signed)
- `usint` - Unsigned Short Integer (8-bit)
- `dint` - Double Integer (32-bit signed)
- `udint` - Unsigned Double Integer (32-bit)
- `word` - Word (16-bit)
- `dword` - Double Word (32-bit)
- `real` - Real (32-bit float)
- `lreal` - Long Real (64-bit float)
- `string` - String
- `time` - Time
- `date` - Date
- `dt` - Date and Time
- `tod` - Time of Day

## Services

### `ads_twincat.write_data_by_name`

Write a value to a PLC variable.

| Field | Required | Description |
|-------|----------|-------------|
| `adsvar` | Yes | The name of the PLC variable (e.g., `.global_var`) |
| `adstype` | Yes | The data type of the variable |
| `value` | Yes | The value to write |

Example:
```yaml
service: ads_twincat.write_data_by_name
data:
  adsvar: ".myGlobalVar"
  adstype: int
  value: 42
```

## Requirements

- Beckhoff TwinCAT 2 or TwinCAT 3 PLC
- ADS route configured between Home Assistant and the TwinCAT device
- The `pyads` Python library (automatically installed)

## Troubleshooting

### Connection Issues

1. Ensure an ADS route is configured on your TwinCAT device pointing to your Home Assistant instance
2. Verify the AMS Net ID and port are correct
3. Check that the TwinCAT runtime is running
4. Ensure no firewall is blocking the ADS ports (default: 48898)

### Variable Access

1. Ensure your PLC program is running
2. Check that the variable names are correct (case-sensitive)
3. Verify the data types match between your configuration and the PLC

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Credits

This integration is based on the original ADS integration from Home Assistant Core, adapted for HACS distribution with the name `ads_twincat`