## Overview

The INA180 from Texas Instruments is a current-sense amplifier designed for low-side current sensing applications. It features a wide supply voltage range of 2.7V to 26V, making it suitable for both battery-operated and automotive applications. With its precision, low offset voltage, and a gain range from 20 V/V to 200 V/V across various versions, it provides accurate current measurement in systems requiring energy.

![INA180](https://firebasestorage.googleapis.com/v0/b/atopile.appspot.com/o/low-side-current-sensor.png?alt=media&token=1805c393-ecab-404a-be20-12081b7320ad "INA180")

## Usage Example

```
import INA180 from "ina180/ina180.ato"
import Power from "generics/interfaces.ato"
import Resistor from "generics/resistors.ato"

module LowSideCurrentSensing:
   powerSupply = new Power
   currentSenseAmp = new INA180
   shuntResistor = new Resistor
   
   # Configure power supply interface for INA180
   powerSupply.voltage = "3.3V to 26V"  # Supply voltage for INA180
   currentSenseAmp.vcc ~ powerSupply.vcc
   currentSenseAmp.gnd ~ powerSupply.gnd
   
   # Shunt resistor configuration for current sensing
   shuntResistor.value = "0.1ohm +/- 1%"  # Example value, adjust as needed
   shuntResistor.footprint = "1206"  # Example footprint, adjust as needed
   
   # INA180 input connections for low-side current sensing
   currentSenseAmp.in+ ~ shuntResistor.p1
   currentSenseAmp.in- ~ shuntResistor.p2
   
   # Load connections (not shown in the example, connect your load here)
   # load.p1 ~ shuntResistor.p2
   # load.p2 ~ powerSupply.gnd

   # Gain configuration for desired measurement range
   # Choose the correct INA180 variant based on the required gain
   currentSenseAmp.gain = "20 V/V"  # Example gain, adjust based on INA180 variant used

```

## Features

### Power Interface: 
Wide supply voltage range from 2.7V to 26V

### Current-Sense Interface: 
High-side measurement, low-side measurement capability with a common-mode voltage range from -0.3V to 26V.

### Gain Options: 
Available in multiple fixed-gain variants (20 V/V to 200 V/V).

## Contributing
Contribute to this package using pull requests.

## License
This current-sense amplifier module is provided under the MIT License.

## Contact
For further inquiries or support, please contact me at narayan@atopile.io.




