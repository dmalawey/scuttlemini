# Design
_The designs as of 2025 are working designs.  Working docs are for distributing robot modules between collaborators, but the designs may be pre-prototype and untested._

# Intentions
_Design intentions discussion here.  For the full design, the intent must be decided collaboratively.  For the design of modules, a respective expert can make initial targets & describe design intent in this section.

### Goals

> Key Goals for Design
>
> * Support low-cost, repeatable build from the ground-up in any global region.
> * Generate a minimal viable DDMR configuration for 10kg payload
> * Fully modular design: every part belongs to a subassembly which has utility or testable goals independent of the full robot
> * Minimize custom parts: The robot is a custom design but the parts should be standard, as much as possible
> * Commonization:  Aim to match SCUTTLE original modules in design details for: Selection of hardware, wiring configuration, etc.
> * Outsourced Data: for each module and each part, we use well-documented selections, and design choices backed by ubiquitous data.
> * Ownership of design: each module can be traced to an "owner" who fully understands the module & can produce documentation
> 

### Resources
_resources for designers arriving to help_

* [SCUTTLE Tech Guide](https://qr.net/scuttleproject) _a github-based webpage for scuttle designs_
* [SCUTTLE Miniguides](https://scuttlerobot.org/resources) _design & eval data on scuttlerobot.org website_
* [Youtube playlist](https://www.youtube.com/playlist?list=PLHkrnCQ5sDmdyelgZAIN76-Y_Tug1E4Ug) _playlist of videos related to scuttle robot, by D. Malawey_

### Glossary

* DDMR: differential drive mobile robot
* ownership: responsibility for producing professional explanatiosn for each decision in an item.


## Chassis
_Descriptions for parts, construction, key tolerances, assembly, and design intent for each module.

### Frame
The aluminum rectangular frame, and DIN rail mounting configuration.

* Material : Aluminum extrusion (2020 profile, Width: 160mm, Length: 200mm, Height: 20mm).
  * Lightweight yet strong, suitable for a 10kg payload.
  * Compatible with DIN rail mounting for easy assembly of submodules. (in progress)

### Wheel Assembly
Design for wheel module with wheel, bearings, shaft, pulley, motor, and belt as needed.

* Wheels : Inline skate wheels (80mm diameter).
  * Provide excellent grip and smooth movement.
* Bearings : Standard 608ZZ bearings for durability and ease of replacement.
* Motors : DC motors
  * intended: to use original SCUTTLE 12v gearmotor, near 5 watts peak (each)
  * rated at 200 or 300 rpm, from original scuttle (for easy kinematics)
  * shaft is d-shaped with aluminum pulley, OTS
  * variations of motor available with shorter body, for clearance on chassis
* Belts and Pulleys :
  * 20-tooth pulley, aluminum, for motor shaft
  * 60-tooth pulley, printed, for wheel (adjustable)
  * Belt will be between 200-300 teeth, with pulley spacing revisions
    
### Prints
We are aiming for one special printing challenge, and that's a fine-pitch wheel pulley with GT2 tooth style.  Before 2020, average 3D printers couldn't accurately produce fine features for successful 2.0mm pulley tooth pitch.  Now, it is feasible but it just requires a bit of special attention.
* from our discord, [Tips for Printing Pulleys](https://www.chiefdelphi.com/t/3dp-pulleys-advice-tips-successes/455441) was shared for our designers.
* challenge no.1 is to design the simplest parametric pulley for the wheel.  We need the tooth count and diameter to match, based on user inputs.
  *  A draft [pulley design](https://grabcad.com/library/pulley_gt2-1) by DM is posted for initial trials (but it's not parametric)
  *  A parametric [pulley design here](https://grabcad.com/library/gt2-parametric-pulley-sw21-1) might be suitable for borrowing equations.

### Unique parts
Discussion of parts that differ from a downscaled version of SCUTTLE Original design.

* Redesigned Brackets : Adapted from SCUTTLE 3030 to fit the smaller 2020 extrusion. (but still can be improve)
* Solar Panel Mount : Custom-designed to integrate solar charging capabilities.

## BOM
Parts list

_Suggested materials copied from BOM spreadsheet, updated 2025.02.24_

| Item         | Product                                                                                                                |
| ------------ | ---------------------------------------------------------------------------------------------------------------------- |
| Extrusion    | [10pcs 1m amazon](https://www.amazon.com/Aluminum-Extrusion-European-Standard-Anodized/dp/B08PQPK379)                  |
| Wheels       | skate wheels 70mm, Amazon                                                                                              |
| Motor Driver | [4pcs L298N Amazon](https://www.amazon.com/HiLetgo-Controller-Stepper-H-Bridge-Mega2560/dp/B07BK1QL5T)                 |
| Encoders     | [AS5600 10-bit Encoder, Amazon](https://www.amazon.com/Magnetic-Encoder-Induction-Measurement-Precision/dp/B097QNG1CN) |
| Motors       | [10pcs gearmotor 113RPM Amazon](https://www.amazon.com/DC-Gear-Motor-Planetary-Industrial/dp/B07XMFLSPB)               |
| Connectors   | [75pcs lever wire connectors](https://www.amazon.com/dp/B08HXXWLT8)                                                    |
| Camera       | [arducam 5mp](https://www.amazon.com/Arducam-Megapixels-Sensor-OV5647-Raspberry/dp/B012V1HEP4)                         |
| Battery      | [LiPo 4pack Amazon](https://www.amazon.com/Tattu-Packs-450mAh-7-4V-Battery/dp/B07K18DJG5)                              |
| Fasteners    | [M5 drop in nuts](https://www.amazon.com/Fastener-Nickel-Plated-Sliding-Aluminum-Profile/dp/B086MKNYDS)                |
| DIN rail     | [10pcs 1m amazon](https://www.amazon.com/Aluminum-Professionals-Hardware-Components-Mounting/dp/B088FFHCDC)            |
| Corners      | [20sets M5 corner brkt](https://www.amazon.com/Aluminum-Profile-Connector-Bracket-Accessories/dp/B0855V2JV3)           |
| casters      | [50pcs blue caster amazon](https://www.amazon.com/dp/B07D2GWL2T)                                                       |
| belts        | [timing belt GT2, 10pcs, amazon](https://www.amazon.com/3Dman-Timing-Closed-Rubber-Printer/dp/B07V6N32B1)              |
| pulley       | [aluminum pulley GT2x16, amazon](https://www.amazon.com/Saiper-Aluminum-Synchronous-Compatible-Printer/dp/B07M9FT3H1)  |
| 3D Parts     | Filament, 1kg, amazon                                                                                                  |
| CPU          | [ESP8266, amazon](https://www.amazon.com/HiLetgo-Internet-Development-Wireless-Micropython/dp/B081CSJV2V)              |

### Wheels

Recommended wheels are sourced from inline-skate type wheels.  
* Example parts on amazon: [skate wheels](https://www.amazon.com/dp/B08CT98HFB)
* Diameter is 80mm, one of the most common standards.  This is about 3/4 diameter of original scuttle
* Clean CAD model on grabCAD: [grabcad skate wheel](https://grabcad.com/library/skatewheel-1)
  
- ![skate wheel products](img/img_skateWheel.jpg)
- ![skate wheel CAD model](img/img_skateWheel2.jpg)
