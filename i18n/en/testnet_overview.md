# Kovri Testnet

- parses testnet config
  - options for Docker
  - options for monitoring (InfluxDB + Grafana/Qt GUI)
  - options for Kovri
- creates, runs, stops, and destroys testnet environment
- starts and stops individual Kovri testnet instances
- creates/configures RouterInfos for reseed files

## Integration with the Qt GUI

- add testnet option to kovri-util
  - `kovri-util testnet [create | run | stop | destroy | exec | help]`
  - callable from the Qt GUI
- may call out to Python for external component needs
  - use Boost.Python to call component API functions inside Kovri:
    - interact with Docker from within `kovri-util testnet`
    - push/pull stats to/from InfluxDB
    - possibly interact with Grafana (if Qt GUI not enough)
  - this would put a large amount of testnet into Python

## Testnet components with Python client API:

- Docker
- InfluxDB
- Grafana (maybe unnecessary)
- (maybe) Python bottle
  - for easy eepsite setup, reseed/subscription servers, auto-update...
- Kovri
  - use Boost.Python to wrap Kovri classes needed for testnet

If not Python, would need to write HTTP API client code.

## Testnet components with HTTP client API

- Docker has well-defined HTTP API (over unix + tcp socket)
  - would need to start daemon with tcp socket for Windows
- InfluxDB has well-defined HTTP API
- Grafana has well-defined HTTP API

## Kovri classes needed for kovri-util testnet

Most functionality already implemented in `kovri-util`, just need to reuse for the testnet component

### I2PControl

- start/stop individual instances
- retrieve individual instance stats
  - uses I2PControlClient to call each instance's I2PControl server
- create reseed file from instance RouterInfos
  - useful for testnet floodfill instances to bootstrap their NetDb
- parse stats from all instances
- send stats to Grafana/Qt GUI for display
- read instance log files
- send logs to Grafana/Qt GUI

### core::RouterInfo

- set keys (for signing/verifying RI, encrypting transport sessions)
- set host
- set port
- disable/enable NTCP & SSU (default enabled)
  - must have at least one
- set capabilities
  - enable/disable floodfill (default disabled)
  - bandwidth
  - reachable/unreachable
  - hidden
  - ssu introducer
  - ssu testing
- set RI options

### core::Instance

- setup RouterInfo
- setup NetDb
- setup reseed (should be client)
- setup transports
- setup server tunnels
- setup logging
 
### client::Instance

- setup http proxy
- setup socks proxy
- setup client tunnels
- setup reseed (currently setup in core)
- setup address book
- setup logging (if separate from core log)

### others...
