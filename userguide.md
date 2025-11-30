
<html>
<head>
    Serverdoc - Restart crashed servers applications and programs<BR><BR>
</head>
<body>
<center><B><font size=+2>Serverdoc</font></B><BR><BR>
<a href= "http://www.serverdoc.com/"><img src="https://www.serverdoc.com/images/sdimages/sd_selection.gif"></a><BR><BR>
[<a href ="about.md">About</a>] [<a href ="gettingstarted.md">Getting Started</a>] [<a href ="userguide.md">Userguide</a>]<BR><BR>
</center><BR><BR>
<a href="#startup"><u>Serverdoc Startup</u></a> - read this and things will be easier :)<br>
<br><a href="#Installing">
<u>Installing &amp; Running Serverdoc</u></a><br><br>
<a href="#bconfig"><u>Configuration</u></a><br>
<a href="#Schedule"><u>Schedule</u></a><br>
<a href="#RemoteAccess"><u>Remote Access</u></a><br>
<a href="#Templates"><u>Templates</u></a><br>
<a href="#CommandSelection"><u>Command Selection</u></a><br>
<a href="#Editcmd"><u>Command Line Remote Edit</u></a><br>
<a href="#Editfile"><u>Remote File Editing</u></a><br>
<a href="#Tricks"><u>Misc Tricks</u></a><br>
<a href="#Updating"><u>Updating</u></a><br>
<br><big><big><span style="font-weight: bold;"><a name="startup"></a>
Serverdoc startup process</span></big></big>, understand what goes on and setup is a lot easier. <br>
<span style="font-weight: bold; font-style: italic;">Current directory</span>
(config folder) is the folder you run serverdoc from, i.e. the "start in" option in
windows shortcuts or the directory you are in when you execute
serverdoc.exe from ms-dos prompt.<br>
<br>
When you execute serverdoc it:-<br>
Checks the <span style="font-weight: bold;">same directory</span> serverdoc.exe is in for your <span style="font-weight: bold;">serverdoc.key</span> file (free/donation or pro mode)<br>
Reads <span style="font-weight: bold;">wwwconfig.cfg</span> file in <span style="font-weight: bold;">current directory</span> and starts web server for remote control if required.<br>
Loads schedule (<span style="font-weight: bold;">schedule.txt</span> - in <span style="font-weight: bold;">current directory</span>) if it exist.<br>
Loads serverdoc config file, <span style="font-weight: bold;">serverdoc.cfg</span> from current directory.<br>
Sets any command line configuration options (i.e. /L1 /P1&nbsp; - see serverdoc.txt)<br>
If no command line was entered, wwwrotate.dat (current directory) does
not exist and schedule is empty then displays pop-up box with command line info.<br>
If no command line was given, serverdoc checks for a command  on the "run" line in wwwconfig then checks schedule.txt for the last command that should be running
and executes that command. NOTE: a schedule event of <B>99 99 99 99 99 <i>c:\folder\program.exe</i></B> will be loaded on serverdoc startup<br>
Starts the application specified in command line (or wwwconfig.cfg or schedule.txt) in low priority then will swtch to the configured setting<br>
The server is now running, serverdoc will restart servers if they close
and attempt to detect any crash windows and close them for you, then restart the server.<br>
When serverdoc it used the run line from wwwconfig.cfg any changes to command line will be saved to the "run" line in wwwconfig.cfg
<BR>
<br><big><big><span style="font-weight: bold;"><a name="Installing"></a>
Installing &amp; Running Serverdoc</span></big></big><BR>I recommend you download and unzip the installation 
example file in the downloads section<br>Simply unzip serverdoc into the directory of your choice (we will use
c:\serverdoc). The first time serverdoc runs it will create
<span style="font-weight: bold;">serverdoc.cfg</span> in the <span style="font-weight: bold;">current directory</span>
if serverdoc.cfg does not exist. 

To start serverdoc you can use sdcontrol.exe (found in installation examples) or create shortcuts. If you crate shortcuts you will
need a shortcut for each instance of serverdoc you wish to run. If you are using sdcontrol.exe you will only need the one shortcut
(<B>sdcontrol.exe /START</b>)to start all the serverdocs.<BR>
To create a shortcut to serverdoc, right click on desktop and browse to c:\serverdoc\serverdoc.exe
and press ok/finish so you now have a shortcut on your desktop. Now right click no the short cut and select
properties, here you can enter the command you want serverdoc to start
(lets say its c:\program\myserver.exe):<br>
<span style="font-weight: bold;">TARGET:</span> c:\serverdoc\serverdoc.exe c:\program\myserver.exe<br>
and what directory to load the config files from:<br>
<span style="font-weight: bold;">START IN:</span> c:\serverdoc<br>
we will leave this as c:\serverdoc for now but if you want to run
multiple serverdocs with different configs (and you <span style="font-weight: bold;">will need to</span> if you
are using remote access) you need to change this "<span style="font-weight: bold;">start in</span>"
directory to another directory for each copy serverdoc you plan to run
(ie c:\serverdoc\scfg0032\ ) and save the config files (i.e.
config.cfg,
wwwconfig.cfg, etc.) in that directory or install a full serverdoc to a
new directory ( maybe c:\serverdoc02\ ). I recommend you use sub
directories to hold the config files for multiple servers that way you
have the one serverdoc.exe/serverdoc.key to update. Having multiple
installations of serverdoc will take longer to upgrade as you will have
to update each serverdoc.exe when the time comes.<br>
<br>
Now double click on your new shortcut and your serverdoc should load up
and start your program. To start this automatically when your computer
boots copy the short cut to the start - programs - startup folder.<br><br><big><big><span style="font-weight: bold;"><a name="bconfig"></a>
Basic Serverdoc Configuration</span></big></big><br>
<img src="http://www.serverdoc.com/images/sdimages/serverdoc_config.gif" title="" alt="">
<br>
<b>Start Serverdoc minimized</b> - will start serverdoc minimized
(yes this stuff is complex heheh)
<br>
<b>Start Server minimized </b>- may not work with all programs as some
programs Maximize themself.
<br>
<b>Write Logfile</b> - will write restarts etc to serverdoc.log
<br>
<b>Server Priority</b> - Setting this to real-time may lock your system.
<br>
<b>Disable Extra Checking</b> - Tick if Serverdoc keeps on incorrectly detecting a crashed server.
<br>
<b>Disable Query Checking</b> - Disable restarts when server does not respond to network queries. You must have port/ip values set in command line if not using default.
<br>
<b>Allow public servers</b> - if not ticked servers will be restarted if the password for the server is removed (if supported with that server)
<br>
<b>Allow max x clients</b> - If set to a value > 0 the server will be restarted if the max players on server is set higher then this value. Command line options for game server override this value.
<br>
<b>Cpu Affinity</b> - Select what CPU's the program serverdoc starts will use.
<br>
<b>Force restart of program every x mins</b> - Will restart program
every x mins, simple :)
<br>
<b>Restart Delay</b> - Delay when restarting a crashed server.
<br>
<b>Check Server every</b> - How often server is checked to see if its alive.<br>

<b>SMTP Server</b> - The mail server to be used for sending email.<br>

<b>Send mail to:</b> - Email address to send crash reports to.<br>
<br><big><big><span style="font-weight: bold;"><a name="Schedule"></a>
Schedule</span></big></big><br>
Schedule.txt is to be saved in the same directory as serverdoc.cfg, this is the "start in" directory.<br>
All commands in schedule.txt
are to be in the below format<br>

<b>Min Hour Dayofweek Dayofmonth Month Command</b><br>
<b></b>
<p>Where:
<br>&nbsp;Min = 0 - 59, the Minute
<br>&nbsp;Hour = 0 - 23, 0 being midnight and 23 being 11pm
<br>&nbsp;Dayofweek = 1 - 7, 1 being Sunday, 2 Monday - 7 Saturday
<br>&nbsp;Dayofmonth = 1 - 31, depending on how many days are in current
month
<br>&nbsp;Month = 1 - 12, 1 being Jan, 12 is Dec.
<br>&nbsp;Command = Command to run, ie C:\Games\quakeserver.exe +map fun
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
= STOP - stop current program and dont start another.
<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
= START - Starts program that was last ran. <br>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; = restartoff - Do not restart servers if they crash<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp; = restarton - Turn server restarting back on<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp; = sdcmdstart - Issue start command to another serverdoc<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp; = sdcmdstop - Issue stop command to anothert serverdoc<br>
<br>
</p>
<p>&nbsp;* = any, always true.
</p>
<p>Examples:<BR>
<b>99 99 99 99 99 c:\windows\notepad</b><BR>
This is a special event, this event will be ran on serverdoc startup but no other time.<BR><BR>

<b>98 98 98 98 98 c:\windows\notepad</b><BR>
This is a "crash" event, will be ran when a application crashes or ends.<BR><BR>

<B>98 98 98 00 x</B> 
This event is run when server starts<BR>
<B>98 98 98 01 x</B> even is run when server stops<BR>
This event is run when server stops or crashes.
x is a number 0 - 99)<BR>
example: I have two serverdocs running and my config folders are c:\serverdoc\master\ and c:\serverdoc\slave\
If I wanted start the slave serverdoc when master one starts its server I would create the following file - c:\serverdoc\master\schedule.txt
98 98 98 00 00 sdcmdstart c:\serverdoc\slave\
98 98 98 01 00 sdcmdstop c:\serverdoc\slave\

If I wanted the slave serverdoc to stop when the master starts and start when the master stops I would use
(in c:\serverdoc\master\schedule.txt)
98 98 98 00 00 sdcmdstop c:\serverdoc\slave\
98 98 98 01 00 sdcmdstart c:\serverdoc\slave\ 


<br>This will start c:\windows\notepad at 50mins past every hour and stop
at 55mins past.
<br><b>50 * * * * c:\windows\notepad</b>
<br><b>55 * * * * stop</b></p>
&nbsp;-s will save current command that's running, run the new command then<br>

&nbsp;revert to the saved command once the new command finishes/crashes.<br>

<span style="font-weight: bold;">12 * * * * -s:update.exe</span><br>
<br>
This will run a Half Life server on Monday &amp; Tuesday, TFC on Wed,
Thurs and Friday and Counterstrike on the weekend and run update.exe at
1am every day then load up the server that was running once update.exe
stops.<b><br>
00 00 2 * * * c:\halfli~1\hlds -console</b>
<b><br>
00 00 4 * * * c:\halfli~1\hlds -console -game tfc</b>
<span style="font-weight: bold;"><br>
00 00 7 * * * c:\halfli~1\hlds -console -game cstrike<br style="font-weight: bold;">
00 01 * * * * -s:update.exe</span><br>
<p>

<br>
</p>
<p>This will rotate every monday between Half-Life, TFC and Counterstrike.
<br>rotate.dat contains:
<br><b>c:\halfli~1\hlds -console</b>
<br><b>c:\halfli~1\hlds -console -game tfc</b>
<br><b>c:\halfli~1\hlds -console -game cstrike</b>
<br>and schedule.txt contains
<br><b>00 00 2 * * * -r:rotate.dat</b>
<br>to rotate every day at 6am you would use
<br><b>00 06 * * * * -r:rotate.dat</b>
<br></p><big><big><span style="font-weight: bold;"><a name="RemoteAccess"></a>
Remote Access</span></big></big><br>
Remote access is set up via the <span style="font-weight: bold;">wwwconfig.cfg</span> file, saved in the "start in" folder.<br> 
You can also access this file via the serverdoc menu by clicking on menu - config - remote access.<BR>
this will contain the port and user/password/access levels. If you are
running Serverdoc Pro you can also select the IP address to bind to<br>
example wwwconfig.cfg<br>
---cut---<br>
port 82<br>
ip 203.33.238.2<br>
user myfriend mypass<br>
user admin neverguess 2041 0<br>
---cut---<br>
Serverdoc will listen on port 82 on ip address 203.33.238.2 (only Pro verision supports IP selection)  and create two accounts. One with only<br>
stop/start functions (myfriend) and one with full config access. Leave the<br>
second value 0 for now.<br><BR>
Other optional settings are:<BR>
<B>user AllFromThisHost www.mygames.com</B><BR>
<B>user AllFromThisHost 203.33.22.34</B><BR>
Allows clients from www.mygames.com to connect without user/password prompt. Like auth disable but only for a single ip.<BR>
NOTE: AllFromThisHost IS CASE SENSITIVE.<BR>
<B>auth MyHosting co</B><BR>
auth displays the string when entering user/pass for remote control. (pro version)<BR>
<B>systray Client #0330</B><BR>
systray will show the string on the taskbar icon, "Client #0330" in this case.<BR>
<B>auth disable</B><BR>
will no longer prompt for password<BR>
<B>fileedit keyword c:\folder\filename</B><BR>
Allow remote access to this file, see the remote file editing section.<BR>
<B>BF2SERVERSETTINGSFILE c:\myfolder\filename.con</B><BR>
Location and filename of BF2 server settings file to use (used if your not using BF2 dedicated server)



<BR>

Normally you will use 0 0 or nothing for access level but if you do want to offer
config changes you need to add up the values of each item you want
access to, type this<br>
number in after the username and password.<br>
1 Start Serverdoc minimized<br>
2 Start Server minimized<br>
4 Write Log file<br>
8 Disable Extra Checking (server is running but serverdoc keeps restarting it)<br>
16 Server Prority (I wouldn't let anyone have this!)<br>
32 Force restart of program every XX mins (0 to disable)<br>
64 Restart Delay XX Seconds (0 to disable)<br>
128 Check server is running every XX Seconds<br>
256 SMTP Server: XXXX (Leave blank = disable)<br>
512 Send email to: XXXX<br>
1024 Save Setting (serverdoc.cfg)<br>
<br>
so, for an example, we want joe to be able to change log file and save<br>
settings, 4+1024=1028. So we would use....<br>
<br>
joe letmein 1028 0<br>
<br>
easy :) Normally access level of 0 0 or nothing will be used.<br>
<br>
<big><big><span style="font-weight: bold;"><a name="Templates"></a>Templates</span></big></big><br>
You can make the serverdoc remote interface page look how you want my modifying the <span style="font-weight: bold;">template.html</span>
file, this is saved in the configuration folder or main folder (with serverdoc.exe). Just add images, edit
colours/text and change the layout like you would a normal html file.<br>
The special keywords you can use are:<br>
<big><span style="font-weight: bold;">Keywords</span></big> (replaced with values)<br>
<span style="font-weight: bold;">*SDFULLCOMMAND*</span> - Current path &amp; command line<br>
<span style="font-weight: bold;">*SDCOMMAND*</span>&nbsp; - Current command line<br>
<span style="font-weight: bold;">*FRIENDLYSDCOMMAND*</span> - Friendly command running from wwwrotate.dat<br>
<span style="font-weight: bold;">*SDDATE*</span> - Date<br>
<span style="font-weight: bold;">*SDTIME*</span> - Time<br>
<span style="font-weight: bold;">*SDIP*</span> - IP address serverdoc is using from wwwconfig.cfg IP line
<span style="font-weight: bold;">*SDVERSION*</span> - Serverdoc version<br>
<span style="font-weight: bold;">*SDCFGSDMIN*</span> - Start Serverdoc Minimized checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGSVRMIN*</span> - Start Server Minimized checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGLOGFILE*</span> - Write Logfile checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGPLOW*</span> - Prority Low checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGPNORMAL*</span> - Prority Normal checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGPHIGH*</span> - Prority High checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGPREALTIME*</span> - Priority Realtime checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGDISABLEEC*</span> - Disable Exta Checking checkbox checked?<br>
<span style="font-weight: bold;">*SDCFGFORCERESTART*</span> - Force Restart value (mins)<br>
<span style="font-weight: bold;">*SDCFGRESTARTDELAY*</span> - Restart Delay value (seconds)<br>
<span style="font-weight: bold;">*SDCFGCHECKSERVER*</span> - Check Server Every x Seconds value<br>
<span style="font-weight: bold;">*SDCFGSMTPSERVER*</span> - SMTP Server value<br>
<span style="font-weight: bold;">*SDCFGEMAILADDRESS*</span> - Email Address value<br>
<span style="font-weight: bold;">*SDROTATEDROPBOX*</span>&nbsp; - Display selection of commands from wwwrotate.dat<br>
<span style="font-weight: bold;">*SDROTATEDROPBOXSHORT*</span> - as above but do not display path names<br>
<span style="font-weight: bold;">*SDROTATEDROPBOXFRIENDLY*</span> - displays &lt;friendly name&gt;, see wwwrotate_example.txt<br>
<span style="font-weight: bold;">*SDUSERNAME*</span> - Username of remote user<BR>
<span style="font-weight: bold;">*SDUSERPASS*</span> - Password of remote user (useful if creating a ftp hyperlink with same user/pass)<BR>
<span style="font-weight: bold;">*SDCONFIGNAME*</span> - Folder name of serverdoc config<BR>

<br>
<big><span style="font-weight: bold;">Conditions</span></big><br>
Adding -R- after &lt;SD (ie &lt;SD-R-SECFL) = must NOT<br>
<span style="font-weight: bold;">&lt;SDSECFL<span style="font-style: italic;">x</span>&gt;</span>boo<span style="font-weight: bold;">&lt;/SD&gt;</span> - Must have first access level x to include boo in html<br>
<span style="font-weight: bold;">&lt;SDSECSLx&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - Must have second access level x<br>
<span style="font-weight: bold;">&lt;SDSERVERRUNNING&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - Server must be running<br>
<span style="font-weight: bold;">&lt;SD-R-SERVERRUNNING&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - Server must NOT be running<br>
<span style="font-weight: bold;">&lt;SDUPDATERUNNING&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - hldsupdatetool.exe is running<br>
<span style="font-weight: bold;">&lt;SD-R-UPDATERUNNING&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - hldsupdatetool.exe is NOT running<br>
<span style="font-weight: bold;">&lt;SD_APP_SERVER.EXE&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span> - server.exe is program in commandine (replace "server.exe" as required)<BR>
<span style="font-weight: bold;">&lt;SDUSERNAME=Admin&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span>  - only user Admin<BR>
<span style="font-weight: bold;">&lt;SDUSERIP=www.myhost.com&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span>  - only connections from this ip/host <BR>
<span style="font-weight: bold;">&lt;SDACCEPTINGCONNECTIONS&gt;</span>insert your code here<span style="font-weight: bold;">&lt;/SD&gt;</span>  - query checks <BR>

For example if you wanted a big red light graphic to be displayed when
the server is not running and a green one when it is running you would
have something like:<br>
&lt;SDSERVERRUNNING&gt;&lt;img
src="http://mywebserver/greenlight.gif"&gt;&lt;/SD&gt;&lt;SD-R-SERVERRUNNING&gt;&lt;img
src="http://mywebserver/redlight.gif"&gt;&lt;/SD&gt;<br>
<br>
To display the "start" link only when server is not running and display "stop" link when server is running:<br>
&lt;SDSERVERRUNNING&gt;&lt;font size=+2&gt;Start &lt;a href="/stop"&gt;Stop&lt;/a&gt;&lt;/SD&gt;<br>
&lt;SD-R-SERVERRUNNING&gt;&lt;font size=+2&gt;&lt;a href="/start"&gt;Start&lt;/a&gt; Stop&lt;/SD&gt;<br>
<br>
<big><big><span style="font-weight: bold;"><a name="CommandSelection"></a>Command Selection</span></big></big><br>
The <span style="font-weight: bold;">wwwrotate.dat</span> file contains a list of commands to be made available via the remote interface. A simple <span style="font-weight: bold;">wwwrotate.dat</span> file offering two selections would look something like this<br>
<span style="font-style: italic;">c:\hlserver\hlds.exe -console -game cstrike +map cs_mapname</span><br style="font-style: italic;">
<span style="font-style: italic;">c:\hlserver\hlds.exe -console -game dod +map dod_mapname</span><br>
<br>
If you have <span style="font-weight: bold;">serverdoc pro</span> you
can also have friendly names, this means instead of the command line
being displayed to the remote client the friendly name you display will
be shown. <span style="font-weight: bold;">wwwrotate.dat</span> would look something like this:<br>
<span style="font-style: italic;">&lt;Counter Strike&gt;c:\hlserver\hlds.exe -console -game cstrike +map cs_mapname</span><br style="font-style: italic;">
<span style="font-style: italic;">&lt;Day of Defeat&gt;&lt;c:\hlserver\hlds.exe -console -game dod +map dod_mapname</span><br>
<br>
"Counter Strike" and "Day of Defeat" will be displayed as options in
the drop down command selection box. To show the drop down command
selection box use the keyword <span style="font-weight: bold;">*SDROTATEDROPBOXFRIENDLY*</span> in your template file.<br>
<br>
Example remote interface screen using friendly names<br>
<img src="http://www.serverdoc.com/images/sdimages/friendlynames.gif" title="" alt="" style="width: 188px; height: 213px;"><br>
<br>
<big><big><span style="font-weight: bold;"><a name="Editcmd"></a>Remote Command Line Edit<br>
</span></big></big>
To allow remote editing of a command line you need two things - Special
keywords in command line and keywords in the template.html file.
Serverdoc needs to know what parts of the command line are to be
edited so we need to add <span style="font-weight: bold;">*SD</span><span
 style="font-style: italic;">keyword</span><span
 style="font-weight: bold;">*</span> to the command line where the
edited value(s) will be placed.<br>

For example, if we where running <span style="font-weight: bold;">C:\server\hlds.exe
-console -game dod</span> and we wanted to be able to change <span
 style="font-weight: bold;">dod</span> to other values we would use <span
 style="font-weight: bold;">C:\server\hlds.exe -console -game
*SDgametype=dod*</span>. The <span style="font-weight: bold;">=dod</span>
assigns the default value of DOD to <span style="font-weight: bold;">*SDgametype*</span>,
serverdoc will run the command <span style="font-weight: bold;">C:\server\hlds.exe
-console -game dod</span>. If you did not want to assign a default
value we would just use <span style="font-weight: bold;">*SDgametype*</span>.

<br>
<br>
Now to allow changing the value remotely we need a form in
template.html, something like.<br>
<pre id="line1"><span style="font-weight: bold;">&lt;FORM ACTION="/CHANGE" METHOD="GET"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">Game &lt;INPUT TYPE=text SIZE="10" NAME="*SDgametype*" value="*SDVgametype*"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;input type="submit" value="Change Command line"&gt;&lt;/form&gt;</span><br
 style="font-weight: bold;"><br></pre>
When "change command line" button is pressed, the browser will submit
the value to <span style="font-weight: bold;">*SDgametype*</span>,
Serverdoc will update the command line with this new value. You may
notice the <span style="font-weight: bold;">value="*SDVgametype*"</span>.
The <span style="font-weight: bold;">*SDV</span><span
 style="font-style: italic;">keyword</span><span
 style="font-weight: bold;">*</span> is replaced with the current value
of that keyword, its important you always set default form values to
the current command line values. <br>

<br>
The following example will show a drop down selection box instead of a
text edit box, offering two options without having to manually type the
value in.<br>
<pre id="line1"><span style="font-weight: bold;">&lt;FORM ACTION="/CHANGE" METHOD="GET"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">Game &lt;SELECT NAME = "*SDgametype*"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;OPTION VALUE = "*SDVgametype*"&gt;*SDVgametype*</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;OPTION VALUE = "Cstrike"&gt;HL - Counter Strike</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;OPTION VALUE = "DOD"&gt;HL - Day of defeat&lt;/SELECT&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;input type="submit" value="Change Command line"&gt;&lt;/form&gt;<br></span><span
 style="font-weight: bold;"><br></span></pre>
<span style="font-weight: bold;">NOTE: you can NOT have spaces in
submitted values. This is for security reasons.</span> If you wish to allow spaces use *SDCOMMANDLINE* - this will allow spaces<br>

<big><span style="font-family: monospace; font-weight: bold;"><br>
</span></big>Some example command lines are:<br>
<span style="font-weight: bold;">c:\server\ucc.exe server
*SDcl=DM-Curse4?game=XGame.xCTFGame?mutator=XGame.MutQuadJump*
ini=UT2004.ini Multihome=67.19.224.190 log=server.log</span><br>
(you can remotely edit <span style="font-weight: bold;">DM-Curse4?game=XGame.xCTFGame?mutator=XGame.MutQuadJump</span>)<br>
<span style="font-weight: bold;">c:\server\hlds.exe -console +game
*SD2=cstrike* +map *SD1="de_dust"*<br>
</span>(you can remotely edit cstrike and de_dust values)<br>
<big><span style="font-family: monospace; font-weight: bold;"><br>
</span>
<a name="Tricks">
<span style="font-weight: bold;">Tricks</span></big><br>
<a href="#TricksSaveCmd"><u>Saving Command line</u></a><br>
<a href="#TricksRestoreCmd"><u>Restore Edited Cmd Line</u></a><br>
<a href="#TricksSameMap"><u>Retart on same map</u></a><br>



<a name="TricksSaveCmd"></a>
<span style="font-weight: bold;">Saving command line</span><br>
You can save the current command line so next time you start serverdoc
(after reboot) it will load the saved command. Load serverdoc with the<span
 style="font-weight: bold;"> /SC LOAD</span> option (ie <span
 style="font-weight: bold;">Serverdoc.exe /SC LOAD</span>) and add the
line <span style="font-weight: bold;">RUN <span
 style="font-style: italic;">command line</span></span> to the
wwwconfig.cfg file<span style="font-weight: bold;"><span
 style="font-style: italic;"> </span></span>(replace
"command line" with the program + options you wish to run) ie your
wwwconfig.cfg may look like:<br>
<span style="font-weight: bold;">port 4547<br>
user me mypassword 0 0<br>

RUN c:\server\hlds.exe +game *SD2=Cstrike* -map *SD1=de_dust*<br>
<br><a name="TricksRestoreCmd"></A>
"Restore" edited command line.<br>
</span>You easy make a button to "restore" the command line to its
original settings. If our default command line was <span
 style="font-weight: bold;">C:\server\hlds.exe -console -game
*SDgametype=dod* </span>but DOD had been changed to something else,
maybe a invalid value was entered. you can have a Restore (or "rescue
me") button to restore default value(s).<br>
<pre id="line1"><span style="font-weight: bold;">&lt;FORM ACTION="/CHANGE" METHOD="GET"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;INPUT TYPE=hidden NAME="*SDgametype*" value="DOD"&gt;</span><br
 style="font-weight: bold;"><span style="font-weight: bold;">&lt;input type="submit" value="Restore Command line"&gt;&lt;/form&gt;</span><br
 style="font-weight: bold;"></pre>
<br>
<a name="TricksSameMap"></a>
<B>Restart on same map</B><BR>
By using the *sdautomap* keyword - restart game server on the map that was being played.<br>
Serverdoc can now restart the server on the map that was being played. Example - if your command line is<br>
c:\server\hlds.exe -console +map datacore<br>
change it to:<br>
c:\server\hlds.exe -console +map *sdautomap=datacore*<br>
The sdautomap value will be updated with current map being played. Ensure query checks are enabled in serverdoc config.<br>
<br>
<br>
<br>
<br>
<big><big><span style="font-weight: bold;"><a name="Editfile"></a>Remote File Editing<br>
</span></big></big>
You can allow access to whole files or just variables in files. First you need to configure the files you wish to edit. This is done in wwwconfg.cfg by entering<BR>
editfile <i>keyword filename</i><BR>
you can also edit a single variable , say hostname in server.cfg<BR>
editfile <i>keyword c:\server.cfg ? hostname</i><BR>
<BR>
For Example, If I wished to allow access to mapcycle.txt file and only the hostname variable in server.cfg I would enter something like:<BR>
<B>editfile myfile .\valve\mapcycle.txt<BR>
editfile myhostname .\valve\server.cfg ? hostname</B><BR>
<BR>
Now in your template to change the hostname we need to add<BR>
<B>&lt;FORM ACTION="/CHANGE" METHOD="POST"&gt;<BR>
&lt;BR&gt;Hostname&lt;INPUT TYPE=text SIZE="25" NAME="*SDFE-myhostname*" value="*SDFEV-myhostname*"&gt;<BR>
&lt;input type="Submit" value ="Save" &gt;&lt;/form&gt;</B><BR>
<BR>
see the *SDFEV- and *SDFE- ? The SDFEV stands for "Serverdoc File Edit Value", this is the contents of the file or variable. SDFE is the file you are saving to.
In this HTML we are displaying the hostname (*SDFEV-myhostname*) value in server.cfg and submitting a text value to *SDFE-myhostname* (saved to hostname variable in server.cfg). myhostname was set in wwwconfig.cfg to 
<B>\valve\server.cfg ? hostname</B>
<BR><BR>
This HTML will display and save the contents of myfile (mapcycle.txt)<BR>
<B>&lt;FORM ACTION="/CHANGE" METHOD="POST"&gt;<BR>
&lt;textarea name="*SDFE-myfile*" rows="10" cols="20" tabindex="1"&gt;*SDFEV-myfile*&lt;/textarea&gt;&lt;BR&gt;<BR>
&lt;input type="Submit" value ="Save Map List" &gt;&lt;/form&gt;</B><BR>
This time its the whole file being edited, this is set in wwwconfig.cfg via editfile 
<br>
<br>
<br>
<br>


<big><big><span style="font-weight: bold;"><a name="Updating"></a>Updating Serverdoc<br>
</span></big></big>Updating serverdoc is normally as simple as
replacing the serverdoc.exe and/or serverdoc.key file with the new
version. I email people on my <a href="http://www.serverdoc.com/modules.php?name=Subscribe">mailing list</a>
as new versions come out. Also subscribe to the "latest serverdoc.exe" thread in message forums for info 
on the very latest serverdoc.exe (sub releases - this info is not sent via mailing list).
If you are running a number of servers it is recommended you use the
single serverdoc.exe and have sub directories under the serverdoc
directory to hold the configuration files. You only have to update the one file
(serverdoc.exe / serverdoc.key), this will make life easier :). Also future features
will be built on this system.
<br><BR>
<b>V0.85B and later -</B> 
Save serverdoc.exe as serverdoc.bin and select update in a serverdoc window. This will
update serverdoc without closing your servers. Serverdoc should exit, update and resume monitoring 
of the server.<BR><BR>

<B>PRE V0.85b -</B>
If you have one copy of serverdoc running from each serverdoc.exe (ie
if you have two serverdocs running you have 2 copies of serverdoc.exe
on HDD) its possible to update without closing your server. Save the
new serverdoc.exe as "server.bin" in the serverdoc directory and select
update from the serverdoc menu. <br>
<br>
<B>PRE V0.85b -</B>If you have the single serverdoc.exe running many copies of serverdoc
you will have to close all the serverdoc's to update the .exe, while
you have to close serverdoc you only have to replace the single
serverdoc.exe (and single serverdoc.key file) if you have many servers
each with there own serverdoc.exe it will take more time to update.<br>
<br>
<br>


</body>
</html>
