---
title: MQTT Integration
sidebar_label: MQTT
---

The MQTT function within TeslaMate allows useful values to be published to an MQTT broker. This is useful in allowing other automation platforms to consume data from TeslaMate.

## MQTT Topics

Vehicle data will be published to the following topics:

| Topic                                                  | Example                                                                                     | Description                                                                           |
| ------------------------------------------------------ | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `teslamate/cars/$car_id/display_name`                  | Blue Thunder                                                                                | Vehicle Name                                                                          |
| `teslamate/cars/$car_id/state`                         | asleep                                                                                      | Status of the vehicle (e.g. `online`, `asleep`, `charging`)                           |
| `teslamate/cars/$car_id/since`                         | 2019-02-29T23:00:07Z                                                                        | Date of the last status change                                                        |
| `teslamate/cars/$car_id/healthy`                       | true                                                                                        | Health status of the logger for that vehicle                                          |
| `teslamate/cars/$car_id/version`                       | 2019.32.12.2                                                                                | Software Version                                                                      |
| `teslamate/cars/$car_id/update_available`              | false                                                                                       | Indicates if a software update is available                                           |
| `teslamate/cars/$car_id/update_version`                | 2019.32.12.3                                                                                | Software version of the available update                                              |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/model`                         | 3                                                                                           | Either "S", "3", "X" or "Y"                                                           |
| `teslamate/cars/$car_id/trim_badging`                  | P100D                                                                                       | Trim badging                                                                          |
| `teslamate/cars/$car_id/exterior_color`                | DeepBlue                                                                                    | The exterior color                                                                    |
| `teslamate/cars/$car_id/wheel_type`                    | Pinwheel18                                                                                  | The wheel type                                                                        |
| `teslamate/cars/$car_id/spoiler_type`                  | None                                                                                        | The spoiler type                                                                      |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/geofence`                      | 🏡 Home                                                                                     | The name of the Geo-fence, if one exists at the current position                      |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/latitude`                      | 35.278131                                                                                   | DEPRECATED: Last reported car latitude                                                |
| `teslamate/cars/$car_id/longitude`                     | 29.744801                                                                                   | DEPRECATED: Last reported car longitude                                               |
| `teslamate/cars/$car_id/location`                      | <pre lang="json">\{<br /> "latitude": 35.278131,<br /> "longitude": 29.744801<br />\}</pre> | Last reported car location (json blob)                                                |
| `teslamate/cars/$car_id/shift_state`                   | D                                                                                           | Current/Last Shift State (D/N/R/P)                                                    |
| `teslamate/cars/$car_id/power`                         | -9                                                                                          | Current battery power in watts. Positive value on discharge, negative value on charge |
| `teslamate/cars/$car_id/speed`                         | 12                                                                                          | Current Speed in km/h                                                                 |
| `teslamate/cars/$car_id/heading`                       | 340                                                                                         | Last reported car direction                                                           |
| `teslamate/cars/$car_id/elevation`                     | 70                                                                                          | Current elevation above sea level in meters                                           |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/locked`                        | true                                                                                        | Indicates if the car is locked                                                        |
| `teslamate/cars/$car_id/sentry_mode`                   | false                                                                                       | Indicates if Sentry Mode is active                                                    |
| `teslamate/cars/$car_id/windows_open`                  | false                                                                                       | Indicates if any of the windows are open                                              |
| `teslamate/cars/$car_id/doors_open`                    | false                                                                                       | Indicates if any of the doors are open                                                |
| `teslamate/cars/$car_id/driver_front_door_open`        | false                                                                                       | Indicates if the driver-side front door is open                                       |
| `teslamate/cars/$car_id/driver_rear_door_open`         | false                                                                                       | Indicates if the driver-side rear door is open                                        |
| `teslamate/cars/$car_id/passenger_front_door_open`     | false                                                                                       | Indicates if the passenger-side front door is open                                    |
| `teslamate/cars/$car_id/passenger_rear_door_open`      | false                                                                                       | Indicates if the passenger-side rear door is open                                     |
| `teslamate/cars/$car_id/trunk_open`                    | false                                                                                       | Indicates if the trunk is open                                                        |
| `teslamate/cars/$car_id/frunk_open`                    | false                                                                                       | Indicates if the frunk is open                                                        |
| `teslamate/cars/$car_id/is_user_present`               | false                                                                                       | Indicates if a user is present in the vehicle                                         |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/is_climate_on`                 | true                                                                                        | Indicates if the climate control is on                                                |
| `teslamate/cars/$car_id/inside_temp`                   | 20.8                                                                                        | Inside Temperature in °C                                                              |
| `teslamate/cars/$car_id/outside_temp`                  | 18.4                                                                                        | Temperature in °C                                                                     |
| `teslamate/cars/$car_id/is_preconditioning`            | false                                                                                       | Indicates if the vehicle is being preconditioned                                      |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/odometer`                      | 1653                                                                                        | Car odometer in km                                                                    |
| `teslamate/cars/$car_id/est_battery_range_km`          | 372.5                                                                                       | Estimated Range in km                                                                 |
| `teslamate/cars/$car_id/rated_battery_range_km`        | 401.63                                                                                      | Rated Range in km                                                                     |
| `teslamate/cars/$car_id/ideal_battery_range_km`        | 335.79                                                                                      | Ideal Range in km                                                                     |
|                                                        |                                                                                             |                                                                                       |
| `teslamate/cars/$car_id/battery_level`                 | 88                                                                                          | Battery Level Percentage                                                              |
| `teslamate/cars/$car_id/usable_battery_level`          | 85                                                                                          | Usable battery level percentage                                                       |
| `teslamate/cars/$car_id/plugged_in`                    | true                                                                                        | If car is currently plugged into a charger                                            |
| `teslamate/cars/$car_id/charging_state`                | Charging                                                                                    | The cars charging state (Charging, Disconnected, Stopped, NoPower, Complete)          |
| `teslamate/cars/$car_id/charge_energy_added`           | 5.06                                                                                        | Last added energy in kWh                                                              |
| `teslamate/cars/$car_id/charge_limit_soc`              | 90                                                                                          | Charge Limit Configured in Percentage                                                 |
| `teslamate/cars/$car_id/charge_port_door_open`         | true                                                                                        | Indicates if the charger door is open                                                 |
| `teslamate/cars/$car_id/charger_actual_current`        | 2.05                                                                                        | Current amperage supplied by charger                                                  |
| `teslamate/cars/$car_id/charger_phases`                | 3                                                                                           | Number of charger power phases (1-3)                                                  |
| `teslamate/cars/$car_id/charger_power`                 | 48.9                                                                                        | Charger Power                                                                         |
| `teslamate/cars/$car_id/charger_voltage`               | 240                                                                                         | Charger Voltage                                                                       |
| `teslamate/cars/$car_id/charge_current_request`        | 40                                                                                          | How many amps the car wants                                                           |
| `teslamate/cars/$car_id/charge_current_request_max`    | 40                                                                                          | How many amps the car can have                                                        |
| `teslamate/cars/$car_id/scheduled_charging_start_time` | 2019-02-29T23:00:07Z                                                                        | Start time of the scheduled charge                                                    |
| `teslamate/cars/$car_id/time_to_full_charge`           | 1.83                                                                                        | Hours remaining to full charge                                                        |
| `teslamate/cars/$car_id/tpms_pressure_fl`              | 2.9                                                                                         | Tire pressure measure in BAR, front left tire                                         |
| `teslamate/cars/$car_id/tpms_pressure_fr`              | 2.8                                                                                         | Tire pressure measure in BAR, front right tire                                        |
| `teslamate/cars/$car_id/tpms_pressure_rl`              | 2.9                                                                                         | Tire pressure measure in BAR, rear left tire                                          |
| `teslamate/cars/$car_id/tpms_pressure_rr`              | 2.8                                                                                         | Tire pressure measure in BAR, rear right tire                                         |
| `teslamate/cars/$car_id/tpms_soft_warning_fl`          | true                                                                                        | Indicates if the Tire pressure measure is soft warning, front left tire               |
| `teslamate/cars/$car_id/tpms_soft_warning_fr`          | false                                                                                       | Indicates if the Tire pressure measure is soft warning, front right tire              |
| `teslamate/cars/$car_id/tpms_soft_warning_rl`          | false                                                                                       | Indicates if the Tire pressure measure is soft warning, rear left tire                |
| `teslamate/cars/$car_id/tpms_soft_warning_rr`          | false                                                                                       | Indicates if the Tire pressure measure is soft warning, rear right tire               |
| `teslamate/cars/$car_id/active_route_destination`      | Home                                                                                        | DEPRECATED: Navigation destination name (or "nil")                                    |
| `teslamate/cars/$car_id/active_route_latitude`         | 35.278131                                                                                   | DEPRECATED: Navigation destination latitude (or "nil")                                |
| `teslamate/cars/$car_id/active_route_longitude`        | 29.744801                                                                                   | DEPRECATED: Navigation destination longitude (or "nil")                               |
| `teslamate/cars/$car_id/active_route`                  | _See below_                                                                                 | Navigation details (json blob)                                                        |
| `teslamate/cars/$car_id/center_display_state`          | 0                                                                                           | Center Display State                                                                  |

:::note
`$car_id` usually starts at 1
:::

### `active_route` payload examples

Routing to a destination.

```json
{
  "destination": "Home",
  "energy_at_arrival": 73,
  "miles_to_arrival": 6.485299,
  "minutes_to_arrival": 23.466667,
  "traffic_minutes_delay": 0.0,
  "location": {
    "latitude": 35.278131,
    "longitude": 29.744801
  },
  "error": null
}
```

Not routing to a destination.

```json
{
  "error": "No active route available"
}
```
