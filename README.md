# wifiomarchy

An [Omarchy](https://omarchy.org/) Wi-Fi bar widget — a fork of the built-in
`omarchy.network` that lets you **hide networks you don't want to see while
scanning**.

Living in an apartment, a Wi-Fi scan can list every network belonging to your
neighbours. With this plugin you can mark any unknown network as *hidden*, and
it will never appear in a scan again — while your own connected and saved
networks are always shown.

## Features

- Connect / disconnect / forget networks (everything the stock widget does).
- **Hide** any unknown network from future scans (eye-off button).
- A **HIDDEN** section at the bottom of the panel lists hidden networks, so a
  mistaken hide can be undone with one click (eye button). It's collapsed by
  default — click the header to expand it.
- Hidden networks are persisted in
  `~/.local/state/omarchy/wifi-hidden-networks.json` and survive shell
  restarts and `omarchy update`.

## Requirements

This plugin runs inside Omarchy's shell and uses these built-in Omarchy
commands, which ship with every Omarchy install:

- `omarchy-network-status` — connection details and throughput.
- `omarchy-network-band` — Wi-Fi band selection.

No other dependencies.

## Install

```bash
omarchy plugin add https://github.com/cdelcollado/wifiomarchy --enable
```

If the widget doesn't appear in your bar automatically, place it:

```bash
omarchy plugin enable cdelcollado.network
```

**Note:** `allowMultiple` is `false`, so make sure the built-in
`omarchy.network` is disabled if you have both installed.

## Usage

1. Click the Network icon in the bar.
2. Let it scan (or keep the panel open — it rescans automatically).
3. Hover a network under **OTHER NETWORKS** and click the eye-off button
   (`󰈉`, tooltip "Hide network").
4. To restore a network, open the **HIDDEN** section at the bottom and click
   the eye button (`󰈈`, tooltip "Show again").

## Development

The interesting bits:

- `Model.js` — network helpers (row projection, sorting, section titles).
- `Panel.qml` — the panel UI, the hide/unhide buttons, and JSON persistence.

Validate a local copy before publishing:

```bash
omarchy plugin validate .
```

## License

[MIT](LICENSE). Derived from Omarchy's `omarchy.network` first-party plugin,
also MIT licensed. See [Omarchy](https://omarchy.org/) for upstream licensing.
