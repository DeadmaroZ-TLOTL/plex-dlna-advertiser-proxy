# Plex DLNA Advertiser Proxy

This local Home Assistant add-on advertises a proxy DLNA server on the LAN and
forwards requests to the existing Plex DLNA server.

It fixes the Home Assistant Plex app bridge-network issue where Plex returns
media URLs such as `http://172.30.x.x:32469/...`, which TVs cannot reach. The
proxy rewrites those URLs to the Home Assistant LAN IP and its own proxy port.

After installation, choose `Plex DLNA Proxy (use this)` on the TV, not the
original Plex DLNA server entry.
