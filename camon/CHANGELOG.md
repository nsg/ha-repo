# Changelog

## 0.6.0

- Fixed snapshot camera images timing out before their sighting frames were
  published.
- Added a 360-second Home Assistant stop timeout so recordings and queued
  uploads can drain cleanly.
- Fixed startup when Supervisor supplies an all-digit MQTT password.
- Made Camon configuration validation strict and improved camera, object-class,
  and storage validation.
- Kept self-updates disabled in the Home Assistant app so updates continue to
  flow through the app store.

See the [Camon releases](https://github.com/nsg/camon/releases) and upstream
[`CHANGELOG.md`](https://github.com/nsg/camon/blob/master/camon-addon/CHANGELOG.md)
for the complete release history.
