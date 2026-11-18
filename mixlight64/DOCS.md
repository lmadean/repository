# Mixlight 64-bit

Mixlight 64-bit (slug `mixlight64`) is a separate add-on for a Raspberry Pi 3, 4 or 5 running 64-bit Home Assistant OS. It does not replace or upgrade the 32-bit Mixlight add-on.

Mixlight Development is a test build. Use Mixlight 64-bit for normal use.

## Run only one Mixlight add-on at a time

The Mixlight add-ons share the shield, so run only one of them.

On 64-bit Home Assistant OS the other one that can start is Mixlight Development. It is built for aarch64, it starts on boot, and it uses the same default MQTT client id, `MIXLIGHT`.

Stop it before you start Mixlight 64-bit:

1. Go to **Settings** > **Apps** > **Mixlight Development**.
2. Select **Stop**.
3. Turn off **Start on boot**, or uninstall the app.

Turning **Start on boot** off does not stop the app, so stop it first. Off sets boot to `manual`: the app stays stopped until you start it, and you can turn **Start on boot** back on. That is not `manual_only`. `manual_only` is set in the app config, the toggle stays off, and it cannot be turned on.

Home Assistant documents the boot setting on [App configuration](https://developers.home-assistant.io/docs/apps/configuration/) and in the [configuration reference](https://contributors.home-assistant.io/apps/reference/configuration/). `auto` starts the app at boot. `manual` starts it only when you start it. `manual_only` never starts it at boot and does not let that be changed.

## What is kept, and what you set again

Add-on options do not carry over. They live on that add-on's Configuration tab: `mqtt_local`, `mqtt_remote`, `mqtt_broker`, `mqtt_port`, `mqtt_user`, `mqtt_password`, `mqtt_keepalive`, `mqtt_client_id`, `hardware_revision`, `hass_prefix`, and `log_level`. The default MQTT client id is `MIXLIGHT`. The default `hass_prefix` is `homeassistant`.

`/config/mixlight.yaml` and `/config/mixlight-backup/` are shared files. On the same Home Assistant install they are still there.

Add-on-internal data is lost. That is `/data/mixlight.yaml` and `/data/store.json`, which holds saved entity values.

## Check that this is 64-bit Home Assistant OS

**Settings** > **System** > **Hardware** shows the board name from Home Assistant's Raspberry Pi hardware platform ([hardware.py](https://github.com/home-assistant/core/blob/dev/homeassistant/components/raspberry_pi/hardware.py)). On 32-bit that name is "Raspberry Pi 3 (32-bit)" or "Raspberry Pi 4 (32-bit)". On 64-bit it is "Raspberry Pi 3", "Raspberry Pi 4", or "Raspberry Pi 5".

The board ids behind those names are `rpi3` and `rpi4` on 32-bit, and `rpi3-64`, `rpi4-64`, and `rpi5-64` on 64-bit. Those are the ids the UI shows, not the `rpi*_64` build-target names.

In **System information** (**Settings** > **System** > **Repairs**, three-dots menu, **System information**), **Board** and **CPU architecture** show different values. **Board** is under Home Assistant Supervisor and is the board id: `rpi3-64`, `rpi4-64`, or `rpi5-64` on 64-bit, and `rpi3` or `rpi4` on 32-bit. **CPU architecture** is under Home Assistant Core. On 64-bit it is `aarch64`, which means 64-bit. Home Assistant's [32-bit deprecation post](https://www.home-assistant.io/blog/2025/05/22/deprecating-core-and-supervised-installation-methods-and-32-bit-systems/) uses that CPU architecture field. The labels are `board` and `arch` in the [Supervisor](https://github.com/home-assistant/core/blob/dev/homeassistant/components/hassio/system_health.py) and [Core](https://github.com/home-assistant/core/blob/dev/homeassistant/components/homeassistant/system_health.py) system health info.
