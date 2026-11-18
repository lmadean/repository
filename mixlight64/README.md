# Mixlight 64-bit

Mixlight 64-bit (slug `mixlight64`) is the add-on for a Raspberry Pi 3, 4 or 5 running 64-bit Home Assistant OS.

Mixlight Development is a test build. Use Mixlight 64-bit for normal use.

Run only one Mixlight add-on at a time. They share the shield. On 64-bit Home Assistant OS, stop Mixlight Development (it starts on boot and uses the same default MQTT client id) before you start this one.

Add-on options do not carry over. `/config/mixlight.yaml` does, on the same install.

The Documentation page explains how to read the board.

## Installation

Follow these steps to install Mixlight 64-bit on a Raspberry Pi 3, 4 or 5 running 64-bit Home Assistant OS.

Home Assistant calls the add-on store the App store. Open it from **Settings** > **Apps** > **Install app**. The steps below use the names on that screen. See [Installing and managing apps](https://www.home-assistant.io/common-tasks/os/apps/).

1. Enable SPI on the Raspberry PI. On the boot partition, edit config.txt and uncomment the line: #dtparam=spi=on. Then reboot the Pi.

2. Install, configure, and start the Mosquitto broker app.
   - Go to **Settings** > **Apps** > **Install app**.
   - Select **Mosquitto broker**.
   - On the **Info** tab, select **Install**.
   - On the **Configuration** tab, set the broker options, then select **Save**.
   - On the **Info** tab, select **Start**.

3. Add the Mixlight repository.
   - Go to **Settings** > **Apps** > **Install app**.
   - Select **Menu** > **Repositories**.
   - Select **Add**.
   - In the **Add repository** dialog, under **URL**, enter `https://github.com/lmadean/repository`, then select **Add**.

4. Create `/config/mixlight.yaml` with a Mixlight configuration.
   - With **File editor**, or a similar app: go to **Settings** > **Apps** > **File editor** and select **Install**. On the **Info** tab, select **Start**, then **Open Web UI**. Create `mixlight.yaml` in `/config`.

5. Install Mixlight 64-bit, set its options, start it, and check the log.
   - In the App store, select **Mixlight 64-bit**.
   - On the **Info** tab, select **Install**.
   - On the **Configuration** tab, set the options, then select **Save**.
   - On the **Info** tab, select **Start**.
   - Open the **Log** tab and check it for problems.
   - Once Mixlight 64-bit is running, the sidebar configuration editor can write `/config/mixlight.yaml` if it is missing. Open **Mixlight** from the sidebar. Add at least one board, then select **Save Configuration**. That writes `/config/mixlight.yaml`.
   - If Mixlight 64-bit is already running, open it under **Settings** > **Apps** and, on the **Info** tab, select **Restart** so it loads the file.

6. On a development board, enable serial. On the boot partition, add these lines to config.txt, then reboot the Pi:

   ```
   enable_uart=1
   dtoverlay=disable-bt
   ```
