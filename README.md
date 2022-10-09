# Home Assistant Configuration

Configuration for [Home Assistant](http://homeassistant.io)

## Install HACS

See https://hacs.xyz/docs/installation/installation

Using the directions for Home Assistant Container, Option 1: Run the installer on the host OS,

```sh
cd home-assistant-configuration-lovelace
wget -q -O - https://install.hacs.xyz | bash -
```

## Integrations

![Home Assistant Integrations](./docs/homeassistant-integrations.png "Home Assistant Integrations")

## Areas

![Home Assistant Areas](./docs/homeassistant-areas.png "Home Assistant Areas")

## Fix bom-radar-card.js

Find and replace the following in bom-radar-card.js

/local/community with /local/custom_ui
/hacsfiles with /local/custom_ui

## Inspirations

https://github.com/bacco007/HomeAssistantConfig
https://github.com/arsaboo/homeassistant-config/tree/master/blueprints/automation/homeassistant

## Hassio nfs share

mount -o bind 192.168.1.161:/volume1/cameras /media/camera/storology

## Add-on Configurations

### AdGuard Home

Network-wide ads & trackers blocking DNS server. Visit the [AdGuard Home](https://github.com/hassio-addons/addon-adguard-home) page for more details.

### AppDaemon 4

Python Apps and Dashboard using AppDaemon 4.x for Home Assistant. Visit the [AppDaemon 4](https://github.com/hassio-addons/addon-appdaemon) page for more details.

#### Configuration

##### Options

```yaml
system_packages: []
python_packages: []
init_commands: []
```

##### Network

| Container | Host | Description |
| --------- | ---- | ----------- |
| 5050/tcp  | 5050 | AppDaemon   |

## Integration Configuration

### Brother Printer

https://www.home-assistant.io/integrations/brother

Configuration via UI

Host: printer.localdomain
Type: Laser

### Bureau of Meteorology

https://github.com/bremor/bureau_of_meteorology

Configuration via UI

Customise Observation Sensors

- Basename for all of your observation sensors: Adelaide (West Terrace / ngayirdapira)
- Which sensors would you like to create?: Temperature, Temperature Feels Like, Rain Since 9am, Humidity, Wind Speed Kilometre, Wind Speed Knot, Wind Direction, Gust Speed Kilometre, Gust Speed Knot

Customise Forecast Sensors:

- Create forecast sensors: true

Customise Forecast Sensors:

- Choose a 'basename' for your forecast sensors (e.g. sensor.basename_temp_max_0): Marden
- Which sensors would you like to create?: Max. Temperature, Min. Temperature, Extended Text, Icon Descriptor, MDI Icon, Short Text, UV Category, UV Max Index, UV Protection Start Time, UV Protection End Time, Rain Amount Min., Rain Amount Max., Rain Amount Range, Rain Chance, Fire Danger
- How many forecast days would you like? (0-7): 7

### Forecast.Solar

https://www.home-assistant.io/integrations/forecast_solar

Configuration vi UI

Name: Home
Latitude: !secret home_latitude
Longitude: !secret home_longitude
Declination: !secret home_roof_decination
Azimuth: !secret home_roof_azimuth
Total Watt peak power of your solar modules: 1000

Options:
Forecast.Solar API Key:
Damping factor:

### Google Cast

https://www.home-assistant.io/integrations/cast

### IKEA TRÅDFRI

https://www.home-assistant.io/integrations/tradfri

Configuration via YAML

```yaml
tradfri:
  host: !secret ikea_tradfri_host
```

Configuration vi UI

Security code: !secret ikea_tradfri_security_key

### Mobile App

### MQTT

https://www.home-assistant.io/integrations/mqtt

Configuration via UI

```yaml
mqtt:
  client_id: !secret mqtt_client_id
  broker: !secret mqtt_broker
  port: 1883
```

### Nest

https://www.home-assistant.io/integrations/nest

Configuration via YAML

```yaml
nest:
  client_id: !secret nest_client_id
  client_secret: !secret nest_client_secret
  # "Project ID" in the Device Access Console
  project_id: !secret nest_project_id
  # Provide the full path exactly as shown under "Subscription name" in Google Cloud Console
  subscriber_id: !secret nest_subscriber_id
```

### Network UPS Tools (NUT)

https://www.home-assistant.io/integrations/nut

Configuration via UI

#### On Docker

Connect to the NUT server:

- Host: localhost
- Port: 3493
- Username: monitor
- Password: homeassistant

Choose the Resources to Monitor:

- Resources: Status Data, Load, UPS Shutdown Delay, Load Reboot Timer, Load Shutdown Timer, Beeper Status, Battery Charge, Low Battery Setpoint, Warning Battery Setpoint, Battery Voltage, Nominal Battery Voltage, Battery Runtime, Low Battery Runtime, Battery Date, Battery Manuf. Date, Battery Chemistry, Input Power Sensitivity, Low Voltage Transfer, High Voltage Transfer, Input Voltage, Nominal Input Voltage, Status

Options:

- Resources: Status Data, Load, UPS Shutdown Delay, Load Reboot Timer, Load Shutdown Timer, Beeper Status, Battery Charge, Low Battery Setpoint, Warning Battery Setpoint, Battery Voltage, Nominal Battery Voltage, Battery Runtime, Low Battery Runtime, Battery Date, Battery Manuf. Date, Battery Chemistry, Input Power Sensitivity, Low Voltage Transfer, High Voltage Transfer, Input Voltage, Nominal Input Voltage, Status
- Scan Interval (seconds): 60

### OpenUV

https://www.home-assistant.io/integrations/openuv

Configuration in YAML

```yaml
openuv:
  api_key: !secret openuv_api_key
```

Configuration via UI

- API Key: !secret openuv_api_key
- Latitude: !secret home_longitude
- Longitude: !secret home_latitude
- Elevation: !secret home_elevation

### Speedtest.net

https://www.home-assistant.io/integrations/speedtestdotnet

Configuration via UI

Options:

- Select test server: \*Auto Detect
- Update frequency (minutes): 30
- Disable auto update: false

### Synology DSM

https://www.home-assistant.io/integrations/synology_dsm

Configuration via UI

- Host: storology.localdomain
- Username: !secret synology_dsm_username
- Password: !secret synology_dsm_password
- Port: 5001
- Uses an SSL certificate: true
- Verify SSL certificate: false

Options:

- Minutes between scans: 15
- Timeout (seconds): 10

### Ubiquiti UniFi

https://www.home-assistant.io/integrations/unifi

Configuration via UI:

Set up UniFi Controller

Host: !secret ubiquity_unity_controller_host
Username: !secret ubiquity_unity_controller_username
Password: !secret ubiquity_unity_controller_password  
Port: 443
Verify SSL certificate: false

Options:

Configure device tracking

- Track network clients: true
- Include wired network clients: true
- Track network devices (Ubiquiti devices): true
- Select SSIDs to track wireless clients on: videoAtHome-2.4g
- Time in seconds from last seen until considered away: 300
- Disable UniFi wired bug logic: false

Configure client controls

Create switches for serial numbers you want to control network access for.

- Network access controlled clients:
- Allow POE control of clients: false
- Allow control of DPI restriction groups: true

Configure statistics sensors

- Bandwidth usage sensors for network clients: true
- Uptime sensors for network clients: true

COnfiguring sensors see https://www.reddit.com/r/homeassistant/comments/buog5r/get_temperatures_from_within_docker/
