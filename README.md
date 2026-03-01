# offline-camp-companion

A Raspberry Pi Zero 2 W project that creates an offline Wi-Fi hotspot and hosts a lightweight wiki-style library for outdoor knowledge (PDFs + images), accessible from a phone browser.

## Features (V1)
- Offline Wi-Fi hotspot
- Mobile-friendly web UI (wiki)
- Categories (namespaces) like Camping / Wildlife / Plants
- Store and browse PDFs + images
- Runs locally, no internet required

## Stack
- hostapd + dnsmasq (hotspot + DHCP + local DNS)
- Nginx + PHP-FPM
- DokuWiki (file-based wiki)
