# Plex DLNA Advertiser Proxy

Home Assistant add-on repository for `Plex DLNA Advertiser Proxy`.

The add-on advertises a DLNA proxy for Plex and rewrites Docker-internal Plex DLNA URLs, such as `http://172.30.x.x:32469/...`, to a LAN-reachable Home Assistant URL.

## Add-on

- `plex_dlna_proxy` - advertises `Plex DLNA Proxy (use this)` on the LAN and proxies Plex DLNA traffic through `listen_port` on the Home Assistant host.

## Default Settings

- Plex DLNA backend: `http://127.0.0.1:32469`
- Advertised IP: `192.168.0.31`
- Proxy port: `32470`

After installing, choose `Plex DLNA Proxy (use this)` on the TV.
