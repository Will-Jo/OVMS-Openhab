# OVMS-Openhab

Open Vehicle Monitoring System is a small device that plugs into the OBD port on your EV - head over to openvehicles.com for more details.
This simple addon for OpenHab enables MQTT communication between Openhab <-> OVMS, and implements a small widget in openhab to display some simple charging info.

The OVMS module itself is used in many EVs, so, the concept should be re-usable.
The icons and settings are currently tailored for a Renault Twizy.

<img width="330" height="504" alt="image" src="https://github.com/user-attachments/assets/3d53e173-6f9b-49a7-9a91-f22f43bbee8d" />

To implement this, there are a few steps needed:

1) You need to have a MQTT server running, I use mosquitto in a docker container.
2) You need to install the MQTT addon to openhab and connect it to the above MQTT server.
3) You need to configure the protocol “Server V3 (MQTT)” in OVMS webui.
    This is done under the Config tab, also, set it to autostart.
    Configure your MQTT server, username and password, the topic prefix should be “ovms/”
    Once this is complete, you should start to see messages arriving in your MQTT server. I use MQTT explorer or MQTTX to view the MQTT server activity.
4) On Openhab, copy in the .items and .things files to these locations:
    openhab/conf/things/ovms.things
    openhab/conf/items/ovms.items
5) In openhab, create a new widget under developer tab and paste the OVMSWidget yaml code in.
