# Changelog

## 0.9.0

- Show each event as a strip of its four frames. An event used to be one
  picture that cycled through its frames; now the frames sit side by side
  on one line, oldest on the left, under the event's time, type and
  duration. Object, movement and continuous events are all the same size,
  and the events page looks the same on a phone and on a desktop.
- An event with fewer than four frames leaves the remaining slots empty.

## 0.8.4

- Soften the edge of the detection mask. A masked area is no longer a block
  of square black cells: its edge breaks up into small boxes, dark grey just
  inside the masked cells and dimming the picture just outside them. Masked
  cells still show nothing of the picture, to the detector or in thumbnails.
- Fix a cropped frame leaving a row or column of pixels visible at the edge
  of a masked cell.

## 0.8.3

- With `detection_boxes` enabled, an object event's filmstrip in the events
  view is now the frames the detector matched on, with the detections
  outlined; they also show the motion boxes when `motion_boxes` is enabled,
  as do the live timeline thumbnail and MQTT snapshots.
- Blur the frame behind the loading label so a still picture is not mistaken
  for live video.

## 0.8.2

- Added an `[analytics.object_detection.framing]` section to choose what the
  detector is shown: the padded motion crop or the full frame, with
  configurable padding, minimum crop size, and aspect ratio.
- Optionally outline motion areas on the model's input, and detections on
  stored thumbnails and MQTT snapshots.
- Map detection boxes through the crop of the frame they were found in.

## 0.8.1

- Added per-camera motion tuner thresholds, observation window, and advanced
  adjustment controls, with 5%/1% starting defaults to validate in Shadow.
- Tune from the camera's minimum object size and manual cell overrides, and
  relax back to that baseline without retaining stale automatic thresholds.
- Account for segment cadence and missing samples, reject long gaps, and align
  learning with the midpoint cell used by motion filtering.
- Show measured cell activity and adaptation status, and keep Shadow proposals
  separate from applied thresholds and saved Auto history.

## 0.8.0

- Added a `tpue` object-detection backend for Coral Edge TPU devices.
- Added a camera order field to sort the camera list.
- Show errors for missing or stalled video, stop serving a dead camera's last
  segments as live, and keep live-edge seeks inside buffered media.
- Bounded the startup archive scan by a single deadline, coalesced snapshot
  decodes, and fetch only the event history a view shows.
- Updated rustls past RUSTSEC-2026-0285.

## 0.7.1

- Reduce mobile live-view work by loading only visible camera tiles and
  processing HLS streams in workers.
- Pause offscreen and background streams, reuse grid players after navigation,
  and limit grid video buffers.
- Keep the loading indicator visible until playback starts and reuse unchanged
  web assets through cache revalidation.

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
