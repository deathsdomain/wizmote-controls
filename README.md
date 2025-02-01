# WizMote Device Controls

This is a Home Assistant blueprint that allows a custom set of actions to be triggered when buttons on a WizMote are pressed.

It works with a custom component installed on an ESPHome device built by [jesserockz](https://github.com/jesserockz/wizmote-esphome)

Use the following in an ESPHome configuration file to integrate with this blueprint:

```yaml
# sample esphome configuration
external_components:
  - source: github://jesserockz/wizmote-esphome
    components:
      - esp_now
      - wizmote

esp_now:

wizmote:
  on_button:
    - homeassistant.event:
        event: esphome.wizmote_action
        data:
          mac: !lambda 'return format_hex(data.bssid, 6);'
          button: !lambda 'return data.button;'
          sequence: !lambda 'return data.sequence;'
```

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fdeathsdomain%2Fwizmote-controls%2Fblob%2Fmain%2Fwizmote-controls-blueprint.yaml)
