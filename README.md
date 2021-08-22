<p align="center">
  <img src="https://user-images.githubusercontent.com/64605172/130371389-182b7c08-d6ad-4069-8e03-18cb472e6ce0.png">
</p>

A simple bash script to notify major earthquakes from [USGS](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/significant_hour.geojson). <sub><sup>[[What counts as a significant earthquake?]](https://earthquake.usgs.gov/earthquakes/browse/significant.php#sigdef)</sup></sub>

## Dependecies

* [libnotify](https://github.com/GNOME/libnotify) ([check if your DE already has libnotify built-in](https://wiki.archlinux.org/title/Desktop_notifications#Libnotify))
* [jq](https://stedolan.github.io/jq/download/)

## Installation

Download bash script and make executable
```bash
curl 'https://raw.githubusercontent.com/Raais/ewalert/main/ewalert' -o $HOME/.local/bin/ewalert
```

```bash
sudo chmod +x $HOME/.local/bin/ewalert
```
### Configuration
Uncomment the [`session="x-session"`](https://github.com/Raais/ewalert/blob/c673c5215be55c04eb7ab67cf470daa2455660db/ewalert#L5) line according to your desktop environment. This is needed for exporting the DBUS_SESSION_BUS_ADDRESS variable.

#### Example (Ubuntu/GNOME)
```bash
### nano $HOME/.local/bin/ewalert ###
session="gnome-session"
```

### Make script run every x minutes

#### Example (cron)
```bash
crontab -e
```
```bash
#run every 10 minutes
*/10 * * * * $HOME/.local/bin/ewalert
```
[USGS Real-time GeoJSON Feeds](https://earthquake.usgs.gov/earthquakes/feed/v1.0/geojson.php) are updated every minute, so you can choose any interval higher than that. The script will not repeat alerts.

You may face issues depending on your setup, eg., if you have notifications disabled, or if you have turned on Do Not Disturb mode.
