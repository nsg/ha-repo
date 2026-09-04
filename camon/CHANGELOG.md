# Changelog

## 0.7.0

- Added per-cell minimum object sizes and an optional per-camera motion tuner
  with shadow and automatic modes.
- Added a live-view tuning heatmap and controls for inspecting, resetting, and
  manually painting cell thresholds.
- Auto-cycle event-card filmstrips while they are visible and request
  viewport-sized live-view posters for faster loading on mobile devices.

## 0.6.4

- Redesigned event lists as image-first cards, collapsing chunked runs and
  allowing filmstrips to be scrubbed in place.
- Showed the latest camera keyframe while the live stream loads.

## 0.6.3

- Restyled the live timeline as a thin scrubber with motion and detection ticks,
  and replaced per-day history maps with an inline list of recent events.
- Updated the HTTP/2 stack to address the denial-of-service vulnerability
  RUSTSEC-2026-0258.

## 0.6.2

- Added an optional per-camera `sub_url` for a low-resolution H.264 stream used
  by the multi-camera grid, reducing load time and bandwidth on constrained
  links while keeping recording, analytics, and single-camera views on the main
  stream.

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
