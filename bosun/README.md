# Bosun

Bosun is an API-key gateway for a Frigate NVR. It authenticates callers and
applies a default-deny allowlist to the HTTP methods and paths each key may
access, then streams permitted requests and responses between the caller and
Frigate.

Configure the Frigate URL, connection timeout, log level, API keys, and access
rules from Home Assistant's native configuration form. See the
**Documentation** tab after installation or the
[Bosun project](https://github.com/nsg/bosun) for more information. The Home
Assistant app is available for `amd64` systems only.
