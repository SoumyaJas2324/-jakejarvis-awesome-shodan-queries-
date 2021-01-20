### jakejarvis (awesome shodan queries)

>> https://github.com/jakejarvis/awesome-shodan-queries



Readme.md
***Awesome Shodan Search Queries Awesome

Over time, I've collected an assortment of interesting, funny, and depressing search queries to plug into Shodan, the (literal) internet search engine. Some return facepalm-inducing results, while others return serious and/or ancient vulnerabilities in the wild.


Most search filters require a Shodan account.

**You can assume these queries only return unsecured/open instances when possible. For your own legal benefit, do not attempt to login (even with default passwords) if they aren't! Narrow down results by adding filters like country:US or org:"Harvard University" or hostname:"nasa.gov" to the end.

**The world and its devices are quickly becoming more connected through the shiny new Internet of Things Sh*t — and exponentially more dangerous as a result. To that end, I hope this list spreads awareness (and, quite frankly, pant-wetting fear) rather than harm.

And as always, discover and disclose responsibly! nerd_face
**Table of Contents

    Industrial Control Systems
    Remote Desktop
    Network Infrastructure
    Network Attached Storage (NAS)
    Webcams
    Printers & Copiers
    Home Devices
    Random Stuff

***Industrial Control Systems
Samsung Electronic Billboards mag_right →

>> "Server: Prismview Player"

***Example: Electronic Billboards
Gas Station Pump Controllers mag_right →

>> "in-tank inventory" port:10001

***Example: Gas Station Pump Inventories
Automatic License Plate Readers mag_right →

>> P372 "ANPR enabled"

***Example: Automatic License Plate Reader
Traffic Light Controllers / Red Light Cameras mag_right →

>> mikrotik streetlight

***Voting Machines in the United States mag_right →

>> "voter system serial" country:US

***Telcos Running Cisco Lawful Intercept Wiretaps mag_right →

>> "Cisco IOS" "ADVIPSERVICESK9_LI-M"

***Wiretapping mechanism outlined by Cisco in RFC 3924:

    Lawful intercept is the lawfully authorized interception and monitoring of communications of an intercept subject. The term "intercept subject" [...] refers to the subscriber of a telecommunications service whose communications and/or intercept related information (IRI) has been lawfully authorized to be intercepted and delivered to some agency.

***Prison Pay Phones mag_right →

>> "[2J[H Encartele Confidential"

***Tesla PowerPack Charging Status mag_right →

>> http.title:"Tesla PowerPack System" http.component:"d3" -ga3ca4f2

**Example: Tesla PowerPack Charging Status
Electric Vehicle Chargers mag_right →

>> "Server: gSOAP/2.8" "Content-Length: 583"

***Maritime Satellites mag_right →

Shodan made a pretty sweet Ship Tracker that maps ship locations in real time, too!

>> "Cobham SATCOM" OR ("Sailor" "VSAT")

***Example: Maritime Satellites
Submarine Mission Control Dashboards mag_right →

>> title:"Slocum Fleet Mission Control"

***CAREL PlantVisor Refrigeration Units mag_right →

>> "Server: CarelDataServer" "200 Document follows"

***Example: CAREL PlantVisor Refrigeration Units
Nordex Wind Turbine Farms mag_right →

>> http.title:"Nordex Control" "Windows 2000 5.0 x86" "Jetty/3.1 (JSP 1.1; Servlet 2.2; java 1.6.0_14)"

***C4 Max Commercial Vehicle GPS Trackers mag_right →

>> "[1m[35mWelcome on console"

***Example: C4 Max Vehicle GPS
DICOM Medical X-Ray Machines mag_right →

>> Secured by default, thankfully, but these 1,700+ machines still have no business being on the internet.

>> "DICOM Server Response" port:104

***GaugeTech Electricity Meters mag_right →

>> "Server: EIG Embedded Web Server" "200 Document follows"

***Example: GaugeTech Electricity Meters
Siemens Industrial Automation mag_right →

>> "Siemens, SIMATIC" port:161

***Siemens HVAC Controllers mag_right →

>> "Server: Microsoft-WinCE" "Content-Length: 12581"

**Door / Lock Access Controllers mag_right →

>> "HID VertX" port:4070

**Railroad Management mag_right →

>> "log off" "select the appropriate"

***Remote Desktop
Unprotected VNC mag_right →

>> "authentication disabled" "RFB 003.008"

***Shodan Images is a great supplementary tool to browse screenshots, by the way! mag_right →

>> Example: Unprotected VNC
The first result right now. disappointed
***Windows RDP mag_right →

>> 99.99% are secured by a secondary Windows login screen.

>> "\x03\x00\x00\x0b\x06\xd0\x00\x00\x124\x00"

Network Infrastructure
Weave Scope Dashboards mag_right →

Command-line access inside Kubernetes pods and Docker containers, and real-time visualization/monitoring of the entire infrastructure.

title:"Weave Scope" http.favicon.hash:567176827

Example: Weave Scope Dashboards
MongoDB mag_right →

Older versions were insecure by default. Very scary.

"MongoDB Server Information" port:27017 -authentication

Example: MongoDB
Mongo Express Web GUI mag_right →

Like the infamous phpMyAdmin but for MongoDB.

"Set-Cookie: mongo-express=" "200 OK"

Example: Mongo Express GUI
Jenkins CI mag_right →

"X-Jenkins" "Set-Cookie: JSESSIONID" http.title:"Dashboard"

Example: Jenkins CI
Docker APIs mag_right →

"Docker Containers:" port:2375

Docker Private Registries mag_right →

"Docker-Distribution-Api-Version: registry" "200 OK" -gitlab

Pi-hole Open DNS Servers mag_right →

"dnsmasq-pi-hole" "Recursion: enabled"

Already Logged-In as root via Telnet mag_right →

"root@" port:23 -login -password -name -Session

Android Root Bridges mag_right →

A tangential result of Google's sloppy fractured update approach. roll_eyes More information here.

"Android Debug Bridge" "Device" port:5555

Lantronix Serial-to-Ethernet Adapter Leaking Telnet Passwords mag_right →

Lantronix password port:30718 -secured

Citrix Virtual Apps mag_right →

"Citrix Applications:" port:1604

Example: Citrix Virtual Apps
Cisco Smart Install mag_right →

Vulnerable (kind of "by design," but especially when exposed).

"smart install client active"

PBX IP Phone Gateways mag_right →

PBX "gateway console" -password port:23

Polycom Video Conferencing mag_right →

http.title:"- Polycom" "Server: lighttpd"

Telnet Configuration: mag_right →

"Polycom Command Shell" -failed port:23

Example: Polycom Video Conferencing
Bomgar Help Desk Portal mag_right →

"Server: Bomgar" "200 OK"

Intel Active Management CVE-2017-5689 mag_right →

"Intel(R) Active Management Technology" port:623,664,16992,16993,16994,16995

HP iLO 4 CVE-2017-12542 mag_right →

HP-ILO-4 !"HP-ILO-4/2.53" !"HP-ILO-4/2.54" !"HP-ILO-4/2.55" !"HP-ILO-4/2.60" !"HP-ILO-4/2.61" !"HP-ILO-4/2.62" !"HP-iLO-4/2.70" port:1900

Outlook Web Access:
Exchange 2007 mag_right →

"x-owa-version" "IE=EmulateIE7" "Server: Microsoft-IIS/7.0"

Example: OWA for Exchange 2007
Exchange 2010 mag_right →

"x-owa-version" "IE=EmulateIE7" http.favicon.hash:442749392

Example: OWA for Exchange 2010
Exchange 2013 / 2016 mag_right →

"X-AspNet-Version" http.title:"Outlook" -"x-owa-version"

Example: OWA for Exchange 2013/2016
Lync / Skype for Business mag_right →

"X-MS-Server-Fqdn"

Network Attached Storage (NAS)
SMB (Samba) File Shares mag_right →

Produces ~500,000 results...narrow down by adding "Documents" or "Videos", etc.

"Authentication: disabled" port:445

Specifically domain controllers: mag_right →

"Authentication: disabled" NETLOGON SYSVOL -unix port:445

Concerning default network shares of QuickBooks files: mag_right →

"Authentication: disabled" "Shared this folder to access QuickBooks files OverNetwork" -unix port:445

FTP Servers with Anonymous Login mag_right →

"220" "230 Login successful." port:21

Iomega / LenovoEMC NAS Drives mag_right →

"Set-Cookie: iomega=" -"manage/login.html" -http.title:"Log In"

Example: Iomega / LenovoEMC NAS Drives
Buffalo TeraStation NAS Drives mag_right →

Redirecting sencha port:9000

Example: Buffalo TeraStation NAS Drives
Logitech Media Servers mag_right →

"Server: Logitech Media Server" "200 OK"

Example: Logitech Media Servers
Plex Media Servers mag_right →

"X-Plex-Protocol" "200 OK" port:32400

Tautulli / PlexPy Dashboards mag_right →

"CherryPy/5.1.0" "/home"

Example: PlexPy / Tautulli Dashboards
Webcams

Example images not necessary. facepalm
Yawcams mag_right →

"Server: yawcam" "Mime-Type: text/html"

webcamXP/webcam7 mag_right →

("webcam 7" OR "webcamXP") http.component:"mootools" -401

Android IP Webcam Server mag_right →

"Server: IP Webcam Server" "200 OK"

Security DVRs mag_right →

html:"DVR_H264 ActiveX"

Printers & Copiers:
HP Printers mag_right →

"Serial Number:" "Built:" "Server: HP HTTP"

Example: HP Printers
Xerox Copiers/Printers mag_right →

ssl:"Xerox Generic Root"

Example: Xerox Copiers/Printers
Epson Printers mag_right →

"SERVER: EPSON_Linux UPnP" "200 OK"

"Server: EPSON-HTTP" "200 OK"

Example: Epson Printers
Canon Printers mag_right →

"Server: KS_HTTP" "200 OK"

"Server: CANON HTTP Server"

Example: Canon Printers
Home Devices
Yamaha Stereos mag_right →

"Server: AV_Receiver" "HTTP/1.1 406"

Example: Yamaha Stereos
Apple AirPlay Receivers mag_right →

Apple TVs, HomePods, etc.

"\x08_airplay" port:5353

Chromecasts / Smart TVs mag_right →

"Chromecast:" port:8008

Crestron Smart Home Controllers mag_right →

"Model: PYNG-HUB"

Random Stuff
OctoPrint 3D Printer Controllers mag_right →

title:"OctoPrint" -title:"Login" http.favicon.hash:1307375944

Example: OctoPrint 3D Printers
Etherium Miners mag_right →

"ETH - Total speed"

Example: Etherium Miners
Apache Directory Listings mag_right →

Substitute .pem with any extension or a filename like phpinfo.php.

http.title:"Index of /" http.html:".pem"

Misconfigured WordPress mag_right →

Exposed wp-config.php files containing database credentials.

http.html:"* The wp-config.php creation script uses this file"

Too Many Minecraft Servers mag_right →

"Minecraft Server" "protocol 340" port:25565

Literally Everything in North Korea north_korea mag_right →

net:175.45.176.0/22,210.52.109.0/24,77.94.35.0/24

TCP Quote of the Day mag_right →

Port 17 (RFC 865) has a bizarre history...

port:17 product:"Windows qotd"

Find a Job Doing This! woman_office_worker mag_right →

"X-Recruiting:"

If you've found any other juicy Shodan gems, whether it's a search query or a specific example, definitely drop a comment on the blog or open an issue/PR here on GitHub.

Bon voyage, fellow penetrators! wink
License

CC0

To the extent possible under law, Jake Jarvis has waived all copyright and related or neighboring rights to this work.

Mirrored from a blog post at https://jarv.is/notes/shodan-search-queries/.
