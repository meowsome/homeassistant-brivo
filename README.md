Brivo Smarthome Compatability with Home Assistant

Brivo Smarthome is a smart home system that many apartments use for smart locks and lights. This repository includes template config files for interacting with the Brivo Smarthome system. I was able to figure this out by visiting the Brivo Smarthome web panel and observing the packets that were being sent to the Brivo API upon each action I performed.

Instructions:
1. Login to https://smarthome.brivo.com/
2. Click on your unit
3. Open the Inspect Element window on Chrome
4. Navigate to the Network tab and search for `token`
5. Copy the token into [secrets.yaml](secrets.yaml) under the `brivo_token` entry
6. For each light you want to add, add a new entry to [brivo_light.yaml](brivo_light.yaml)
    1. Call it whatever you'd like in `friendly_name`
    2. Using Inspect Element, find the light's `main-icon` div and copy the 6-digit from the `device-id` attribute to `device_id` in the config file
    3. To make the status work, change the `sensor.xxxx` sensor name under `value_template`
7. Do the same for each lock

Unfortunately, the apartment I lived in did not have a smart thermostat, so I was not able to add that to this repository. 

Hope you enjoy! 
