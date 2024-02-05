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
- go_minmus : Launches a vessel to Minmus and lands it... somewhere.
- return_to_kerbin: returns to kerbin from a moon in the Kerbin system. Tested with the Mun. Assumes you have parachutes

The scripts will stage as needed. Debug and status output is shown in the console, opening it is highly recommended.

## Phases of a Mission

Initially the vessel is launched, gravity turn is performed and we climb to close to the target apoapsis. Usually an additional burn is performed to fune tune once we have exited the atmosphere. After circularization, we check if the inclination needs to be change. 

Then the transfer is planned. For anything but Mun, the transfer from Kerbin will happen in two phases:
1. An initial burn to get on an escape trajectory from Kerbin
2. A second burn executed above 100k km altitude to fine tune the trajectory and get a good encounter

After the correction burn, we wait until we are in the spehere of influence (SOI) of the target body. Once that is the case, we circularize, lower periapsis and lower apopasis to the target orbit height.

Last we pick a spot to land, slow down close to that spot and the auto lander plans and executed a (hopefully) soft landing. Right now landing spots are hardcoded, we do no check the terrain for suitability.

Return starts with an initial burn to an apoapsis that is circularized. We then claculate ejection angles (at least in the Kerbin system) and perform an ejection burn. This should put us into an elliptical orbit around Kerbin. We then wait for the Apoapsis, lower periapsis and attempt aero capture. This may happen over a number of passes to reduce heat.

Once Periapsis is below sea level, the landing code takes over, waits for safe opening of parachutes and lands.

Most scripts are written that they can be aborted and re-started at most time. Quicksave is your friend.

## Where to get help with the scripts

Best place to get help are the [KSP forums](https://forum.kerbalspaceprogram.com/topic/214543-release-kontrolsystem2-042/). 

If you encounter a bug or have a suggestions, please file it here on GitHub.

