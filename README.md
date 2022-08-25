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

#### Configuration

##### Options

```yaml
ssl: true
certfile: fullchain.pem
keyfile: privkey.pem
```

##### Network

| Container | Host     | Description                              |
| --------- | -------- | ---------------------------------------- |
| 53/udp    | 53       | DNS server port                          |
| 80/tcp    | Disabled | Web interface (Not required for Ingress) |

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

### File editor

Simple browser-based file editor for Home Assistant. Visit the [File editor](https://github.com/home-assistant/hassio-addons/tree/master/configurator) page for more details.

#### Configuration

##### Options

```yaml
dirsfirst: false
enforce_basepath: true
git: true
ignore_pattern:
  - __pycache__
  - .cloud
  - .storage
  - deps
ssh_keys: []
```

### Git Pull

Simple git pull to update the local configuration. Visit the [Git pull](https://github.com/home-assistant/hassio-addons/tree/master/git_pull) page for more details.

#### Configuration

##### Options

```yaml
deployment_key:
  - "-----BEGIN OPENSSH PRIVATE KEY-----"
  - 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
  - "-----END OPENSSH PRIVATE KEY-----"
deployment_key_protocol: rsa
deployment_user: ""
deployment_password: ""
git_branch: master
git_command: pull
git_remote: origin
git_prune: false
repository: "git@github.com:greenthegarden/home-assistant-configuration-lovelace.git"
auto_restart: false
restart_ignore:
  - ui-lovelace.yaml
  - .gitignore
repeat:
  active: false
  interval: 300
```

### Samba

Expose Home Assistant folders with SMB/CIFS. Visit the [Samba share](https://github.com/home-assistant/hassio-addons/tree/master/samba) page for more details.

#### Configuration

```yaml
workgroup: WORKGROUP
username: homeassistant
password: h0me@ssistant
interface: ""
allow_hosts:
  - 10.0.0.0/8
  - 172.16.0.0/12
  - 192.168.0.0/16
  - "fe80::/10"
veto_files:
  - ._*
  - .DS_Store
  - Thumbs.db
  - icon?
  - .Trashes
compatibility_mode: false
```

### Network UPS Tools

Manage battery backup (UPS) devices. Visit the [Network UPS Tools](https://github.com/hassio-addons/addon-nut) page for more details.

#### Configuration

##### Options

```yaml
users:
  - username: nut
    password: hassionutserver
    instcmds:
      - all
    actions: []
devices:
  - name: myups
    driver: usbhid-ups
    port: auto
    config:
      - vendorid = 051d*
mode: netserver
shutdown_host: "false"
list_usb_devices: true
log_level: debug
```

##### Network

| Container | Host     | Description       |
| --------- | -------- | ----------------- |
| 3493/tcp  | Disabled | Network UPS Tools |

### SSH & Web Terminal

SSH & Web Terminal access to your Home Assistant instance. Visit the [SSH & Web Terminal](https://github.com/hassio-addons/addon-ssh) page for more details.

#### Configuration

##### Options

```yaml
ssh:
  username: homeassistant
  password: ""
  authorized_keys:
    - >-
      ssh-ed25519
      AAAAC3NzaC1lZDI1NTE5AAAAIJeXQHCpJD193ss7gKJgi1YX0PLMzPXVPNqEsKvjwx5W
      philip@DESKTOP-L53R83M
  sftp: false
  compatibility_mode: false
  allow_agent_forwarding: false
  allow_remote_port_forwarding: false
  allow_tcp_forwarding: false
zsh: true
share_sessions: false
packages:
  - build-base
init_commands:
  - ls -al
log_level: info
```

##### Network

| Container | Host | Description |
| --------- | ---- | ----------- |
| 22/tcp    | 22   |             |

##### Audio

Input: Default

Output: Default

### Terminal & SSH

Allow logging in remotely to Home Assistant using SSH. Visit the Terminal & SSH page for more details.

#### Configuration

##### Options

```yaml
authorized_keys:
  - >-
    ssh-ed25519
    AAAAC3NzaC1lZDI1NTE5AAAAIJeXQHCpJD193ss7gKJgi1YX0PLMzPXVPNqEsKvjwx5W
    philip@DESKTOP-L53R83M
apks: []
password: ""
server:
  tcp_forwarding: false
```

##### Network

| Container | Host | Description |
| --------- | ---- | ----------- |
| 22/tcp    | 22   |             |

##### Audio

Input: Default

Output: Default

## Integration Configuration

### AdGuard Home

https://www.home-assistant.io/integrations/adguard

Configuration via Add-on

### Ambee

https://www.home-assistant.io/integrations/ambee/

API from https://api-dashboard.getambee.com/

Configuration via UI

API: 509406d79389e7ce6b40fee65ec9b3f7dbf50a438ca818e0ed5039e1a2c9a0ba
Name: Home
Latitude: !secret home_longitude
Longitude: !secret home_longitude

### Brother Printer

https://www.home-assistant.io/integrations/brother

Configuration via UI

Host: BRWA8A79536739F.localdomain
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

Configuration via YAML

```yaml
mqtt:
  client_id: !secret mqtt_client_id
  broker: !secret mqtt_broker
  port: 1883
  # username: !secret mqtt_username
  # password: !secret mqtt_password
  discovery: true
  discovery_prefix: homeassistant
  birth_message:
    topic: "hass/status"
    payload: "online"
  will_message:
    topic: "hass/status"
    payload: "offline"
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

#### On Hass.io

Connect to the NUT server:

- Host: a0d7b954-nut
- Port: 3493
- Username: !secret nut_server_username
- Password: !secret nut_server_password

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

### Raspberry Pi Power Supply Checker

https://www.home-assistant.io/integrations/rpi_power

### Speedtest.net

https://www.home-assistant.io/integrations/speedtestdotnet

Configuration via YAML

```yaml
speedtestdotnet:
  scan_interval:
    minutes: 30
  monitored_conditions:
    - ping
    - download
    - upload
```

Configuration via UI

Options:

- Select test server: \*Auto Detect
- Update frequency (minutes): 30
- Disable auto update: false

### Synology DSM

https://www.home-assistant.io/integrations/synology_dsm

Configuration via YAML

```yaml
synology_dsm:
  - host: !secret synology_host
    port: 5001
    username: !secret synology_dsm_username
    password: !secret synology_dsm_password
```

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
