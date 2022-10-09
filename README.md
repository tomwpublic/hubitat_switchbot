# hubitat_switchBot

This provides various driver capabilities for SwitchBot devices, including the humidity/temperature meter, bot, curtain, humidifier, strip light, smart lock, motion sensor, contact sensor, plug mini, and hub IR functionality.  

Note that all operations have a cloud (internet) interaction.  The HTTP accesses are made according to the SwitchBotAPI reference:
* https://github.com/OpenWonderLabs/SwitchBotAPI

Installing with Hubitat Package Manager (HPM) is recommended.

# Manual Installation instructions:

* In the *Drivers Code* section of Hubitat, add any drivers that apply to your system: switchbotSystem (always required), switchbotBot, switchbotCurtain, switchbotIRDevice, switchbotMeter, switchbotHumidifier, switchbotStripLight, and switchbotSmartLock.
* In the *Devices* section of Hubitat, add a *New Virtual Device* of type SwitchBot System
* On the configuration page for the newly created *Device*, enter these details and then Save Preferences:
    * Your Token and Secret Key, which can be acquired as described in the SwitchBotAPI reference: https://github.com/OpenWonderLabs/SwitchBotAPI#getting-started
    * The refresh interval in seconds
        * Note that there is a documented limit of 1000 API accesses per day, and each device refresh or action is at least one access.  Set this number accordingly.
* OPTIONAL: in the *Apps Code* section of Hubitat, add the switchbotEventsApp.  This step is necessary if you plan to use the webhook feature for real-time device status updates (currently supported for Meter, Meter Plus, Strip Light, Smart Lock, Motion Sensor, and Contact Sensor).
    * In the *Apps* section of Hubitat, select *Add User App* and install the SwitchBot Events app.  Select your SwitchBot System device and click Done.
    * Note that some devices only report a subset of their attributes in real-time events.  For example, the Contact Sensor only reports open/close status and the Motion Sensor only reports active/inactive status.

# Usage instructions:

* Refresh the device configuration page and ensure your devices appear in the JSON *devices* under State Variables
* Use createChildDevices to create the appropriate child devices for all known device types
* Most device actions are self-explanatory.  Look around and try things out!
* For SwitchBot IR Device:
    * Off and On are shortcuts for the *turnOff* and *turnOn* commands if supported by the device
    * Other built-in commands are documented in the SwitchBotAPI reference:  https://github.com/OpenWonderLabs/SwitchBotAPI#command-set-for-virtual-infrared-remote-devices .  Any commands with *command parameter* 'default' can be left blank.
    * For custom commands, the 'command' input is the button name from the SwitchBot app.  The 'parameter' input can be left blank.

# Disclaimer

I have no affiliation with any of the companies mentioned in this readme or in the code.
