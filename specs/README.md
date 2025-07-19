# Celestial MIDI Render
> Proudly made by [SolaricZuli]()!

### *Celestially Better than Aranara MIDI Render!*

# Celesial MIDI Renderer - MIDI Specifications

## (SUPERIOR) CelesMIDI Format
Main Structure

Structure is as follows:

[Data Type][Data Value/s]*
>*Variable Length Data Values are concluded with a separator, "|".

Data Type can be as follows:

>0 - 7: First digit of note pitch, which ranges from 00 to 7F.

>8 - A: Reserved, Unused

>B: Pitch Bend, Unused

>C: Control Change, for Visual, Audio, and some Technical Effects

>D: Program Change

>E: Tempo Change

>F: Track Header

>L: Lyrics Text

Data Values depend on the Data Type: Note: All values are in hexadecimal.

Note Events

>[Pitch - 2 chars][Velocity - 2 chars][Channel - 1 char][Tick - Variable][Separator][Length - Variable][Separator]

Program Change

>[Patch Value - 2 chars][Channel - 1 char][Tick - Variable][Separator]

Tempo Change

>[Microseconds per Beat - Variable][Separator][Tick - Variable][Separator]

Track Header

>[Track Value - Variable][Separator]

Control Change

>[Control Change Parameter - 2 chars][Control Change Value - 2 chars][Channel - 1 char]


## AraMIDI Format
Main Structure

Structure is as follows:

[Data Type][Data Value/s]*
>*Variable Length Data Values are concluded with a separator, "|".

Data Type can be as follows:

>0 - 7: First digit of note pitch, which ranges from 00 to 7F.

>8 - B: Reserved, Unused

>C: Control Change, Unused

>D: Program Change

>E: Tempo Change

>F: Track Header

Data Values depend on the Data Type: Note: All values are in hexadecimal.

Note Events

>[Pitch - 2 chars][Velocity - 2 chars][Channel - 1 char][Tick - Variable][Separator][Length - Variable][Separator]

Program Change

>[Patch Value - 2 chars][Channel - 1 char][Tick - Variable][Separator]

Tempo Change

>[Microseconds per Beat - Variable][Separator][Tick - Variable][Separator]

Track Header

>[Track Value - Variable][Separator]

# Navigation Portal
> [Main Menu](https://daniferous.github.io/CelestialMIDIRender/)

> [Render Now! - Release 1.3 Build 1](https://daniferous.github.io/CelestialMIDIRender/render/CMR%20Release%201.3.html)

> [View My Celestial Account](https://daniferous.github.io/CelestialMIDIRender/account)

> [Check out the Celestial Concourse for new deals!](https://daniferous.github.io/CelestialMIDIRender/concourse)

> [Read the Celestial MIDI Render - End User License Agreement](https://daniferous.github.io/CelestialMIDIRender/EULA/)

> [More about MIDI Specifications](https://daniferous.github.io/CelestialMIDIRender/specs/)