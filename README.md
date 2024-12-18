#### Update 2024-02-11

Xbox controller plists have been updated to fix dpad issues in Sleeping Dogs, GRID Autosport, etc. 

If they cause issues in other games please open an issue and try the 
[old versions of the files](https://github.com/axu2/feral-interactive-mac-controllers/tree/00bbe01c3b432c76e9e4e8659f898449588e88a0).



# feral-interactive-controllers
Fixes Xbox controller support for Tomb Raider, Life is Strange, Bioshock, Sleeping Dogs, and other Feral Interactive Mac games due to recent controller firmware updates. You can view your controller's firmware version in `System Report`. This repo is only tested on the following firmware version, earlier ones may cause issues like crashes or connectivity issues.

```
Xbox Wireless Controller:
Vendor ID: 0x045E              
Product ID: 0x0B20
Firmware Version: 5.17.3202.0
```

This repo contains pre-made configuration files. For new controllers or firmwares, follow the guide below. Feel free to PR any other new controllers. It doesn't hurt to have multiple files, since the same controller might need a different file depending on the firmware. 

If your Xbox controller isn't detected by Mac at all via Bluetooth, you need to update the controller firmware via an Xbox or the Windows Xbox Accessories app. 

If you don't have access to either, you can update the controller firmware via a Windows VM https://www.vmware.com/products/fusion.html

## Supported Games
* Tomb Raider (2013)
* Rise of the Tomb Raider
* Shadow of the Tomb Raider
* Life is Strange
* Life is Strange 2
* Bioshock Remastered
* Bioshock 2 Remastered
* Sleeping Dogs
* GRID Autosport
* Deus Ex: Mankind Divided
* Batman: Arkham City GOTY

Feel free to open a PR adding to the list of supported games! All feral ports should work but adding to the list makes search engine optimization easier.

## Support Email Text (plist file attachment in repo)

The Xbox One controller was not available at the time of development of our Mac version of the game, so I have attached a file to this email that will add support for it. Please first download this file and carry out the following steps:
 

* Find your installation of the game:

  * If you are using a **Mac App Store version** of the game, the game's application icon will be in your Applications folder.

  * If you are using a **Steam version** of the game, the game's application icon can be found by Right Clicking game in Steam Library, then selecting Properties > Local Files > Browse Local Files.

* Right click the game's application icon and choose 'Show Package Contents' from the dropdown menu.

* Open the 'Contents' folder, then the 'Resources' folder and finally 'Input Devices'.

* Drag the attached .plist file into the folder (you may be asked to Authenticate using your username and password, please do so).

* Close the Finder window.


If you are using a Steam version of the game, we also recommend that you follow the steps below:
 
* Ensure your Xbox One controller is not switched on.

* Open the Steam Client.

* Click 'Steam' in the top menu bar (next to the Apple logo in the top left of your Mac's screen).

* In the dropdown that appears, click 'Preferences'.

* In the new window that opens, select 'Controller' in the left list, then click 'General Controller Settings'.

* Another window will open. Ensure that 'Xbox Configuration Support' is not checked.

* Quit Steam.

* Launch Steam.

* Switch on Xbox One S controller to connect via Bluetooth.

* Launch game.


You should now be able to use the controller in the game. Please let us know if this helps. 

## Donate

If this repo helps, feel free to donate!

[![Donate PayPal](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/donate/?business=QFJVE7A6LCP6U&no_recurring=0&item_name=Feral+Interactive+Mac+Controllers&currency_code=USD)

## If it still doesn't work

Previously, my Xbox One controller only worked wired. After fixing the bluetooth issue, the select button still didn't work. 

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

I also changed the string for the **CGPDeviceType** key to **Standard** instead of **Xbox** to stop the left stick drifting in Sleeping Dogs and GRID Autosport.

This also appears to be compatible with the other games tested.

```
<key>CGPDeviceType</key>
<string>Standard</string>
<key>ProductID</key>
<integer>2848</integer>
<key>ButtonBack</key>
<string>9:11</string>
```

If you still can't get it to work modify `XboxOneController.plist` with your controller's ProductID and just use the controller wired. This seems to be neccessary in some games with the Series Elite 2 controller.

You may need to disable steam input.
