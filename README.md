# dv-loco-analogue-control-mod (Continued)

**See https://www.nexusmods.com/derailvalley/mods/687 for the rewrite of the original mod by the original author**

Nexus mods page: https://www.nexusmods.com/derailvalley/mods/490

Derail Valley mod for analogue control in locomotives

# REGENERATE THE CONFIG.JSON AFTER EVERY UPDATE TO PREVENT VERSION MIGRATION ISSUES

There is only one joystick configured in the game. Multiple attached controllers will fight each other. 99% Sure this wont work with VR.

This mod puts the value on your controller axis into the in game axis.
You should use a controller which holds its current value such as a HOTAS throttle.
Don't try and use something like an xbox controller.

For button mappings please use your joystick/controller utility or 3rd party software to map buttons to keys

## Using the Mod

 - Install Unity Mod Manager
 - Copy the `LocoAnalogueControlMod.dll` and `Info.json` into the `Derail Valley\Mods\LocoAnalogueControlMod` folder
 - Run Derail Valley to generate `config.json` in the mod folder
 - Update `config.json` for each input.
	 - `AxisName` is the in game joystick axis name which is assigned an axis number. [See Understanding Joystick Mapping](#understanding-joystick-mapping). Leave any unused inputs as a blank string
	 - `Scaling` Allows you to apply a scaling to an axis in case it doesnt saturate the full range. Applying a negative scaling will invert the axis
	 - `FullRange` takes a -1 to 1 range and maps it to 0 to 1
	 - `Debug` enables printing the value being applied to the mod manager log. Enable this for first time setup.
	 - `DeadZoneCentral` is the percentage of the axis where an input value will produce a 0 value expressed as a float. 0.1 = 10%
	 - `DeadZoneEnds` is the percentage of the axis where an input value will produce a  -1/1 value expressed as a float. 0.1 = 10% 
 - Disable and re-enable the mod from the mod manager log window open (`ctrl + F10`) to reload the config and hop into a locomotive
 - With the mod manager log window open move your controller axis and observe the output in the log window
	 - The reverser axis should be from -1 to 1. All other axis are from 0 to 1
 - Correctly set the `config.json` then disable and re-enable the mod

## Understanding Joystick Mapping

The in game axis names need to be provided to the config json to grab the correct axis number from your controller. All controllers use the same axis names so multiple controllers are not supported unless the devs change this behaviour.

A simple way to find the controller axis numbers is through Windows game controllers test utility.
This can be opened with `WinKey + R` then typing `joy.cpl`. Select the apropriate device (there should only be one connected) and select `Properties` followed by `Test`. You can then get the game axis name from the table.

| Input Axis Number | Game Axis Name | Windows Axis Name| Inverted in game |
| -- | -- | -- | -- |
| 0 | Oculus_GearVR_LThumbstickX | X Axis | False |
| 1 | Oculus_GearVR_LThumbstickY | Y Axis | True |
| 2 | Oculus_GearVR_RThumbstickX | Z Axis | False |
| 3 | Oculus_GearVR_RThumbstickY | X Rotation| True |
| 4 | Oculus_GearVR_DpadX | Y Rotation | False |
| 5 | Oculus_GearVR_DpadY | Z Rotation| True |
| 11 | Oculus_GearVR_LIndexTrigger | | False |
| 12 | Oculus_GearVR_RIndexTrigger | | False |

## Building from Source

You will need Visual Studio and Derail Valley to be installed.

- If not done already, install the latest version of the mod using Unity Mod Manager.
- Set the `DVInstallPath` environment variable to the location of your installation of Derail Valley.
  For example this might be `C:\Program Files (x86)\Steam\steamapps\common\Derail Valley\`.
  This can be done either by:
  - Running `setx DVInstallPath "C:\Program Files (x86)\Steam\steamapps\common\Derail Valley"` in Run or the Command Prompt.
  - Using the "Rnvironment Variables" window in "System Properties".
- Open the `LocoAnalogueControlMod.sln` file.
- Go to the "Build" menu and click "Build Solution". This should build the mod and install it.
