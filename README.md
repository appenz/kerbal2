# Kerbal Space Program 2

Automation for KSP2 written with KontrolSystem2.

## Installation

Tested with the Steam version of Kerbal Space Program 2, but it should work with any version.
1. Install [Kontrolsystem2](https://spacedock.info/mod/3316/Kontrol%20System%202), the easiest way to do this is via [CKAN](https://forum.kerbalspaceprogram.com/topic/154922-ckan-the-comprehensive-kerbal-archive-network-v1280-dyson/) as it will pull in all needed dependencies.
2. Clone this GitHub repo in a directory of your choice. Once cloned, go into the BepInEx configuration and set the "localLibPath" to this directory. You can alternatively copy the files from this project into the KSP2/BepInEx/plugins/KontrolSystem2/to2Local directory.

Now when you launch KSP2 and select the rightmost icon at the center bottom (looks like 3x3 squares) there should be a new option "Kontrol System 2"

## Using the scripts

Right now there are the following missions:
- launch_to_orbit: launches a vessel into low Kerbin orbit.
- land_athmosphere: lands a vessel from orbit around Kerbin. Assumes you have parachutes. Tries to land near the KSC.
- go_mun : Launches a vessel to the Mun and lands in a flat area near the Mun's equator. Needs enough delta_v to get there.
- return_to_kerbin: returns to kerbin from a moon in the Kerbin system. Tested with the Mun. Assumes you have parachutes.

The scripts will stage as needed. Debug and status output is shown in the console, opening it is highly recommended.
