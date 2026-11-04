# Changelog

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
