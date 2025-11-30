This zip contains basic installation examples - 5 config folders for 5 servers. For more documentation please see the userguide and the text files in serverdoc zip. 

NOTE: Serverdoc pro will be required for the pro examples to operate correctly.
(save serverdoc.key in same folder as serverdoc.exe and sdcontrol.exe)

To load all serverdocs on windows start up add a shortcut in startup folder:
sdcontrol.exe /start


When you create new config folder(s) (for a new server) you can load the new serverdocs with 
sdcontrol.exe /start
This will not restart the ones already running.

The fastest way to add a serverdoc config for a new server is to copy a config folder into a new folder and just change the required parts (command line, and if using remote access port, user and pass). Now just run sdcontrol.exe /start to start your new server.

If you are using SD Pro you can start/stop enable/disable serverdoc via the sdcontrol program. More functions coming soon. Program is in very early days (free version will allow starts via sdcontol)
