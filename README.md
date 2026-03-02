
# Offline Camping Companion

Camp Companion is a Raspberry Pi Zero 2 W project that creates an offline-first Wi-Fi knowledge server. It broadcasts its own network and hosts a lightweight wiki-style library for outdoor information (PDFs and images), accessible from any phone or laptop browser.

---

## Features (Phase 1)

* Offline Wi-Fi hotspot (NetworkManager-based)
* Switchable development mode (home Wi-Fi) and field mode (offline hotspot)
* Mobile-friendly web interface (DokuWiki)
* Structured namespaces (Camping, Wildlife, Plants, First Aid, etc.)
* PDF and image storage using DokuWiki media system
* Fully local operation with no internet required in field mode

---

## Operating Modes

### Development Mode

* Connected to home Wi-Fi
* Used for installing packages and updating content
* Access via:
  [http://camp-companion.local](http://camp-companion.local)

Switch command:

```
sudo nmcli connection up netplan-wlan0-<your-wifi-name>
```

### Field Mode (Offline)

* Pi broadcasts its own network (e.g., OUTDOOR-LIB)
* Devices connect directly to the Pi
* Access via:
  [http://10.42.0.1](http://10.42.0.1)

Switch command:

```
sudo nmcli connection up outdoor-ap
```

---

## Stack

* NetworkManager (Wi-Fi access point mode with shared IPv4)
* Nginx (web server)
* PHP 8.4 + php-fpm
* DokuWiki (file-based wiki engine)

---

## File Structure

```
/var/www/wiki/
    data/pages/                # Wiki content
    data/media/                # Images and PDFs (DokuWiki-managed)
        library/books/         # PDF storage
```

All media files use lowercase, hyphen-separated naming to avoid case-sensitivity issues.

Example:

```
knots-book.pdf
first-aid-bleeding-control.pdf
```

---

## System Dependencies (Base Setup)

The following base packages are installed before configuring the web stack:

* git — version control and reproducibility
* avahi-daemon — enables `.local` hostname resolution
* curl / wget — downloading packages and resources
* unzip — extracting archives
* htop — system monitoring

---

## Current Status

Phase 1 complete:

* Hotspot configuration via NetworkManager
* Web server stack installed
* DokuWiki deployed
* Namespace structure created
* Media system verified
* Offline PDF serving confirmed

---

