# Plex DLNA Advertiser Proxy

Home Assistant add-on repository for `Plex DLNA Advertiser Proxy`.

The add-on advertises a DLNA proxy for Plex and rewrites Docker-internal Plex DLNA URLs, such as `http://172.30.x.x:32469/...`, to a LAN-reachable Home Assistant URL.

## Add-on

- `plex_dlna_proxy` - advertises `Plex DLNA Proxy (use this)` on the LAN and proxies Plex DLNA traffic through `listen_port` on the Home Assistant host.

## Installation

1. In Home Assistant, open **Settings** -> **Apps** -> **App Store**.
   On older Home Assistant versions, open **Settings** -> **Add-ons** -> **Add-on Store**.
2. Open the three-dot menu and choose **Repositories**.
3. Add this repository URL:

   ```text
   https://github.com/DeadmaroZ-TLOTL/plex-dlna-advertiser-proxy
   ```

4. Search for **Plex DLNA Advertiser Proxy**.
5. Install the add-on.
6. Open the add-on **Configuration** tab and set:

   - `plex_url`: Plex DLNA backend URL. Use `http://127.0.0.1:32469` when Plex runs as a Home Assistant add-on on the same host.
   - `advertise_ip`: Home Assistant LAN IP, for example `192.168.0.31`.
   - `listen_port`: proxy port, default `32470`.
   - `friendly_name`: the DLNA server name shown on TVs.

7. Start the add-on and enable **Start on boot**.
8. On the TV, choose **Plex DLNA Proxy (use this)** instead of the original Plex DLNA server entry.

## Requirements

- Plex DLNA must be enabled.
- The TV and Home Assistant must be on the same LAN/VLAN where UDP SSDP multicast can pass.
- Port `listen_port` must be reachable from the TV.

## Verify

Open these URLs from another device on the LAN:

```text
http://192.168.0.31:32470/health
http://192.168.0.31:32470/DeviceDescription.xml
```

Replace `192.168.0.31` with your Home Assistant LAN IP. The health endpoint should return `ok`.

## Migrating From The Old Custom Integration

If you used the old `plex_dlna_advertiser` custom integration, disable it before using this add-on:

1. Remove or comment the `plex_dlna_advertiser:` block in `configuration.yaml`.
2. Remove, rename, or disable `custom_components/plex_dlna_advertiser`.
3. Restart Home Assistant.

## Default Settings

- Plex DLNA backend: `http://127.0.0.1:32469`
- Advertised IP: `192.168.0.31`
- Proxy port: `32470`

After installing, choose `Plex DLNA Proxy (use this)` on the TV.
