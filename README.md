# Intro

OpenBeken simulator. Written in SDL and OpenGL, currently works on Windows, but should be easy to port.

OpenBeken simulator allows you to draw a simple sketch (simplified schematic) of an IoT device and run OpenBeken on Windows on that simulated device.
You can place buttons, LEDs, relays, trimmers, power metering chips, interact with them (press buttons etc) and check how OpenBeken would behave on such device.
This allows you to develop OpenBK configurations and scripts easily, even without getting a real device.

Features:
- load and save sketches (JSON format) along with a simulated BK7231 flash memory dump (bin format; contains config, LittleFS, etc)
- draw a circuit like you'd draw in Cadsoft Eagle
- place and use buttons (they are simulated on voltage levels, so all Click, Double Click, Hold Start, Hold Release etc OBK events are working)
- place relays/bulbs that you can control with buttons or OBK panel or scripts
- whole OBK HTTP panel works on windows (as a HTTP server on port 80), the Javascript Web App also works, you basically get OBK device on Windows
- MQTT is also working well, so you can pair your simulated machine with Home Assistant, experiment with HASS automation, test HA discovery
- place single color, CW (CCT), RGB and RGBCW strips and simulate their behaviour 
- use Tasmota Device Groups on Windows (fully functional, simulated OBK device can talk to real Tasmota/Beken devices on your network)
- send GET packets with SendGET command (fully functional, your Windows OBK sim can send HTTP GET to any server)
- and more....

# Basic usage

Run the simulator executable. An SDL Window will open with your device simplified sketch (WiFi module and some peripherals), also an OpenBeken HTTP server will run on port 80 on your local machine, so you can access your virtual OBK device by entering "localhost" or your local IP in the web browser. Note that you need to have port 80 not in use for that purpose, so stop services like Apache/Xampp, etc, before running OBK sim.

Now you can do two things:
- you can play around with Web interface, scripts, etc, just like on any other physical device
- you can change the simulated hardware in the Simulator window, add objects (relays, bulbs, LEDs, buttons), connect them with wires and script them anyway you want in Web panel, interact with buttons by clicking them

Your current scene can be easily saved and loaded, just make sure to save manually after making changes to device flash memory - by default, they are NOT saved. To manage virtual devices, use FILE menu:
- File->New (Empty) will create an empty  scene
- File->Load allows you to load an existing simulation (device schematic sketch + device flash dump with setting in flash)
- File->Save saves changes to current sketch
- File->Save As allows you to save current sketch to another file
- File->Open Recent provides a list of recently viewed sketches

Basic tools are available under the hotkeys on alphanumeric keyboards. 
- Key 1 is Use Tool, which allows you to press buttons, move sliders
- Key 2 is Move Tool, which allows you to move objects
- Key 3 is Wire Tool, which allows you to draw wires. Press LMB to draw, and press RMB to change draw mode
- Key 4 is Delete Tool, which allows you to delete objects, labels and wires
- Key 5 is Copy Tool, it can be used to quickly make a duplicate of clicked object
- Key 6 is Info Tool, it prints debug information about object under mouse cursor
- Key 7 is Text Tool, which allows you to print text on simulator sketch

# Command line arguments

OpenBeken simulator supports the following command line arguments:
- port - this allows you to change the HTTP port so multiple instances can run on single PC
- w and -h - this allows you to change the starting resolution of the window
- runUnitTests - this allows you to disable the long self test process that is at the startup of the simulator

Keep in mind that you need to prefix each argument with -, so to set port to 81 you should write: -port 81 , etc.
  
# Compiling

Get main repository here: 
https://github.com/openshwprojects/OpenBK7231T_App/tree/main
Next, assuming you have a path like W:\GIT\OpenBK7231T\apps\OpenBK7231T_App, copy content of simulator dir from this repo there, so you get paths like W:\GIT\OpenBK7231T\apps\OpenBK7231T_App\libs_for_simulator
Then open MSVC project (from the OpenBK7231T_App repo), select win build config



