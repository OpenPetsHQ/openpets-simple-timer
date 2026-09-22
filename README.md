# Simple Timer

An OpenPets SDK v3 plugin for one-shot countdowns with preset or custom
durations, an optional label, a pinned pet HUD, pause/resume, cancel, +5
minutes, and an expiry alert with snooze or dismiss.

The alert can optionally play a sound and request an OS notification. The
plugin stores absolute timestamps and reconciles them on startup, so sleep and
restart do not turn a countdown into a duplicate or stale callback. If both
alert presentation paths fail, the expiry remains pending for a later lifecycle
recovery instead of being marked delivered.

Plugin id: `openpets.simple-timer`.

## Files

```text
openpets.plugin.json  # SDK v3 manifest, permissions, and settings
index.js              # Timer lifecycle, host-rendered HUD, scheduling, storage
locales/en.json       # English strings
test.js               # Deterministic SDK harness checks
```

No bundled assets are required; the plugin uses the host's timer icon and
host-rendered UI.

## Permissions

- `pet:speak`, `pet:interact`, `pet:pin`: HUD and fallback speech.
- `audio`, `notify`: optional expiry sound and OS notification.
- `schedule`, `storage`: absolute expiry/HUD scheduling and durable recovery.
- `commands`, `status`: pet menu commands and Plugins-window status.

The plugin package is kept in this repository so OpenPets can consume a tagged,
standalone release without copying its source into the desktop host.

## Development

Install dependencies once:

```bash
npm install
```

Run the deterministic SDK harness:

```bash
npm test
```

Validate the plugin package with the OpenPets CLI:

```bash
npx -y @open-pets/cli plugin validate .
```

To test the plugin in OpenPets, use **Tray → Plugins → Developer Mode → Load
Folder** and select this repository. Refresh the folder after editing.

## OpenPets integration

The standalone repository is the canonical source for the plugin. OpenPets
should consume a tagged release or pinned commit through its plugin catalog and
package validation flow; the host repository should retain only catalog or
integration metadata, not a second hand-maintained copy of these files.

## License

[MIT](LICENSE)
