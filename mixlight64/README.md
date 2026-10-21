# Mixlight 64-bit

Mixlight 64-bit (slug `mixlight64`) is the add-on for a Raspberry Pi 3, 4 or 5 running 64-bit Home Assistant OS.

Mixlight Development is a test build. Use Mixlight 64-bit for normal use.

Run only one Mixlight add-on at a time. They share the shield. On 64-bit Home Assistant OS, stop Mixlight Development (it starts on boot and uses the same default MQTT client id) before you start this one.

Add-on options do not carry over. `/config/mixlight.yaml` does, on the same install, and after an OS reinstall only if you restore a backup that includes Home Assistant settings.

The Documentation page explains how to read the board, and how to move a 32-bit install onto 64-bit Home Assistant OS.
