# OctoPrint-FilamentReloaded

[OctoPrint](http://octoprint.org/) plugin that integrates with a filament sensor hooked up to a Raspberry Pi GPIO pin and allows the filament spool to be changed during a print if the filament runs out.

Future developments are planned to include multiple filament sensors and pop-ups.

Initial work based on the [Octoprint-Filament](https://github.com/MoonshineSG/Octoprint-Filament) plugin by MoonshineSG and Octoprint-Reloaded plugin by [kontakt](https://github.com/kontakt/Octoprint-Filament-Reloaded/archive/master.zip) and [ssorgatem](https://github.com/ssorgatem/Octoprint-Filament-Reloaded/archive/master.zip)

## Required sensor

Using this plugin requires a filament sensor. The code is set to use the Raspberry Pi's internal Pull-Up resistors, so the switch should be between your detection pin and a ground pin.

This plugin is using the GPIO.BOARD numbering scheme, the pin being used needs to be selected by the physical pin number.

## Features

* Configurable GPIO pin (including the type of resistor on the pin)
* Debounce noisy sensors.
* Support normally open and normally closed sensors.
* Execution of custom GCODE when out of filament detected.
* Optionally pause print when out of filament.
* Icon in the nav bar to reflect filament detection status. (with check frequency in parameters)

An API is available to check the filament sensor status via a GET method to `/plugin/filamentreload/status` which returns a JSON

- `{status: "-1"}` if the sensor is not setup
- `{status: "0"}` if the sensor is OFF (filament not present)
- `{status: "1"}` if the sensor is ON (filament present)

## Installation

* Install via the bundled [Plugin Manager](https://plugins.octoprint.org/plugins/filament_sensor_reloaded/). _Installs [ssorgatem](https://github.com/ssorgatem/Octoprint-Filament-Reloaded/archive/master.zip) version._
* Manually using this URL: https://github.com/nickmitchko/Octoprint-Filament-Reloaded

## Configuration

After installation, configure the plugin via OctoPrint Settings interface.

* Wire the sensor pin to Pin 18

  ![pi pins](https://user-images.githubusercontent.com/7769991/151637147-26865806-1e60-4114-a93e-4e437530c197.png)
* Ensure the "Board Pin Mode" Setting to "Board Mode"

* Connect filament sensor ground to pin 4 and voltage to pin 1. Use only 3.3v, not 5v for sensor! 

