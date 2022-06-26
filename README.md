# Install alt:V and SaltyChat under Linux

### Requirements

 - Grand Theft Auto account
 - Lutris installed
 - Wine installed
 - Winetricks installed
 - Optional: ProtonUp-Qt

## Grand Theft Auto Installation

 1. Download `Grand Theft Auto` from Lutris (https://lutris.net/games/grand-theft-auto-v/). I'm using the install script with the Rockstar Launcher in this guide.
 2. Install as mentioned in the Lutris script.
 3. Download the newest `wine-ge` version. ProtonUp-Qt is the easiest way to get it (`lutris-GE-Proton7-16-x86_64` at the time of writing).
 4. Select it as the wine version in Lutris.
 
## alt:V Installation
 1. Download the latest `alt:V client` (https://altv.mp/#/downloads).
 2. Move it into your prefix. I put mine inside `$WINEPREFIX/drive_c/ProgramData/altv/altv.exe`.
 3. Press configure and select the `altv.exe` as the executable.
 4. Start it and press "No" to install it in the same folder. It will crash after launching GTA5.
 5. Open a terminal and navigate to `$WINEPREFIX/path_to_altv/cef`.
 6. Create symlinks for the following files. You can copy and paste the whole block.
  ```Bash
ln -s ../libs/chrome_elf.dll . &&
ln -s ../libs/icudtl.dat . && 
ln -s ../libs/libcef.dll . && 
ln -s ../libs/snapshot_blob.bin . && 
ln -s ../libs/v8_context_snapshot.bin .
```
7. Now you can launch it again and the server browser should work.

## TeamSpeak 3 and SaltyChat Installation
1. Download the `32-bit Teamspeak 3 Client` (https://www.teamspeak.com/en/downloads/).
2. Create a new prefix in Lutris.
3. Select wine as the starter.
4. In the game settings choose a path for your prefix (preferably in your Lutris folder) and select 32-Bit architecture.
5. Select the TeamSpeak installation file as the executable (you don't have to move it anywhere, just keep it inside your downloads folder).
6. Under starter options select latest `lutris-fshack` as the wine version (`lutris-fshack-7.2-x86_64` at the time of writing). 
7. Also disable DXVK. This will prevent the SaltyChat window from being just a black screen.
8. Press save and launch it. Install TeamSpeak as usual. Don't launch it after the installation.
9. Click on "Wine-Configuration" and select `Windows 10` as the windows version. Press "OK".
10. Go back to the configuration.
11. Select the TeamSpeak executable instead of the installer as your executable. It's most likely `$WINEPREFIX/drive_c/Program Files/TeamSpeak 3 Client/ts3client_win32.exe`.
12. Download the latest SaltyChat plugin (https://gaming.v10networks.com/SaltyChat).
13. Open the plugin with an archive manager and copy (and merge) the plugins folder into the `TS3Client` directory. It should be `$WINEPREFIX/drive_c/users/$USER/AppData/Roaming/TS3Client/` if you did not change it.
14. Open a terminal and install `dotnet461` with winetricks.
```Bash
WINEPREFIX="put_path_here" winetricks -q dotnet461
```
15. Download ``Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019`` (https://aka.ms/vs/16/release/vc_redist.x86.exe)
16. Execute it inside the prefix. Can be done directly in Lutris with the "Launch EXE inside Wine-Prefix" option.
17. TeamSpeak should now have the SaltyChat plugin installed.
18. Set the theme to `windows` inside TeamSpeak so buttons are visible.
