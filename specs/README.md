```
You are currently visiting https://www.solariczuli.com/specs.html.
```

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

## Technical Effects (Beta)
```
Upcoming Additions for MIDI Makers:

By Release 26.1 or maybe even in Release 1.3, after relying heavily on a modification of a MIDI Parsing Tool, said modification has released support for MIDI CC, however, it is for a different format and relies on utilising the MIDI Synth installed on the user's computer. Currently, the technology used to play MIDI Synth on the "Aranara MIDI Render" is currently classified, which is not fair as it is a pioneering feat of technology that should be shared for all!

In light of this, we the Celestial Team spearheaded by SolaricZuli, have decided to try and make a modification to include support for certain MIDI CC. Starting at the time and date of implementation, our modified MIDI Parsing Tool and as well as the original modification, can be used to convert MIDIs into playable Celestial MIDI Render songs. 

As such, we will unveil a new format: the CelesMIDI format. It is an extension to the existing araMIDI files and can be loaded even if the importer requests for araMIDI files - by simply dropping the CelesMIDI file onto the import window. The only key difference is that araMIDI files do not contain the support for MIDI CC while CelesMIDI does.

Now, the original creator of the AraMIDI file did not include MIDI CC Support as the effects on Audio (non-MIDI Synth) are minimal and feared that it would put a large impact on audio performance. Which is why we have decided to prove that creator wrong and put at least some of the audio effects included!

For now, the MIDI CC will only impact visually. However, we plan to add support for Attack, Release, and Hold MIDI CC in the future. So, stay tuned!

Pitch Bend Support will be to a new header... following the "Faelei MIDI Format" which recently its structure became open for public viewing. This approach is to ensure that even that format can be opened on this far more superior renderer!

MIDI CC Visual Effects
CC	Range	Description
20	00	Reset Background Color to Set Color, Remove Overlay (set opacity to 00), Reset Falling Speed - Implemented
21	00~7F	Amount of Red on the Background to Set - Implemented
22	00~7F	Amount of Green on the Background to Set - Implemented
23	00~7F	Amount of Blue on the Background to Set - Implemented
24	00~7F	Set Falling Speed (Significant Digits) Requires CC 25 to proceed after otherwise skipped.
25	00~7F	Set Falling Speed (Exponent: 40 is 0, 7F is 63, 00 is -64)
26	00~7F	Amount of Red on the Overlay
27	00~7F	Amount of Green on the Overlay
28	00~7F	Amount of Blue on the Overlay
29	00~7F	Overlay opacity
30	00~7F	Displays Text from Register (Channel), at size 01~7F (30 is equal to 1xsize). Size of 00 will End Display.
31	00/01	Disables/Enables Piano Renderer (overrides the setting in the menu)

MIDI CC Audio Effects
CC	Range 	Description
11	00~7F	Expression
14	00~7F	Volume Override (Targeted Channel)
15	00~7F	Reserved
64	00/7F	Hold (Release infinity)
72	00~7F	Release (00 = 0%, 40 = 100%, 7F = 200%, % of 200ms)
73	00~7F	Attack (00 = 0%, 40 = 100%, 7F = 200%, % of 200ms)
74	00~7F	Cutoff (00 = 0%, 40~7F = 100%, % of Volume)


MIDI CC Technical Effects (Advanced) [Medium Priority]
Revision 2
Note: First two characters = Value of CC. Last character is the Channel.
CC	Value A	Value B 	Value C	Description
102	00~7F	0~F	-	Sets B to A, B is the Variable, A is the value.
103	0~F	0~F	0~F	Does operation C from A to B. Results store to either A or B, depending on C.
104	0~F	0~F	0~F	Does comparision C between A and B. Results store to either A or B, depending on C.
105	00~7F	0~F	-	Obtains registered variable A, stores to B. Same as Revision 1 CC 107.
106	00~7F	0~F	-	Runs function A from registry, if B is TRUE (1). Same as Revision 1 CC 108
107	09~7F	0~F	-	Registers a variable from Register B*
108	00~7E	0~F	-	Registers a function, function index from Register B.*
109	10~7F	0~F	-	Gets value from list set in A, at index of value set in B. Use index 0 if A is variable, -1 to get value of A as a single-item list. Value is stored to 11th registered variable 0x0A.
110	10~7F	0~F	-	Sets the value at an index set in B of the list set in A. Use index 0 if A is variable, -1 to replace all list and set A as a single-item list. Value is obtained from the 11th registered variable 0x10.
111	10~7F	0~F	-	Removes a value at an index set in B of the list set in A. Use index 0 to delete the last item of A, -1 to delete/clear list A. This is, by far, the most dangerous function.
112	20~7F	0~F	-	Sets B to A, B is the Variable, A is the value (Returns text thru Unicode, use concat operation to join.)
113	00/01	0~F	-	Set to 0 to Disable Image View from Register. Set to 1 to Enable Image View from Register, if Register contains valid Hex Image Data.
								
*Some variables/functions cannot be modified or altered.

CC 103 Operations
Value C	Operation
0	A+B→A
1	A-B→A
2	A*B→A
3	A/B→A
4	B→A
5	A^B→A
6	A%B→A
7	round(B)→A	
8	A+B→B
9	A-B→B
A	A*B→B
B	A/B→B
C	A||B→B	
D	A^B→B	May change to random(0,A)→B
E	A%B→B	
F	1/A→B

CC 104 Operations
Value C	Operation
0	A>B→A
1	A<B→A
2	A=B→A
3	A!B→A
4	-
5	-
6	-
7	-
8	A>B→B
9	A<B→B
A	A=B→B
B	A!B→B
C	-
D	-
E	-
F	-	

Pre-defined list of variables for CC 105
Values 00~7F are stored to Register Channel.
Values	Description
00	MIDI ID
01	Variable 00 / Program State
02	USER ID number (index on user_list)
03	USER current tier
04	Current Tick
05	Current Notecount
06	Current NPS
07	Current FPS
08	Current Synth Limit

Pre-defined list of functions for CC 106
Values 00~7E target the lists registered.
Values 7F will force stop the Renderer.

All sub-characters for CC 112
For values 00 ~ 7F (0~127) in order

	00(0)	08(8)	10(16)	18(24)	20(32)	28(40)	30(48)	38(56)
+0		█	℗	░	 	(	0	8
+1	※	▄	®	▒	!	)	1	9
+2	°	▌	○	▓	"	*	2	:
+3	×	▐	↻		#	+	3	'
+4	¡	▀	↺		$	,	4	<
+5	¿	♪	§		%	-	5	=
+6	◘	♫	⋮		&	.	6	>
+7	•	◊	Γ		'	/	7	?

	40(64)	48(72)	50(80)	58(88)	60(96)	68(104)	70(112)	78(120)
+0	@	H	P	X	`	h	p	x
+1	A	I	Q	Y	a	i	q	y
+2	B	J	R	Z	b	j	r	z
+3	C	K	S	[	c	k	s	{
+4	D	L	T	\	d	l	t	|
+5	E	M	U	]	e	m	u	}
+6	F	N	V	^	f	n	v	~
+7	G	O	W	_	g	o	w	 
```


# Navigation Portal
> [Main Menu](https://daniferous.github.io/CelestialMIDIRender/)

> [Render Now! - Release 26.2 Build 3](https://daniferous.github.io/CelestialMIDIRender/render/CMR%2026.2B3.html)

> [View My Celestial Account](https://daniferous.github.io/CelestialMIDIRender/account)

> [Check out the Celestial Concourse for new deals!](https://daniferous.github.io/CelestialMIDIRender/concourse)

> [Read the Celestial MIDI Render - End User License Agreement](https://daniferous.github.io/CelestialMIDIRender/EULA/)

> [More about MIDI Specifications](https://daniferous.github.io/CelestialMIDIRender/specs/)

> [Celestial MIDI Software Support Page](https://daniferous.github.io/CelestialMIDIRender/support/)