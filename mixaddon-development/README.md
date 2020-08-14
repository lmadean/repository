# Home Assistant Mixlight Add-on (Development)

## Installation

Follow theese steps for a successfull instalation.

1. Enable SPI on the Raspberry PI. On the boot partition, edit 
   config.txt and uncomment the line:
        #dtparam=spi=on 
2. Search for the "Mosquitto broker" add-on in the Supervisor 
   add-on store and install it. Configure the addon and start it.
3. Add the mixlight repository in the Supervisor add-on store
   https://github.com/lmadean/mixaddon
4. Search for the "File editor" add-on in the Supervisor add-on store
   and install it. Configure the addon and start it. 
5. Using the "File editor" create a new file called mixlight.yaml and 
   create a mixlight configuration.
6. Search for the "Mixlight" add-on in the Supervisor add-on store
   and install it. 
7. Start the "Mixlight" add-on.
8. Check the logs for any problems.