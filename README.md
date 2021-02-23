# hubitat_switchBot

This provides various driver capabilities for SwitchBot devices, including the humidity/temperature sensor, bot, curtain, humidifier, and hub IR functionality.  

Note that all operations have a cloud (internet) interaction.  The HTTP accesses are made according to the SwitchBotAPI reference:
* https://github.com/OpenWonderLabs/SwitchBotAPI

# Manual Installation instructions:

* In the *Drivers Code* section of Hubitat, add the switchbotSystem, switchbotBot, switchbotCurtain, switchbotIRDevice, and switchbotMeter drivers.
* In the *Devices* section of Hubitat, add a *New Virtual Device* of type SwitchBot System
* On the configuration page for the newly created *Device*, enter these details and then Save Preferences:
    * Your Open Token, which can be acquired as described in the SwitchBotAPI reference: https://github.com/OpenWonderLabs/SwitchBotAPI#getting-started
    * The refresh interval in seconds
        * Note that there is a documented limit of 1000 API accesses per day, and each device refresh or action is at least one access.  Set this number accordingly.

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
