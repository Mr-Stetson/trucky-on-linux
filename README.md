# How to install Trucky for ETS2 or ATS on Linux
This is my first guide so if you have any suggestions for improvements let me know.
I installed Overwolf and Trucky for both games prefixes separately but you could use symlink to make both games use the same prefix.
## tl:dr for advanced users
You need dotnet35, dotnet48, vcrun2022, install Overwolf with [Overwolf Setup installer](https://content.overwolf.com/downloads/setup/latest/regular.html) and install Trucky from Overwolf store.
## Setup
1. Download and install [SteamTinkerLaunch (STL)](https://github.com/sonic2kk/steamtinkerlaunch) (I use [ProtonUp-Qt](https://github.com/DavidoTek/ProtonUp-Qt) to handle STL and custom Proton versions)
2. Set the game to run STL as compatibility layer
	- Right-click the game from library -> Properties -> Compatibility -> Check the box and select STL
3. Run the game and go to **STL Main Menu**. You have 2 seconds to press the button before the game launches, if you miss it just close the game and try again.
4. From STL click "**Game Menu**"
	- Under "**Proton Settings**" set "**Proton version**" to what proton version you want to use.
	- Untick "**Use Steam Linux Runtime**"
	- Click "**Save**" and "**Main Menu**"
1. From STL select "**Winetricks**" to install the necessary Windows libraries
	- "**Winetricks category**": dll
	- Click "**Select**" - a new window opens
	- Tick "**dotnet35**" , "**dotnet48**" and "**vcrun2022**" and click "**Select**" - the window closes
	- Click "**Install**" and wait for a notification for winetricks installation has finished (5-10 minutes depending on PC)
	- After it has finished check "**Winetricks**" again and check that all pakcages under "**Currently Selected Packages**" has "**(already installed)**" suffix
		- If they don't check [Troubleshooting](https://github.com/Mr-Stetson/trucky-on-linux#if-winetricks-doesnt-install-packages)
2. Download [Overwolf Setup installer](https://content.overwolf.com/downloads/setup/latest/regular.html). The normal installer doesn't work.
3. From STL select "**One time run**"
	- "**One time command**": Browse to `OverwolfSetup.exe`
	- Click "**Run command**" and go through the installation
4. From STL select "**Game files**" - here you can see the "**WINEPREFIX**" path
5. From STL select "**One time run**" again
	- "**One time command**": Browse to "**WINEPREFIX**" path and further `drive_c/"Program Files (x86)"/Overwolf/OverwolfLauncher.exe`
	- Click "**Run Command**" and install Trucky from Overwolf store (**DON'T LAUNCH THE GAME** from Trucky installation last step, just close the window with "x")
	- Launch Trucky from Overwolf and login and set your settings how you like them
	- Close Trucky and Overwolf
6. From STL click "**Game Menu**"
	- Under "**Misc Options**":
		- Tick "**Use custom command**"
		- "**Custom command**": Browse to "**WINEPREFIX**" path and further `drive_c/"Program Files (x86)"/Overwolf/OverwolfLauncher.exe`
		- Tick "**Fork custom command**"
		- "**Wait for custom command**": Set to at least 1, I set to 10 so Overwolf launches fully before the game launches
	- Click "**Save**" and "**Main Menu**"
7. From STL click "**Exit**"
	- If Steam says the game is still running after couple seconds Overwolf is hanging and you can just click Stop from Steam
8. Launch the game and start logging some jobs!

## Troubleshooting
### If Winetricks doesn't install packages
I just deleted the `drive_c` of the WINEPREFIX of the game and it worked after. If you have played the game with Proton before your settings are in the prefix, back them up:
- From STL select "**Game files**"
- Tick "**WINEPREFIX**" and click "**Select**"
- Browse to `drive_c/users/steamuser/Documents` and backup the game folder (ETS2 or ATS)
- Go back to delete `drive_c` folder
- Try Winetricks again
### Overwolf doesn't launch anymore
If Overwolf updates it doesn't launch anymore and you need to download [Overwolf Setup installer](https://content.overwolf.com/downloads/setup/latest/regular.html) again and use the **STL One time run** to install the update manually. This doesn't affect Trucky installation so once you update Overwolf manually you should be good to go.
