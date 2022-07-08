# Club Orion Audio Reactive Keyboard MIDI Control
This guide will show you how to set up your system to be able to control the audio reactive lights inside Club Orion with MIDI using a computer keyboard.

I have provided my preferred bindings and will continue to update it should I modify the bindings. They are centered around having a numpad and as such might not work on smaller keyboards, if you don't have a numpad you will probably need to adapt your own set of bindings. 

My preset is as follows:

* Light Animations 1-8 corresponding to the same number key on the numpad
* Flashers Hard Flash on forward slash (/), Random Flash on asterisk (*), Flashers Off on plus (+)
* Flasher speed on the "1-Modulation" control in VMPk
* Blinders Hard Strobe on minus (-)
* Blackout Toggle on backslash \
* Rainbow, Random Rainbow, and Color Chord on F2, F3, and F4 respectively
* Disco Ball Toggle on F7
* Fog Machine on F8

## IMPORTANT
The program that is used to generate the midi signals(VMPK) only registers keystrokes when its window is focused. If you have VRChat focused, it will not work. Thus, if you don't have a 2nd monitor, you might not be able to utilize this method.

## Requirements
* A keyboard
* LoopMIDI - https://www.tobias-erichsen.de/software/loopmidi.html - Virtual MIDI port to send signals from VMPK into VRChat
* VMPK - https://vmpk.sourceforge.io/ - Generates the MIDI signals from keyboard input

## Installation

1. Install LoopMIDI and VMPK
2. Open LoopMIDI and create a new port with a name so that you will know what it is
3. Add this to VRChat's launch options in Steam, replacing the placeholder with the name of the port you just created: `--midi={name}`
 - If you don't know how to do this, go to your Steam library and right click on VRChat, then click Properties. That should bring up a window that has a launch options box.

## VMPK Setup

1. Make sure LoopMIDI is running with the port you created unmuted.
2. Open VMPK and go to Edit -> MIDI Connections
    <p align="center">
    <img src="img/vmpk_s2.png">
    </p>
3. Set the "MIDI OUT Driver" to "Windows MM"
3. Set the "Output MIDI Connection" to the name of the LoopMIDI port you created. If it doesn't show on the dropdown, make sure LoopMIDI is running with the port unmuted.
4. Uncheck "Enable MIDI Thru on MIDI Output"
5. Click OK
    <p align="center">
    <img src="img/vmpk_s3.png">
    </p>
6. Go to Edit -> Keyboard Map
7. If you are using my provided config, download it from the repository then click the Open button and navigate to the XML and select it and hit OK. Otherwise, continue the steps below.
8. If you are making a custom binding set, assign all keys you intend to a number slot in VMPK. It doesn't have to be in any specific order or organization, but I did it in a sequential way for organization.
    - You can't use F1, that brings up the help page for VMPK, unless there is a way to change that which I haven't found yet.
    - There are 128 slots for keys, so you shouldn't need to worry about running out.
9. Once you have finished, click "Save As..." and save it somewhere so that you don't lose the bindings.
10. This is optional but I strongly recommend it: Go to File -> Save Configuration and save the current setup you have, sometimes stuff can be messed up if you don't load it every time you open.

## MIDI Binding in Club Orion

For a general overview of how AudioLink works in Club Orion watch this video by AcChosen, the creator of both VRSL and Club Orion.
https://www.youtube.com/watch?v=4l-vIRe8NlE

1. Go into VRChat and Club Orion, making sure you have LoopMIDI already running prior to launching and you have VMPK open.
2. In Club Orion, open the Audiolink lighting panel and click the "Enable MIDI" button.
3. If you are using my preset of numpad-based binds, then copy the following into your clipboard and paste it in the "Import to" field on the MIDI panel, then you are finished. I have also included them in a text file in the repository to save locally so you always have it on hand. If you aren't, continue to the steps below.
    `*|^3, &36$|^3, &37$|^3, &38$|^3, &39$|^3, &40$|^3, &41$|^3, &42$|^3, &43$|^3, &55$|^3, &49$|^3, &50$|^3, &51$|^3, &52$|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|^3, &48$|EXDEE|^3, &46$|EXDEE|^3, &45$|^3, &56$|^3, &47$|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|EXDEE|%EXDEE%^3, &1$%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%EXDEE%*`
4. Click something on the lighting panel, visual/sfx panel, or Audiolink panel. The last thing you pressed will appear on the MIDI panel under "Event To Record".
5. Click the "RECORD MIDI" button, then tab to VMPK and press the key on your keyboard you wish to bind to that function. Repeat for all functions you wish to bind.
6. To save your midi bindings, click the "Export (to String)" button and copy the text that appears in the box next to it to a text document and save it.

## Workflow after initial setup

1. Open LoopMIDI with your port unmuted
2. Open VMPK and load the .conf file which has your keyboard bindings already loaded
3. Open VRChat and go into Club Orion
4. Switch to Audiolink and open the MIDI panel, and import the saved string of your controls.

## Troubleshooting

- LoopMIDI must be launched before VRChat
- If VMPK is registering keystrokes but there is no change in game, check that the MIDI output connection in VMPK is correct
   - LoopMIDI also shows the current throughput of MIDI data through the virtual port, that can be checked to confirm if there is data going through. If there is data going through but still no reaction, then you might have a problem with your bindings, or you might have accidentally changed the "Channel" or "Base Octave" in VMPK.
- VMPK freezes randomly sometimes, I know no fix for this other than just force quitting using task manager and restarting VMPK, making sure to re-load the .conf file you should have saved.
- Be sure to load the .conf every time you start VMPK