# Changelog

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

## 0.201

- No changes to the add-on itself since 0.200.

## 0.200

- Renamed back to Mixlight Development and marked as experimental in the add-on store.
- Fixed the spelling of "Raspberry" in the add-on description.
- No changes to the add-on itself since 0.140. This is the build tested before Mixlight 64-bit 0.201.

## 0.140

- Development build for testing. Mixlight 64-bit first ships as 0.201; use that for normal use.
- No longer opens port 8099 on your network; open Mixlight from the sidebar.
