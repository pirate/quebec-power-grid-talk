# Quebec's 735kv power lines can survive the apocalypse, but can they run TCP?!

*Slides and resources for the [!!con 2020](http://bangbangcon.com/) talk.*

## Description

Quebec built the world's first 735 kV power line in 1965, and was the highest-voltage, longest-distance network for decades before the rest of the world caught up. Even today it's still seen as "bomb-proof" by the rest of the world, and is often used as a model. But it wasn't always that way...

When a massive ice storm took down 36,000 power pylons overnight in 1998, Quebec had to rebuild and restart their power grid from the ground up. Let's do some failure analysis and learn how big power systems around the world are designed to fail gracefully, and what happens when they don't. (P.S. TCP over power lines totally works)

## Speaker Bio

Nick Sweeting is the co-founder of [Monadical](https://monadical.com) in Montreal, and his favorite bike paths all run under power lines. He's a Django developer by day, and rogue internet archivist / power grid investigator by night. He likes learning about how big systems fail, and thinks thyristor halls look neat.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Pole_2_Thyristor_Valve.jpg/600px-Pole_2_Thyristor_Valve.jpg)

## Outline

- 2min: intro, photos of james bay project
	- hydro quebec origin story
	- mega dams near the arctic circle + big wires
  - modern distinct grid regions of North America
    - (Quebec & Texas = independent)
- 3min: technical overview of power systems
	- High-voltage 3-phase AC / phased power systems
	- old school: transformers and fuses
	- modern: capacitors + thyristors + optic coupling
  - grid electricity uses a whole different set of tools and math from micro eletronics
    - frequency syncronization, phase balancing
    - Hz = spinning kitectic energy in the system
    - distance measuring by bouncing a pulse down the wire and timing each impedance mismatch's reflected pulse
- 3min: HVDC, edison wins after all
	- good for long distances grid connections with no step-ups / step-downs (Quebec sells lots of power to NY northeast USA)
	- more efficient wiring, no skin effect
	- rescue lifeline in blackout situations
	- easier to control digitally
- 1min: theres a whole world of network chatter on power lines
    - channels are coupled on and off with capacitors, like radio
    - signals get attenuated by transformers / capacitative loss / radio transmission losses (aka pollution)
		- AM radio band for home entertainment radio stations
		- ~100-500kHz: OSGP, IOT, home automation, meter reading
		- ~9-500kHz: DLC MAC ethernets with IPv6 at 576 kbit/s for grid contorl and meter reading
		- ≥ 1 MHz LAN: ethernet-over-power AC wall wart systems
		- 2.4-6GHz BPL: long-distance broadband backhaul, but causes lots of interference because the grid is a massive antenna
		- ≥100 MHz transverse mode: long-distance >1 Gbit/s connections, but interferes with astronomy and lots of other stuff
- 2min: how does this carry over to software?
  - modular pieces with industry-shared common APIs
	- it's a distributed system: time synchronization, leader election, back-pressure communication
  - it's a critical system: graceful degradation, load-shedding, split brain avoidance, and staggered restart procedures
	- it's an abstracted system: humans, politics, circular dependencies ("we cant start the database without the auth server running first" == "we cant start this natural gas power plant without grid power to spin up its compressors")
