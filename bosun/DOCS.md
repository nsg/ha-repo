# Bosun

Bosun is an API gateway that sits in front of a [Frigate](https://frigate.video)
NVR. It authenticates callers by API key and enforces a **default-deny
allowlist** over which HTTP method and path each key may reach, then
reverse-proxies permitted requests to Frigate.

The app is available for `amd64` systems only. Its source code, image build,
release artifacts, icon, and issue tracker remain in the
[Bosun project](https://github.com/nsg/bosun). Home Assistant pulls the
prebuilt `ghcr.io/nsg/bosun-amd64` image; it does not compile Bosun on your
Home Assistant machine.

## Installation

1. Install Bosun from the NSG Home Assistant repository.
2. Configure `frigate_url` and `api_keys` in the app's **Configuration** tab.
3. Start Bosun.

Updates are delivered through Home Assistant. When a new version is published,
the app shows an **Update** button.

## Configuration

Everything is configured from the app's **Configuration** tab; there are no
configuration files to edit.

- **Frigate URL** — Frigate's base URL. If Frigate runs as its own app, this is
  typically `http://<frigate-slug>:5000` or
  `http://homeassistant.local:5000`.
- **Upstream connect timeout** — 1–60 seconds to establish a connection to
  Frigate. It bounds connection setup only and does not cut off snapshots or
  video streams.
- **Log level** — `trace`, `debug`, `info`, `warn`, or `error`.
- **API keys** — one entry per caller. Each key has a name, a secret sent in
  the `X-API-Key` header, and a list of access rules.

### Rules

A request is allowed only when one of the key's rules matches both its HTTP
method and request path. An unknown key receives `401`; a known key without a
matching rule receives `403`.

- `methods` contains allowed HTTP verbs. `*` matches any verb.
- `paths` contains glob patterns. `*` matches characters within one path
  segment, while `**` matches any number of segments.

## Networking

Bosun listens on port `8080` inside the container. Change its host mapping in
the app's **Network** section when needed. The `/healthz` endpoint does not
require a key.

Make an authenticated request:

```bash
curl -H "X-API-Key: a-long-random-secret" \
  http://<home-assistant>:8080/api/events
```

## Support

- [Bosun documentation](https://github.com/nsg/bosun#readme)
- [Example configuration](https://github.com/nsg/bosun/blob/master/bosun.example.json)
- [Issues](https://github.com/nsg/bosun/issues)
