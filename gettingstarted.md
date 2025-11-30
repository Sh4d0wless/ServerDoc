
<html>
<head>
    <title>Serverdoc - Restart crashed servers applications and programs</title>
</head>
<body>
<center><B><font size=+2>Serverdoc</font></B><BR>
<a href= "http://www.serverdoc.com/"><img src="https://www.serverdoc.com/images/sdimages/sd_selection.gif"></a><BR>
[<a href ="about.md">About</a>] [<a href ="gettingstarted.md">Getting Started</a>] [<a href ="userguide.md">Userguide</a>]<BR>
</center><BR>
<Table><TR><TD>
<B>NOTE:</B> For installation examples please download the installation examples in downloads section.<BR>
<BR>
<u>Getting started</u><br>
<B>Installing Serverdoc</B><BR>
<img src="https://www.serverdoc.com/images/sdimages/step01.gif" align="left">
Create a folder called serverdoc and unzip the latest zip into this folder.<BR>
If you have a pro or donation key also copy serverdoc.key to this folder.<BR>
</TD></TR><TR><TD>

<B>Setting up your first server:</B><BR>
<img src="images/sdimages/sd_install1.gif" align="left">
Run SDCONTROL.EXE and press "ADD"
</TD></TR><TR><TD>
<img src="images/sdimages/sd_install2.gif" align="left">
Enter the name of the configuration folder. Entering something meaningful here will help you manage your servers.<BR>
Click on "Create Folder"<BR>
</TD></TR><TR><TD>
<img src="https://www.serverdoc.com/images/sdimages/sd_install3.gif"><BR>
Now enter the command line you wish serverdoc to run.<BR>
<B>Recommended</B> - Copy your game server to a subfolder of the configuration folder called server (once copied press "refresh folders" to see the new folders).<BR>
Once your command line is complete press "save and exit"<BR>
You now see the server configuration you just created.<BR>
<img src="https://www.serverdoc.com/images/sdimages/sd_install4.gif"><BR>
<GR>
If you want remote web access now click on wwwconfig.cfg. Enter the required port, user values. Save and exit notepad.<BR>
<BR>
In Serverdoc Pro you can create your own web interface. It is strongly recommended you create a structure of templates using *SDINCLUDE=filename* so you only need to update one file to "update" all your interfaces.<BR>
<BR>
To start your server press "start"
You can issue commands to multiple servers by pressing "multi-select"<BR>
To start all your servers (ie at boot up) run "start all.bat".<BR>


<BR><BR><BR>

<U>Without SDControl.exe</U><BR>
Creating the config folder: Create a folder in c:\serverdoc, in this case we are using the clients name Gary Brown.
</TD></TR><TR><TD>
<img src="https://www.serverdoc.com/images/sdimages/step03.gif" align="left">
<B><I>optional</I></B> copy the game server to a subfolder in the config folder, we will create a folder called hl2. Doing this simplifies the path to the servers. (<B>.\hl2\srcds.exe</b> Vs <B>g:\servers\hl2server002\srcds.exe</b>)
</TD></TR><TR><TD>
In the config folder (gary_brown) Create a file called wwwconfig.cfg and enter the following:<BR>
<B>port 2081<BR>
user myname mypass<BR>
run .\hl2\srcds.exe -console +game cstrike +map de_dust<BR></B>
<BR>
Adjust the run line as required. If you have installed the server as a subfolder of the config folder you may use <B>.\</b>  if you have not be sure to enter the full path.<BR>
<BR>
Thats it, now double click start all.bat (or shortcut to sdcontrol.exe /start) to start the new serverdoc. Your server should now be running, if its not click "open" in serverdoc window to check the mini-log for the problem. The remote access url is http://<I>ipaddress</I>:2081 and user/password is per the wwwconfig.cfg settings.<BR>
<BR>
<B>Creating your second, third etc server:</b><BR>
<img src="https://www.serverdoc.com/images/sdimages/step04.gif" align="left">
Create a new config folder this time we will use "Tim Roberts" . Copy the wwwconfig.cfg from a current config folder in to the new config folder you just created. Edit port, user and run values in wwwconfig.cfg to suit. Save this file and click start all.bat (or shortcut to sdcontrol.exe /start) to start the new serverdoc and server.<BR>

</TD></TR></TABLE>


</body>
</html>
