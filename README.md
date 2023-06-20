# feral-interactive-controllers
Updated controller configuration files for Feral Interactive Mac games like Tomb Raider, Life is Strange.

This repo contains pre-made configuration files. For new controllers or firmwares that change a controller's product ID, follow the guide below. It doesn't hurt to have multiple files, since the same controller might need a different file depending on the firmware.

## Adding a new configuration

Previously my Xbox One controller would only work wired. For official support email support@feralinteractive.com

First, if your Xbox controller isn't detected by Mac at all via Bluetooth, you need to update the controller firmware via an Xbox or the Windows Xbox Accessories app.

Generate a System Report in Tomb Raider launcher to find out your controller's Product ID. Mine looked like:
```
Xbox Wireless Controller:
Vendor ID: 0x045E              
Product ID: 0x0B20
Firmware Version: 5.17.3202.0
```

then convert the Product ID from hex to decimal. 0x0B20 in hex is 2848 in decimal.

Then you need to edit the game's `XboxOneControllerSBluetoothv3.plist` file.

I changed the ProductID to to make it work. Also change ButtonBack to make the select button work. This also works on Series.

```
<key>ProductID</key>
<integer>2848</integer>
<key>ButtonBack</key>
<string>9:11</string>
```

## Finding configuration file location

```
The Xbox One controller was not available at the time of development of our Mac version of the game, so I have attached a file to this email that will add support for it. Please first download this file and carry out the following steps:
 
Find your installation of the game:
If you are using a Mac App Store version of the game, the game's application icon will be in your Applications folder.
If you are using a Steam version of the game, the game's application icon can be found by Right Clicking game in Steam Library, then selecting Properties > Local Files > Browse Local Files.
Right click the game's application icon and choose 'Show Package Contents' from the dropdown menu.
Open the 'Contents' folder, then the 'Resources' folder and finally 'Input Devices'.
Drag the attached .plist file into the folder (you may be asked to Authenticate using your username and password, please do so).
Close the Finder window.

If you are using a Steam version of the game, we also recommend that you follow the steps below:
 
Ensure your Xbox One controller is not switched on.
Open the Steam Client.
Click 'Steam' in the top menu bar (next to the Apple logo in the top left of your Mac's screen).
In the dropdown that appears, click 'Preferences'.
In the new window that opens, select 'Controller' in the left list, then click 'General Controller Settings'.
Another window will open. Ensure that 'Xbox Configuration Support' is not checked.
Quit Steam.
Launch Steam.
Switch on Xbox One S controller to connect via Bluetooth.
Launch game.

You should now be able to use the controller in the game. Please let us know if this helps. 
```
