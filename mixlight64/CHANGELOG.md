# Changelog

## 0.203

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

- First release of Mixlight 64-bit (slug `mixlight64`), a separate add-on for 64-bit Home Assistant OS on aarch64. It does not replace or upgrade the 32-bit Mixlight add-on. Install it fresh and set the options again; options do not carry over. /config/mixlight.yaml does on the same install; after reinstalling the OS it carries over only when you restore a backup that includes Home Assistant settings. Stop Mixlight Development before starting this one. The web UI opens from the sidebar.
