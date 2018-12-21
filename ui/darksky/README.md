# Dark Sky Weather Card

The Dark Sky Weather Card provides current and forecasted weather conditions using the Dark Sky weather platform. The card 
is configured by passing sensor entities from the Dark Sky Sensor platform in to the card.  It is also possible to configure
the card's capabilities through configuration flags.

**Installation**
------------------------------
1. Add **dark-sky-weather-card.js** to your **www/custom_ui/** directory.  If you don't have this directory (this is your first
custom card), you will need to create it.

2. Download the amcharts icons from https://www.amcharts.com/dl/svg-weather-icons/ and put them in **www/icons/weather_icons**.  Create 
the directories if necessary. You should end up with an **animated** directory and a **static** directory inside the **weather_icons** directory.

**Configuration**
------------------------------
1. Add the Dark Sky sensor platform to your configuration.yaml or sensors.yaml or wherever you keep your sensor configuration.

~~~~  
- platform: darksky
    api_key: <Your Dark Sky API Key>
    forecast:
      - 0
      - 1
      - 2
      - 3
      - 4
      - 5
    monitored_conditions:
      - icon
      - summary
      - nearest_storm_distance
      - nearest_storm_bearing
      - humidity
      - temperature
      - temperature_high
      - temperature_low
      - apparent_temperature
      - apparent_temperature_high
      - apparent_temperature_low
      - wind_speed
      - wind_bearing
      - precip_type
      - precip_probability
      - precip_accumulation
      - precip_intensity
      - precip_intensity_max
      - uv_index
      - daily_summary
      - pressure
      - visibility
    update_interval:
      minutes: 5
~~~~

The next two steps are completed differently based on the version of HA you are using:
- Pre 0.84 or if using yaml mode in 0.84 or above : Add to your ui-lovelace.yaml file.
- Using storage mode in 0.84 or above use the "Raw Config Editor" to add the reference and definition to the config.

2. Add the card reference at the top of the configuration
~~~~
resources:
  - url: /local/custom_ui/dark-sky-weather-card.js?v=7.1
    type: module
~~~~

3. Add the card definition:
~~~~
type: custom:dark-sky-weather-card
entity_sun: sun.sun
entity_daily_summary: sensor.dark_sky_daily_summary
entity_current_conditions: sensor.dark_sky_icon
entity_humidity: sensor.dark_sky_humidity
entity_pressure: sensor.dark_sky_pressure
entity_temperature: sensor.dark_sky_temperature
entity_visibility: sensor.dark_sky_visibility
entity_wind_bearing: sensor.dark_sky_wind_bearing
entity_wind_speed: sensor.dark_sky_wind_speed
entity_forecast_high_temp_1: sensor.dark_sky_daytime_high_temperature_1
entity_forecast_high_temp_2: sensor.dark_sky_daytime_high_temperature_2
entity_forecast_high_temp_3: sensor.dark_sky_daytime_high_temperature_3
entity_forecast_high_temp_4: sensor.dark_sky_daytime_high_temperature_4
entity_forecast_high_temp_5: sensor.dark_sky_daytime_high_temperature_5
entity_forecast_low_temp_1: sensor.dark_sky_overnight_low_temperature_0
entity_forecast_low_temp_2: sensor.dark_sky_overnight_low_temperature_1
entity_forecast_low_temp_3: sensor.dark_sky_overnight_low_temperature_2
entity_forecast_low_temp_4: sensor.dark_sky_overnight_low_temperature_3
entity_forecast_low_temp_5: sensor.dark_sky_overnight_low_temperature_4
entity_forecast_icon_1: sensor.dark_sky_icon_1
entity_forecast_icon_2: sensor.dark_sky_icon_2
entity_forecast_icon_3: sensor.dark_sky_icon_3
entity_forecast_icon_4: sensor.dark_sky_icon_4
entity_forecast_icon_5: sensor.dark_sky_icon_5
entity_summary_1: sensor.dark_sky_summary_1
entity_summary_2: sensor.dark_sky_summary_2
entity_summary_3: sensor.dark_sky_summary_3
entity_summary_4: sensor.dark_sky_summary_4
entity_summary_5: sensor.dark_sky_summary_5
locale: en
static_icons: false
sunset: true
tooltips: true
tooltip_bg_color: 'rgb( 75,155,239)'
tooltip_border_color: orange
tooltip_border_width: 3
tooltip_caret_size: 10
tooltip_fg_color: '#fff'
tooltip_left_offset: -5
tooltip_width: 100
~~~~

**Flags**
--------------------------
| Flag                 | Values                       | Usage                                                                         |
|----------------------|------------------------------|-------------------------------------------------------------------------------|
| locale               | **en** / fr / de / it / etc. | Sets locale display of day names and time formats                             |
| static_icons         | true / **false**             | Switches between static (true) and animated (false) icons                     |
| sunset               | true / **false**             | Enables display of sunset and sunrise indicators                              |
| tooltips             | true / **false**             | Enables tooltips that show daily forecast summary                             |
| tooltip_width        | **110**                      | Sets the width of the tooltip in px                                           |
| tooltip_bg_color     | **rgb( 75,155,239)**         | Sets the background color of the tooltip (rgb / # / color)                    |
| tooltip_fg_color     | **#fff**                     | Sets the foreground color of the tooltip (rgb / # / color)                    |
| tooltip_border_color | **rgb(255,161,0)**           | Sets the color of the tooltip border including the caret (rgb / # / color)    |
| tooltip_border_width | **1**                        | Sets the width of the tooltip border in px                                    |
| tooltip_caret_size   | **5**                        | Sets the size of the caret (the little arrow pointing down) in px             |
| tooltip_left_offset  | **-12**                      | Sets the offset of the left edge of the tooltip. Specified in negative (-) px |