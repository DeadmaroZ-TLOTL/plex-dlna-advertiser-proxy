# Plex DLNA Advertiser Proxy

This local Home Assistant add-on advertises a proxy DLNA server on the LAN and
forwards requests to the existing Plex DLNA server.

It fixes the Home Assistant Plex app bridge-network issue where Plex returns
media URLs such as `http://172.30.x.x:32469/...`, which TVs cannot reach. The
proxy rewrites those URLs to the Home Assistant LAN IP and its own proxy port.

After installation, choose `Plex DLNA Proxy (use this)` on the TV, not the
original Plex DLNA server entry.

## Installation

1. Add this repository to Home Assistant:

   ```text
   https://github.com/DeadmaroZ-TLOTL/plex-dlna-advertiser-proxy
   ```

2. Install **Plex DLNA Advertiser Proxy** from the App Store/Add-on Store.
3. Configure the add-on:

   - `plex_url`: Plex DLNA backend URL. Use `http://127.0.0.1:32469` when Plex runs as a Home Assistant add-on on the same host.
   - `advertise_ip`: Home Assistant LAN IP, for example `192.168.0.31`.
   - `listen_port`: proxy port, default `32470`.
   - `friendly_name`: the DLNA server name shown on TVs.

4. Start the add-on and enable **Start on boot**.
5. On the TV, choose **Plex DLNA Proxy (use this)** instead of the original Plex DLNA server entry.

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
