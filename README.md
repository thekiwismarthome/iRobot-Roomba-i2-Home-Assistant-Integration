# Home Assistant iRobot Integration for Roomba i2
iRobot Roomba i2 Home Assistant Integration

 ![image](https://github.com/user-attachments/assets/00687266-913b-4268-be24-dcef96fbf4ba)
 
Get Roomba BLID & PW the easy way (using Windows)

I know there are other ways but I use windows on a day to day basis, haven’t switched everything to Linux yet and this was pretty easy to do.  Here is the official [HA page](https://www.home-assistant.io/integrations/roomba/)

But for my reference and the rest of you, here ya go…
First let us fetch the stuff we need. This is two files in total. Create a temporary folder on your desktop for extra convenience (you can name the folder whatever you want) and put these two files inside that folder:

Python installation package. I recommend getting the latest “executable installer”. You can find this in the ‘Download’ section of the official Python website https://www.python.org

Roomba Python Library. This is a zip-package of files normally used to establish integration with your Roomba (you can find it at https://github.com/NickWaterton/Roomba980-Python). Look for a green button marked “Clone or download”, Click it and select “Download zip”.

You should now have these two files (one exe file and one zip file) in a folder on your desktop.

Start Python installation by running the exe-file.
Select “Customise installation”. Click “Next”. 
On the “Advanced options” page be sure to check “Add Python to environment variables” and 
edit “Customise install location” to “C:/Python”, then click “Install”.
Please keep the Python installation file in your desktop folder for now.

Open the Roomba zip-file and locate the “roomba” folder inside. Copy this folder into your freshly installed Python folder (C:/Python).

Open a Command prompt.  Then navigate to your C:/Python directory using the “cd \python” command.

Once inside the Python folder, type “pip install six” and press ENTER. Now this package called “six” should begin to install. After a few second you should be back in the command prompt.

For those that really want to know, I am soo glad I googled it now…. 😉

The Python "six" package is a library designed to help developers write code that is compatible with both Python 2 and Python 3 by providing utility functions to bridge the differences between the two versions, allowing you to maintain a single codebase that works across both Python environments without major modifications

Type “python .\roomba\getpassword.py <LOGIN> <PASSWORD>”, hit ENTER and wait a few seconds. Now your Roomba should be detected by the script. From here on you should follow on-screen directions.
Make sure your Roomba is turned on and parked in the base, and then holding the “Home” button for most devices… apparently… However, for the i2 and S9 I believe you need to press the 2 buttons on either side of the Start button (Home and the Spot Clean) for a few seconds to hear a bleep or not, can’t remember the bleep it was 1am. 

![image](https://github.com/user-attachments/assets/db8e7f2b-a32e-433c-9380-803ec0eac126)

This should cause the Wi-Fi indicator on your Romba to flash - then hit ENTER in the command prompt to continue and wait a few seconds more.




It should show something like this…

```
c:\python>python .\roomba\getpassword.py
2024-11-22 20:02:53 INFO [Roomba.Password] Using Password version 2.1
2024-11-22 20:02:53 INFO [Roomba.Password] reading/writing info from config file ./config.ini
2024-11-22 20:02:53 INFO [Roomba.Password] waiting on port: 5678 for data
2024-11-22 20:02:54 INFO [Roomba.Password] Robot at IP: 192.168.0.58 Data: {
  "ver": "3",
  "hostname": "Roomba-*********CANT_SHOW_YOU_THIS********",
  "robotname": "Roomba",
  "robotid": "*********CANT_SHOW_YOU_THIS********",
  "ip": "192.168.0.58",
  "mac": "50:14:79:AA:BE:6E",
  "sw": "daredevil+2.6.0+daredevil-release+163",
  "sku": "i215800",
  "nc": 0,
  "proto": "mqtt",
  "cap": {
    "binFullDetect": 2,
    "addOnHw": 1,
    "oMode": 2,
    "dockComm": 1,
    "edge": 0,
    "maps": 2,
    "pmaps": null,
    "mc": null,
    "tLine": 2,
    "area": 1,
    "eco": 1,
    "multiPass": 3,
    "team": 1,
    "pp": 0,
    "lang": 2,
    "5ghz": 0,
    "prov": 3,
    "sched": 1,
    "svcConf": 1,
    "ota": 2,
    "log": 2,
    "langOta": 2
  }
}
2024-11-22 20:03:04 INFO [Roomba.Password] 0 robot(s) already defined in file./config.ini, found 1 robot(s) on network
2024-11-22 20:03:04 INFO [Roomba.Password] To add/update Your robot details,make sure your robot (Roomba) at IP 192.168.0.58 is on the Home Base and powered on (green lights on). Then press and hold the HOME button on your robot until it plays a series of tones (about 2 seconds). Release the button and your robot will flash WIFI light.
Press <Enter> to continue...
s<Enter> to skip configuring this robot:
2024-11-22 20:03:44 INFO [Roomba.Password] Roomba (Roomba) IP address is: 192.168.0.58
2024-11-22 20:03:45 DEBUG [Roomba.Password] Connection Successful
2024-11-22 20:03:45 DEBUG [Roomba.Password] Waiting for data
2024-11-22 20:03:45 INFO [Roomba.Password] blid is: *********CANT_SHOW_YOU_THIS********
2024-11-22 20:03:45 INFO [Roomba.Password] Password=> :1: *********CANT_SHOW_YOU_THIS******** <= Yes, all this string.
2024-11-22 20:03:45 INFO [Roomba.Password] Use these credentials in roomba.py
2024-11-22 20:03:45 INFO [Roomba.Password] Configuration saved to ./config.ini
```

Now go to your Home Assistant > Settings > Devices & services | Integrations
It should pick it up straight away without any help  but just in case, click “+ Add Integration”, search Roomba

 ![image](https://github.com/user-attachments/assets/c0f59c7a-726b-42f1-b6ea-059dbc09d8bd)


It should then find your Roomba, if not then add it manually by typing in the Host IP
 
![image](https://github.com/user-attachments/assets/b39b0aa7-caf1-4e1e-9250-9cab09ea3ed3)


It will ask you for your password, use the one we got earlier, copy everything between the => and <=, except the blank spaces 😊

It should … just work form there.
One thing I did notice, it took a short while for the vacuum enti9ty to become available to add into a card, a bit frustrating at 1am, thinking I was going doolally.



