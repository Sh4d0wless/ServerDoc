What does ServerDoc do?
-ServerDoc will start a program and check the program is still running every five seconds (default) and restart the program if required (if its crashed or closed) on Win95/98/ME/200x/NT/XP & Linux systems. Windows NT users should read this note and WinXP users should read this note. Linux control requires serverdoc running on a windows machine.
-ServerDoc can also run different commands with its internal scheduling. You may want to run a game server between 6pm and 10pm or run different game servers hourly/daily/weekly or monthly. Serverdoc can even be set up to load a different mod/patch. You could have your servers set up to run Normal DeathMatch one night, Team Fortress the next, Counterstrike the night after.
-Serverdoc also has a remote interface to allow you (or clients) the ability to stop/start and change/edit the server command line. Remote clients can also be provided with access to edit files or only edit certian variables within a file.
-Serverdoc can monitor private and maxplayer settings of a number of game servers and restart them if a client as violated these settings.

A crashed server is no fun, and with serverdoc, it will be back up within seconds.

I have ServerDoc looking after my Quake 1, 2, 3 and Halflife Servers. (NOTE: I no longer run severs but continue work on serverdoc) You will need the VB6 runtimes if you dont already have them. :)

Basic Usage (not using SDcontrol, schedule or wwwconfig.cfg)
Serverdoc.exe [gameserver command line]
ie: C:\serverdoc\Serverdoc.exe f:quakeqwsv +maxplayers 16

Add your servers to your startup folder for automatic restarting of servers after power failure/reboot.

