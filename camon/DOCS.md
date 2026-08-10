# Camon for Home Assistant

Camon is a multi-camera NVR with motion and object analytics, tiered recording
storage, a browser interface, and Home Assistant MQTT discovery. The app embeds
the Camon interface in the Home Assistant sidebar through ingress.

The app is available for `amd64` systems only. Its source code, image build,
release artifacts, and issue tracker are maintained in the
[Camon project](https://github.com/nsg/camon). Home Assistant pulls the
prebuilt `ghcr.io/nsg/amd64-addon-camon` image; it does not compile Camon on
your Home Assistant machine.

## Install

1. Install Camon from the NSG Home Assistant repository.
2. Create `/addon_configs/<repo>_camon/camon.toml` as described below.
3. Start Camon, then select **Camon** in the sidebar.
4. Optional: enable **Watchdog** on the app page so Home Assistant restarts
   Camon if a required recorder task fails.

## Configuration

Camon has no options form in Home Assistant. Configure it with the same
`camon.toml` format used by native installations. Start with the project's
[commented example configuration](https://github.com/nsg/camon/blob/master/config.toml.example).

Create the configuration file at:

```text
/addon_configs/<repo>_camon/camon.toml
```

Use File editor, Studio Code Server, SSH, Samba, or another app that can edit
add-on configuration directories. On first start, Camon places a commented
`camon.toml.example` beside the expected file. Copy or rename it to
`camon.toml`, add at least one `[[cameras]]` entry, and restart Camon.

Camon forces the container-specific settings below at startup:

- `update.enabled = false`: updates are installed through Home Assistant.
- `http.port = 22666`: this is the ingress port.
- `http.bind = 0.0.0.0`: ingress reaches Camon over the container network.
- `http.allow_open = true`: Home Assistant ingress handles authentication.
- `storage.data_dir = /data/storage`: recordings use the persistent app data
  volume.

All other settings use the upstream `camon.toml` configuration unchanged.

## MQTT discovery

Camon can publish camera, motion, occupancy, and snapshot entities through
Home Assistant MQTT discovery. Install the Mosquitto broker app and configure
the MQTT integration, then restart Camon. Camon requests optional access to
the Supervisor MQTT service and uses its connection details automatically when
available. An external broker can instead be configured in `camon.toml`.

## Updates and support

The app version matches the tag of its prebuilt GHCR image. Camon's source
repository builds and publishes that image; this Home Assistant repository
only publishes the catalog entry that points to it.

- [Camon documentation](https://github.com/nsg/camon#readme)
- [Example configuration](https://github.com/nsg/camon/blob/master/config.toml.example)
- [Issues](https://github.com/nsg/camon/issues)
- [Releases](https://github.com/nsg/camon/releases)
