# Simple Timer

An OpenPets SDK v3 plugin for one-shot countdowns with a pet HUD, pause and
resume controls, and an expiry alert.

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
