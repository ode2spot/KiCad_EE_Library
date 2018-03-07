# KiCad EE Library

## KiCAD Library Setup

Library Naming Conventions
* must not be the same as built-in library
* prefix with unique designator for compatibility, eg EE_[NAME]
* should be as generic as possible, eg EE_Resistor_SMD, EE_Capacitor_SMD, EE_OpAmp ...


### Schematic Library Setup

Schematic Libraries are located at "~/Seed/Resources/KiCad_EE_Library/lib_Files/[LibraryName].lib"

Add schematic library to library list:
1) open Schematic Library Editor
2) go to Preferences->Component Libraries
3) add library

Make a new library by "saving as" with a library open (out of date with nightly build!)

#### Part Field Properties
NOTE: add these through KiCad -> Preferences -> Template Field Names

Field|Description
-----------------------|---------------------------------------------------
*Reference:|reference designator
*Value:|unique name of the part, include all relevant data points except manufacturer
*Footprint:|filepath to footprint -> [FootprintLibrary(.pretty)]:[FootprintName], click "assign footprint" for wizard
*Datasheet:|URL for datasheet
PartValue:|displayed value of the part, eg Resistors -> resistance, Capacitors -> capacitance, IC's -> part number
Composition:|construction material, eg Resistors -> ThinFilm/ThickFilm, Capacitors -> C0G/PPS ...
Precision:|precision of part
PowerRating:|maximum power dissipation of part
VoltageRating:|maximum allowed voltage across the part
CurrentRating:|maximum allowed current through the part
Tempco:|temperature coefficient
PbFree:|is part lead-free, bool
RoHS:|is part RoHS compliant, bool
Manufacturer:|manufacturer of part
MPN:|Manufacturer Part Number
MouserPN:|Mouser Part Number
DigiKeyPN:|DigiKey Part Number
SmallBearPN:|Small Bear Electronics Part Number
MammothPN:|Mammoth Electronics Part Number
TaydaPN:|Tayda Part Number
MouserPrice:|price for 1 unit @ Mouser
DigiKeyPrice:|price for 1 unit @ DigiKey
SmallBearPrice:|price for 1 unit @ SmallBear
MammothPrice:|price for 1 unit @ Mammoth
TaydaPrice:|price for 1 unit @ Tayda
ALTMPN:|Alternative Manufacturer Part Number
ALTMouserPN:|ALT Part Mouser Part Number
ALTDigiKeyPN:|ALT Part DigiKey Part Number
ALTMouserPrice:|ALT Part price for 1 unit @ Mouser
ALTDigiKeyPrice:|ALT Part price for 1 unit @ DigiKey

NOTE: * = default

### Footprint Setup

Local footprints are located at "~/Seed/Resources/KiCad_EE_Library/footprints/[LibraryName(.pretty)]/"

Add footprint Library to library list:
1) open PCB Footprint Editor
2) Preferences -> Footprint Libraries Manager
3) Append Library
4) use {KIUSRMOD} in path.  NOTE: KIUSRMOD is defined using Preferences -> Configure Paths



### 3D Setup

3D packages exist at "~/Seed/Resources/KiCad_EE_Library/packages3d/[LibraryName(.3dshapes)]/"

each package has two 3D models: .step, .wrl


To set a part's 3D model:
1) open PCB Footprint Editor
2) open library and load footprint
3) open Footprint Properties -> 3D Settings
4) click Add 3D Shape and navigate to desired 3D model


built-in 3D models can be found at "~/Seed/Resources/KiCad_GIT_Library/kicad-packages3D/"
which is downloaded from the KiCad git page


### 3D Exporting

To generate a 3D .dae board file:
run "kicadStepDAE [BoardFileName]" from the BoardFileName's directory

"kicadStepDAE" is a script located in "/usr/local/bin"
this script runs a FreeCAD macro on the supplied file name

The FreeCAD macro is called "kicad-StepUp-tools.FCMacro" and is located at "~/Library/Preferences/FreeCAD/Macro"
This macro uses "~/ksu-config.ini" for its configuration settings

"~/ksu-config.ini" points to "~/Seed/Resources/KiCadLibrary/packages3d/" as the location
for the local 3D models

The "kicad-StepUp-tools.FCMacro" opens the BoardFile in FreeCAD, loads each part's 3D model from the local file path
declared in the configuration file, and exports the board file as both a .step and .dae
