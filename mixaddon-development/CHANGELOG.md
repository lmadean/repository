# Changelog

## 0.210

- Startup no longer stops because this add-on sees itself as another Mixlight add-on. When a different add-on really is running, the log names that add-on and the slug this one detected for itself.

## 0.209

- A stopped or crashed Mixlight add-on no longer blocks startup. When another one really is running, the log names that add-on, whether it was seen from MQTT or the Supervisor, and its state.

## 0.208

- Only dimmer levels and light colours are saved. Reloading the configuration page does not drop a level that is being saved, startup does not replace those saved levels with defaults, and a broken settings file is left unchanged and shown in Home Assistant.
- The configuration editor follows the Home Assistant theme: dark when Home Assistant is dark, light when it is light, and it switches when Home Assistant switches.
- Input boards are no longer given a DMX line when the configuration is saved. They have no bus setting. A DMX line already written on an input board is left as it is.
- Saving the configuration keeps boards and settings the editor does not show, including covers, climates, and options such as timer and area.
- The configuration editor asks whether a new relay board is on Mixbus or DMX, shows that bus on output boards, and saves each board's dmx as chosen or loaded. Dimming and RGB boards are saved as DMX. An output board with no DMX setting is saved as DMX. RGB channel orders rgb, rbg, grb, gbr, brg, and bgr are shown and saved as written. A dimmer or an RGB light on Mixbus cannot be saved, and a restored backup is refused in that case.
- The add-on stays idle when another Mixlight add-on is already running, and the log names that add-on. It starts on its own once the other one stops. Restarting this add-on does not count as another one. Two add-ons that start in the same couple of seconds, or that both start while the broker is down, can both run. If the broker dies first and keeps the last online message, the other add-on stays idle until this one starts again.
- Entities you remove from the configuration disappear from Home Assistant after a restart. Entities that are still configured stay, with their state unchanged, and lights and covers do not move.
- If the add-on cannot use SPI, the log explains how to uncomment `#dtparam=spi=on` in `config.txt` on the boot partition and reboot. It then waits and exits so it can restart. A shield that is there but does not answer is unchanged.
- When saved entity states have not been stored yet, startup logs a warning and continues with the default states.

## 0.207

- If the shield does not start, or it never answers, the add-on logs the error, waits, and exits so it can restart, instead of staying up and reporting that it is fine. A short or incomplete reply is logged and that command fails, instead of crashing the service.
- Wall buttons and relays still work when the MQTT broker is stuck, the network drops, or the broker is not running at startup. The add-on connects when the broker comes up, and lights and covers do not move on their own.
- Boards marked `dmx: true` (unquoted) are now treated as DMX boards, as the docs always said, so check those boards.

## 0.206

- Restarting the MQTT broker no longer clears input readings or shows them unavailable. When the broker is back, each entity shows the state it kept during the outage, and lights and covers do not move.

## 0.205

- The first press of a button after the add-on starts switches the light. A button that is already held, or a switch that is already on, does not change the lights when the add-on starts.

## 0.204

- With two or more relay boards, each relay shows the right state in Home Assistant, and switching one relay leaves the others unchanged.
- With no relay boards configured, the add-on no longer sends the relay data command to the shield. Setups with one or more relay boards are unchanged.
- A temperature, humidity, or other input reading with no value now shows as unavailable in Home Assistant instead of 0. A real reading of 0 still shows as 0. 0% humidity shows as unavailable. The same happens when that board does not answer or the read fails. Input-board ADC entries have no sample, so they stay unavailable and can be removed.
- Lights, switches, dimmers, and other outputs keep their last state. They follow the add-on only: a crash, kill, or power loss shows them unavailable. A normal stop removes the entities.
- A thermostat stays available when it has no room temperature and shows that temperature as unknown. Heating and cooling are unchanged.
- If the broker reconnects, the last published state is sent to Home Assistant again and nothing in the add-on acts on that replay.

## 0.203

- No changes to the add-on itself since 0.202.

## 0.202

- The startup log no longer shows a Python syntax warning from the shield service.
- Board, output, button, and sensor names and addresses now show exactly as typed, including quotes and symbols.
- Loading the configuration shows an error when it fails, and Reload reports success only when the file was actually loaded.
- Closing or reloading the page warns you when there are unsaved changes.
- Save stays off until a configuration has loaded. An empty or unreadable configuration can't be saved over the file, and Restore stays available to recover a backup.
- A configuration that is incomplete or in the wrong shape is left unused, and the one already on screen stays.
- If the configuration file changed since it was loaded, Save asks you to reload it first.
- When the configuration has settings the editor can't show, it still appears, and Save stays off so those settings aren't lost.
- The configuration editor now refuses to save an empty or broken configuration instead of overwriting it.
- A configuration that cannot be read is no longer opened as an empty editor, and saving is refused when the file has settings the editor cannot keep.
- Add-on icons and logos now have transparent backgrounds, and the Mixlight 64-bit add-on shows its icon and logo.
- Saved entity states are kept in `/config/mixlight-settings.json`. On startup, `/data/store.json` is copied there when the new file is missing, and the old file is left in place.

## 0.201

- No changes to the add-on itself since 0.200.

## 0.200

- Renamed back to Mixlight Development and marked as experimental in the add-on store.
- Fixed the spelling of "Raspberry" in the add-on description.
- No changes to the add-on itself since 0.140. This is the build tested before Mixlight 64-bit 0.201.

## 0.140

- Development build for testing. Mixlight 64-bit first ships as 0.201; use that for normal use.
- No longer opens port 8099 on your network; open Mixlight from the sidebar.
