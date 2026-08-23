# Changelog

## 0.6.1

- Fixed the live view stalling for several seconds when opening a camera by
  following hls.js's buffered live position instead of seeking past it.
- Kept the loading overlay visible until the first video frame plays.
- Reduced live latency by rounding the HLS playlist target duration to the
  nearest second instead of always rounding it up.

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

See the [Camon releases](https://github.com/nsg/camon/releases) for the complete
release history.
