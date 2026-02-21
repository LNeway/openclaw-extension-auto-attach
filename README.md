# OpenClaw Chrome Extension (Browser Relay)

Purpose: attach OpenClaw to an existing Chrome tab so the Gateway can automate it (via the local CDP relay server).

## Features

- **Manual Attach/Detach**: Click the extension icon to attach/detach the current tab
- **Auto-Attach**: Automatically attach to configured domains when pages load
- **Wildcard Support**: Match multiple subdomains with wildcard patterns (e.g., `*.example.com`)

## Dev / load unpacked

1. Build/run OpenClaw Gateway with browser control enabled.
2. Ensure the relay server is reachable at `http://127.0.0.1:18792/` (default).
3. Install the extension to a stable path:

   ```bash
   openclaw browser extension install
   openclaw browser extension path
   ```

4. Chrome → `chrome://extensions` → enable "Developer mode".
5. "Load unpacked" → select the path printed above.
6. Pin the extension. Click the icon on a tab to attach/detach.

## Options

Right-click the extension icon → "Options" to configure:

- **Relay port**: defaults to `18792`. Change if your OpenClaw profile uses a different `cdpUrl` port.
- **Auto-attach domains**: comma-separated list of domains to automatically attach.
  - Default: `xiaohongshu.com, *.xiaohongshu.com`
  - Supports exact match: `example.com`
  - Supports wildcards: `*.example.com` (matches all subdomains)
  - Example: `xiaohongshu.com, *.example.com, github.com`

## Auto-Attach Behavior

When auto-attach is enabled for a domain:

1. **Page Load**: Automatically attaches when a matching page finishes loading
2. **Page Reload**: Detaches old connection and re-attaches after reload completes
3. **Tab Switch**: Automatically attaches when switching to a matching tab that's already loaded

The extension badge shows the connection status:
- `ON` (red): Connected and attached
- `…` (yellow): Connecting
- `!` (red): Error (relay server not reachable)
- Empty: Not connected

## Troubleshooting

- **Red `!` badge**: The relay server is not reachable. Start OpenClaw's browser relay, then click the icon again.
- **Auto-attach not working**: Check the Service Worker console (`chrome://extensions` → "Service Worker" → "inspect") for `[auto-attach]` logs.
- **Page reload issues**: The extension automatically detaches and re-attaches on page reload.

## Dev / load unpacked

1. Build/run OpenClaw Gateway with browser control enabled.
2. Ensure the relay server is reachable at `http://127.0.0.1:18792/` (default).
3. Install the extension to a stable path:

   ```bash
   openclaw browser extension install
   openclaw browser extension path
   ```

4. Chrome → `chrome://extensions` → enable “Developer mode”.
5. “Load unpacked” → select the path printed above.
6. Pin the extension. Click the icon on a tab to attach/detach.

## Options

- `Relay port`: defaults to `18792`.
