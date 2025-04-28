## The Ultimate Quad Troubleshooting Procedure

This procedure is to guide you through troubleshooting your issue. Whether it be a receiver, VTX, ESC, Motor or any other issue, this procedure will guide you through the the stages you should be taking to try to solve it.
Proper troubleshooting procedure should always be based on stages starting at the _simplest_ and often the most overlooked through to the most _complex_ and often the stage which most people jump to immediately. **90%** of issues will be resolved at the first two simplest stages - rarely do they require a complex solution - so it is important that you take the time initially to start at the simplest stage to potentially save time in the long run if you jump to the more complex stages.

**Stage 1: _Check your physical build_**
---
Most issues arise from these checks not being carried out thoroughly. You think you've soldered a wire to the correct pad but you haven't actually checked that it is correct. Go back and check it and double check it to make sure. Compare it to the wiring diagrams or installation instructions and fix it if you find it is wrong. Some examples are:
**Power issues:**
    - something not powering up properly
    - no lights turning on
    - no start up motor tones
**Signal issues:**
    - controller stick movements not registering on the quad
    - vtx not displaying OSD or changing channels correctly
    - motor not turning or ESC not beeping on startup

**_Things to check:_**
**Power issues:**
    - check that you're providing the correct voltage to the device (i.e. 9V vs 5V etc)
    - check that the solder joint or plug is not loose
    - check with a multimeter that you are receiving voltage at your device

**Signal Issues:**
    - check that your Rx and Tx are connected to the correct pads (i.e. Tx (talk) on device goes to Rx (listen) on FC and vice versa)
    - check that the solder joint or plug is not loose
    - check that you are connecting to the intended UART (also part of Step 2)
    - if there is a plug with a lot of wires connected, check they are in the correct order between FC and device (e.g. ESC cable)

If you would like to have your install sanity checked, many people would be more than happy to help as long as there are clear photos and information on FC model and make as well as any other information which would help them check your stuff for you.

Remember - this might be annoying because you have finished putting everything together and you need to pull it apart to check these things, but you should ask yourself if you would rather spend a few minutes undoing screws and moving things out of the way to check these simple things and have a solution at the end of the day or spend hours trying to solve a complex issue which doesn't end in a solution until you pull it apart and check your build, only to see that it was a simple install issue all along and you've wasted hours trying other things.

**Stage 2: _Check your FC config_**
---
Once you have checked over your wiring and general installation and the issue has not been resolved, this is the time to connect your FC to your computer and use your configurator of choice (Betaflight, INAV etc). This is the stage where you check that the configuration of the FC matches what you have connected to it, whether this is:
- checking that you've got the correct settings on the correct UART in your ports tab
- checking that the correct receiver protocol is selected in the receiver tab
- checking that your ESC protocol matches your ESC (i.e. DSHOT or bidirectional DSHOT etc) in the motors tab

A few common issues to look out for:
- the UART that the device is soldered is not matched in the PORTS tab of Betaflight (or INAV)
    - check your FC silkscreen or wiring diagram to check which UART the device is soldered to and then change it in the PORTS tab and make sure to save and reboot (otherwise the settings will not be saved)
    - for receivers you need to change the "Serial Rx" slider
    - for VTX you need to change the "Peripherals" drop down (for analogue VTX make sure to check whether Tramp or Smartaudio is correct)
    - for GPS and ESC change the "Sensor Input" drop down
- your receiver is powered, but you don't see any sliders moving in the RECEIVER tab but you've confirmed that the port is correct
    - make sure that you've selected "Serial (via UART)" as your receiver mode and the Serial Receiver Provider matches your receiver protocol (i.e. CRSF for ELRS, Tracer or Crossfire, SBUS for Frsky, SPEKTRUM1024/2048/SRXL etc for a spektrum reciever. Most likely it will be CRSF)
    - if this is set correctly, then it is more than likely to do with a radio setting, whether it be model match on your ELRS Lua script or your radio models have not been set up correctly to output the correct channels
- your GPS is not working or you can't see the GPS tab in Betaflight/INAV
    - under the CONFIGURATION tab, scroll down to the Other Features section and make sure the toggle button next to "GPS" is on, which should make the GPS tab show up
    - in the GPS tab make sure the Protocol is set to "UBLOX" (the most common protocol) and take your quad outside if possible to check for GPS satellite fixes (rarely GPS will work inside). If you aren't on a laptop, use telemetry on your radio to confirm whether your GPS is receiving satellites 
- your motors are not operating when testing them in the motors tab (**with no props on of course!!**)
    - 

**Stage 3: _Check your Device versions_**
---
At this point of troubleshooting it is hard to provide generic advice because often the issue you are having is device specific. A few common devices will be addressed here but it is highly advisable to get in contact with someone to ask for advice.

This would be the first stage at which you may need to flash firmware to anything. Often, if there are issues with devices not working after you've been through the previous troubleshooting stages, it is something to do with the firmware of the device (note that it is almost never an issue with the FC firmware unless there is a lack of a certain feature that the device requires of the FC which is only fixed by a newer FC firmware version). Devices such as ELRS receivers, Walksnail VTXs and DJI VTXs often need to have matching firmware to the transmitter or goggles to work properly and so this is what should be checked.

For a detailed procedure for flashing firmware to ELRS devices, there is great information found here: https://www.expresslrs.org/
For a detailed procedure for flashing firmware to Walksnail devices, there is great information found here: https://walksnail.wiki/ and https://oscarliang.com/setup-avatar-fpv-system/
For a detailed procedure for flashing firmware to Walksnail devices, there is great information found here: https://oscarliang.com/dji-fpv-system-update-firmware/

**Stage 4: _Still having an issue after all these steps?_**
---
At this point if the issue has not been resolved in the preceeding stages, it is a very specific issue to whatever device you are using and you should be contacting anyone knowledgable in the specific device for help. When contacting them, describe the process you have followed and what checks you have performed, with photos also if they ask, as this will help them help you get the resolution you are after. 

Often there are discord servers dedicated to the specific devices with people that have specific knowledge about that device who may be able to narrow down the issue and help resolve it with you or suggest tests to perform that will help them diagnose the issue. Always keep in mind that they are often not being paid to help and they are doing you a favour so should be communicated with in a respectful manner.
