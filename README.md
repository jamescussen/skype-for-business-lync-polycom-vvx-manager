Skype for Business / Lync Polycom VVX Manager
=============================================

            
Skype for Business / Lync Polycom VVX Manager is a Powershell based GUI tool that can be used to manage and control Polycom VVX phones.

**[](http://www.myskypelab.com/2015/10/skype-for-business-lync-polycom-vvx.html)**


![Image](https://github.com/jamescussen/skype-for-business-lync-polycom-vvx-manager/raw/master/vvxphonemanager3_sm.png)


**Note: This tool requires that the Polycom VVX phones have specific configuration settings deployed in them. For more details on these settings please visit: [http://www.myskypelab.com/2015/10/skype-for-business-lync-polycom-vvx.html](http://www.myskypelab.com/2015/10/skype-for-business-lync-polycom-vvx.html)**


 


**Features:**


**Phone discovery** – Phones can be discovered either by automatically querying the Lync/Skype for Business Monitoring database (provided there is a monitoring role deployed in the environment) by pressing the “Discover from
 Monitoring DB” button. Alternatively, this can be done by entering IP Address ranges and “pinging” contiguous subnet ranges for phones using the “Discover from IP Range” button (format: '192.168.0.1-192.168.0.20' OR '192.168.0.0/24'
 OR add multiple with comma separation '192.168.0.0/24,192.168.1.0/24'). During the discovery process, phones that are logged in to user accounts will be listed in the users list. If the tool finds a VVX handset that is not signed in, it will be added to the
 user list under the name “VVXNot@LoggedIn_<index number>”. This allows you to use the tool to access these devices even though they are not signed into the system.


**Export/Import Phone Info** – This feature outputs a CSV file that contains all the Users, IPs, Firmware Version, Serial Numbers, Lync/Skype for Business Server, and MAC Address (if available) for all phones. If you select the 'More'
 checkbox you will also get the additional Lync/Skype for Business policy settings for each user (this is slower).


**Access Web Interface** - Access the web interface of a VVX phone by selecting a user in the user list and clicking the “Web Config” button. This will automatically load the web browser to the phone's web interface.


**Pin control** – The “Pin…” button will load a dialog that will Set, Test, Lock, Unlock a user’s PIN number.


**Send Text Messages** - Send text messages to be displayed on a Polycom VVX phone. An example of this would be to send a message to warn before a system upgrade or a reboot. Messages are displayed on the screen for 30 seconds. (Special
 configuration is required in the VVXs for this feature. See the blog post for more information)


**Get More Info** – By pressing the “More Info” button you can get extended information about a VVX phone including: Device Info, Call Status, Presence Info, Network Info, Line Info, SIP Status, Network Statistics.


**Reboot/Restart Phones** – You have the choice of Rebooting or Restarting a single, multiple, or All phones.


**Reset Config** – You have the option to Reset the Config or Factory Reset the configuration with one or many phones.


**Get/Set Config** - You can Get or Set any setting in the phone configuration. You simply need to enter the configuration setting name (as you would find in the configuration file eg. log.level.change.hset) and click the Get or Set buttons
 to view or change the setting's value.


**Dial / End Call** – You can choose to remotely dial a SIP URI (eg. john.smith@domain.com or[+61395551111@domain.com](mailto:+61395551111@domain.com)) on a phone by entering a URI and pressing the “Dial” button.
 If the phone is on a call you can also choose to end the call using the “End Call” button.


**Test FTP Config Server **- Test your FTP Configuration File server by simply entering the IP address of the FTP server and pressing the “Test FTP” button. The tool will attempt to connect to the FTP server and download information
 about key files associated with a Polycom configuration server deployment. These include the base configuration file (000000000000.cfg), configuration files in the CONFIG_FILES tag, any MAC address files associated directly with phones, and firmware files
 (*.sip.ld). The tool will give feedback as to the state of the FTP server.


**View Screen** – The “Screen…” button will open a dialog that will show you the user's screen. Before the user's screen can be viewed the user must first manually allow access to the Screen Capture feature (this
 is a security measure so that the user is aware that someone is viewing their screen). This setting within the Basic->Preferences screen will only be made available while the VVX screen dialog is displayed (the tool automatically makes the setting 'up.screenCapture.enabled'
 in the device to turn on this preference setting). At this point the user will have to enable the following setting in their phone preferences: **Settings -> Basic -> Preferences -> Screen Capture -> Enabled**


**Command Line Settings** – If you would like to load the script with your own specific settings to save time, you can specify these in the command line when loading the script. (See the blog post for more details)


**Settings Dialog** – The “Settings…” button allows you to configure your own passwords, web service port and HTTPS settings for the tool.


 


**UPDATES
2.01 Enhancements**


  *  Fixed issue with the Get Config function 
  *  Increased the timeout for discovery ping from 200ms to 350ms to handle sites that might be over a higher latency connection. Also added a setting called 'Discovery Wait Time' which allows you to tune the time that the tool will wait for responses from discovery
 messages sent to phones (setting between 200ms-1000ms). 

**2.02 Enhancements**


  *  Fixed issue with rescan on CSV import. 
  *  Included new Polycom MAC Address range 64:16:7F 
  *  Added a discovery summary at the end of IP Based discovery. This gives a useful summary when scanning multiple IP ranges.

  *  The command line input for IPRangeInput now accepts muiltple ranges in comma separated format. eg. Skype4B-Lync-PolycomVVXManager2.02.ps1 -IPRangeInput '192.168.0.1-192.168.0.200,192.168.0.10/24'


**2.03 Bug Fix**


  *  There was an issue with detecting users when capital 'SIP:' was used as part of their SIP URI. This has been fixed.


**2.04 Bug Fix**


  *  Fixed a couple of typos that affected operation on Powershell 5 
  *  Added more VVX types when discovering logged out phones 

**2.05 Bug Fix**


  *  Added port number to screen viewing URL. Required when non-standard HTTP/HTTPS port is used.


**2.10 Fixes and Enhancement! (28/7/2017)**


  *  Replaced Invoke-RestMethods with shiny new .net web requests to fix annoying connection issues found in previous versions.

  *  Added option in Send Message dialog to select the theme/style of the message displayed on the VVX. Default is to send the new SfB dialog style, the original Polycom theme and red/alarm themes are also available.

  *  Updated Icon to new MySkypeLab icon. 
  *  Added some more detail in blog post about Push configuration. 

**2.20 More Fixes and Enhancements! (28/8/2017)**


  *  Fixed threading issue with discovery that could result in some devices not being listed.

  *  Added support for RealPresence Trios.- Added support for VVXs and Trios configured as CsMeetingRoom devices.

  *  Added Trio Filter checkbox to view only users with Trios. 
  *  When not logged in Trio is discovered it will be displayed as 'TrioNot@LoggedIn'.

  *  Fixed discovery Instance name when default SQL instance is used. 
  *  Changed the 'VVXNot@LoggedIn_<value>' name to end with the IP Address of the device rather than an incrementing number.

  *  Fixed the IP Address discovery count text in powershell window to make more sense

  *  Fixed issue with listview scrolling and colored lines changing back to black. Clicking on the listview will refresh the colours.

  *  Increased VVX and Trio list checkbox filter speed. 
  *  Fixed issues with setting and testing pins. 

**2.21 Bug Fixes (8/11/2017)**


  *  Fixed issue with config Get and Set not working with https connections 
  *  Fixed issue with LineURI and DialPlan not being outputted in CSV for Common Area Phones and Meeting Room devices


**2.50 Fixes and 5.7 API Enhancements (24/1/2018)**


**Note: The config setting httpd.ta.enabled='1' is required for the 5.7 features to work correctly**


 


  *  Added Touch Simulation (Tap/Swipe) when viewing screen on 5.7 software. This works on the range of VVX500, VVX600, VVX400, VVX300 and VVX200 devices (yes, even non-touch screen devices). Simply click on the screen where you would like to send a tap or click
 and drag to send a swipe command. Note: There is no support for hardware button presses (eg. the home button) in the API yet so we will have to wait for full remote control of devices.

  *  Viewing the screen now does not require user involvement to turn on Screen Capture within the phone preferences in version 5.7. This will automatically be set by the tool each time the screen button is clicked.

  *  Added additional information when the “More” button is clicked for devices with 5.7 and above (CPU, Memory, Session Information, Additional Call Status info).

  *  Added Sign in / Sign Out functions (in send command dropdown box) allowing AD Authentication and PIN Authentication - Supported on 5.7 and above. Not supported for Trios.

  *  Bulk PIN Authentication Sign In. See the Bulk PIN Authentication section of the blog post for more details - Supported on 5.4 and above. Not supported for Trios.

  *  Corrected issue with VVX Manager failing with virtual IPs from HyperV (Thanks to Ross Gernon for the feedback)

  *  Added a retry when polling devices during discovery. Some VVXs don't respond to the first NOTIFY message so a second is sent to try and force a response.

  *  Fixed issue when connecting to default MSSQLSERVER instances. 
  *  Many other smaller bug fixes 

**3.00 Bug Fixes - Added Skype for Business Online support (25/08/2018)**


  *  The VVX Phone Manager can now list up users from Skype for Business Online and discover their VVX devices using the Network IP Discovery method (supports users with VVXs/Trios and CAP Devices).

  *  The 'Connect SfBO' button will connect the PowerShell session to SfB Online. You will need to enter your Office 365 username and password to connect. Once connected a green 'Online' label will be displayed next to the button and the button’s text
 will change to 'Disconnect SfBO' which you can click to disconnect from SfB Online.

  *  Two new command line attributes added for SfB Online Username and Password so you can connect without being prompted for credentials (example: .\Skype4B-Lync-PolycomVVXManager3.00.ps1 -OnlineUsernameInput john.smith@tenant.onmicrosoft.com -OnlinePasswordInput
 'Password') 
  *  Cleaned up the info display and changed font and added some colour. Now includes information about where a user is Homed (OnPrem or Online) and Hosted VM (HostedVoicemailPolicy) fields.

  *  Added support for testing HTTP/HTTPS config servers (Test Server Button). Files are now downloaded into memory so no file has to be written to disk and checks for VVX250,350,450 firmware. Trio firmware and APP_FILE_PATH_Trio8800 path now supported.

  *  Rewrote user information gathering code to be cleaner and work with SfB Online.

  *  Removed exit button from messages sent to VVX400 
  *  Many other bug fixes :) 

**3.01 Trio discovery and fix update (25/10/2018)**


  *  Trios in later versions do not support NOTIFY based discovery anymore. Added automatic REST based fall back for discovery of these devices.

  *  If REST is disabled on a Trio that falls back to REST discovery, a device named TrioRestDisabled@<IP Address> will be added to the list and you can then use the 'Web Config' button to enable REST (Settings > Applications > REST API > Enable).

  *  When Visual+ is discovered it will be added to the list as TrioVisualPlus@<IP Address> and you will be able to access the web interface with the 'Web Config' button.

  *  Fixed Trio screen display size by halving the size to fit on regular screen resolutions.

  *  Made updates to the Import CSV logic to properly handle Trios. 

**3.02 O365 Connection Optimisations (6/2/2019)**


  *  Improvements with reconnecting to O365 after connection timeout. (Thanks to Greig Sheridan for helping with the testing of this release)


**3.03 MFA Support added for O365 (6/3/2019)**


  *  Added MFA support when signing into O365. 

 


**For all information on of operation of this tool please visit this link:** 


[http://www.myteamslab.com/2015/10/skype-for-business-lync-polycom-vvx.html](http://www.myskypelab.com/2015/10/skype-for-business-lync-polycom-vvx.html)


 






        
    
