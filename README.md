# Quebec's 735kv power lines can survive the apocalypse, but can they run TCP?!

<b>The challenges involved in designing and maintaining one of the most resilient power grids on earth,<br/>
and lessons we can learn from the grid as software engineers.</b>

Speaker Info: [Nick Sweeting](https://nicksweeting.com) | [@theSquashSH](https://twitter.com/theSquashSH) on Twitter | [@pirate](https://github.com/pirate) on Github | [LinkedIn](https://www.linkedin.com/in/nick-sweeting-430999b3/)  
> Co-Founder @ Monadical, a startup based in Medellín, NYC, and Montréal, with remote employees around the world.  
[Monadical](https://monadical.com) is a software development shop doing full-stack development and project management.

<a href="https://youtu.be/QEZ0N0rrbL0?t=24039"><img src="https://img.shields.io/badge/Watch-YouTube-red.svg?style=flat"/></a>
<a href="https://twitter.com/thesquashSH"><img src="https://img.shields.io/badge/Tweet-%40theSquashSH-lightblue.svg?style=flat"/></a>
<a href="https://github.com/pirate/quebec-power-grid-talk"><img src="https://img.shields.io/github/stars/pirate/quebec-power-grid-talk.svg?style=flat&label=Star+on+Github"/></a>

---

<div style="text-align:center">
<a href="https://youtu.be/QEZ0N0rrbL0?t=24039">
<img src="https://i.imgur.com/djJFxnu.png" alt="First slide of talk" width="500px">
</a>
</div>
<a href="https://youtu.be/QEZ0N0rrbL0?t=24039">Video (YouTube)</a>, <a href="https://pirate.github.io/quebec-power-grid-talk/Quebec%20Power%20Grid%20Talk.pdf">Slides (PDF)</a>

`#bangbangcon2020` `#virtualbangbangcon` `#electrical-grid` `#distributed-systems` `#failure-analysis` `#safety-engineering` `#infrastructure`

## Events & Video

- [**!!con 2020**](http://bangbangcon.com/speakers.html#nick-sweeting) @ *Virtual Conference* on 2020/05/09  
  Video: https://youtu.be/QEZ0N0rrbL0?t=24039

- [Burning Man 2019](https://burningman.org/event/art-performance/performance-opportunities/center-camp-cafe/2/) @ Black Rock City on 2019/09/01  
  Center Camp Cafe open mic lightning talks (not recorded)

## Slides

 - [PDF](https://pirate.github.io/quebec-power-grid-talk/Quebec%20Power%20Grid%20Talk.pdf)
 - [HTML](https://pirate.github.io/quebec-power-grid-talk/Quebec%20Power%20Grid%20Talk/assets/player/KeynoteDHTMLPlayer.html#0)
 - [Keynote](https://github.com/pirate/quebec-power-grid-talk/raw/master/Quebec%20Power%20Grid%20Talk.key)
 - [SlideShare](https://www.slideshare.net/NickSweeting1/quebecs-735kv-power-lines-can-survive-the-apocalypse-but-can-they-run-tcp)
 - [SpeakerDeck](https://speakerdeck.com/pirate/quebecs-735kv-power-lines-can-survive-the-apocalypse-but-can-they-run-tcp)

## Description

Quebec built the world's first 735 kV power line in 1965, and was the highest-voltage, longest-distance network for decades before the rest of the world caught up. Even today it's still seen as "bomb-proof" by the rest of the world, and is often used as a model. But it wasn't always that way...

When a massive ice storm took down 36,000 power pylons overnight in 1998, Quebec had to rebuild and restart their power grid from the ground up. Let's do some failure analysis and learn how big power systems around the world are designed to fail gracefully, and what happens when they don't. (P.S. TCP over power lines totally works)

## Speaker Bio

Nick Sweeting is the co-founder of [Monadical](https://monadical.com) in Montreal, and his favorite bike paths all run under power lines. He's a Django developer by day, and rogue internet archivist / power grid investigator by night. He likes learning about how big systems fail, and thinks thyristor halls look neat.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/04/Pole_2_Thyristor_Valve.jpg/600px-Pole_2_Thyristor_Valve.jpg)

## Outline

- 1min: intro, photos of james bay project
    - hydro quebec origin story, now it has 20,000+ employees
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
- 2min: HVDC, edison wins after all
    - good for long distances grid connections with no step-ups / step-downs (Quebec sells lots of power to NY northeast USA)
    - more efficient wiring, no skin effect
    - rescue lifeline in blackout situations
    - easier to control digitally (https://en.wikipedia.org/wiki/Static_VAR_compensator)
- 2min: theres a whole world of network chatter on power lines
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
    

## Quotes & Images

> Altogether the reservoirs created by the James Bay Project cover an area of 13,341 square kilometers - the largest bodies of water ever created by humankind. One of the reservoirs, Caniapiscau, is the largest freshwater lake in Quebec.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/D%C3%A9versoir%2C_Centrale_hydro-%C3%A9lectrique_Robert-Bourassa.jpg/600px-D%C3%A9versoir%2C_Centrale_hydro-%C3%A9lectrique_Robert-Bourassa.jpg)

> In addition to the six 735 kV power lines that stem from the James Bay Project, a seventh power line was constructed as an 1,100 kilometres (680 mi) northward extension of an existing high-voltage direct current (HVDC) line connecting Quebec and New England. This power line expansion was completed in 1990. As a result, the direct current power line is unique because there are multiple static converter and inverter stations along the 1,480 kilometres (920 mi) long power line.[8] It is also the first multiterminal HVDC line in the world. The ±450 kV power line can transmit about 2,000 MW of hydroelectric power to Montreal and the Northeastern United States.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/4f/Quebec_Map_with_Hydro-Qu%C3%A9bec_infrastructures-en.png/660px-Quebec_Map_with_Hydro-Qu%C3%A9bec_infrastructures-en.png" width="500px">

<img src="https://upload.wikimedia.org/wikipedia/commons/f/fe/Nercmap.JPG" width="500px">

> The pylons and conductors are designed to handle 45 millimetres (1.8 inches) of ice accumulation without failure,[19] since Hydro-Québec raised the standards in response to ice storms in Ottawa in December 1986 and Montreal in February 1961, which left 30 to 40 millimetres (1.2 to 1.6 inches) of ice.[50][51][52] This has led to the belief that Hydro-Québec TransÉnergie's electrical pylons are "indestructible".[53] Despite being more than three times higher than the Canadian standard of only 13 millimetres (0.51 inches) of ice tolerance,[54] an ice storm in the late-1990s deposited up to 70 millimetres (2.8 inches) of ice.[19][51]

<img src="https://www.howitworksdaily.com/wp-content/uploads/2012/11/Ice.jpg" width="500px">

> In the North American ice storm of 1998, five days of freezing rain collapsed 600 kilometres (370 mi) of high voltage power lines and over 3,000 kilometres (1,900 mi) of medium and low voltage distribution lines in southern Quebec. Up to 1.4 million customers were without power for up to five weeks.

<img src="https://news.hydroquebec.com/media/filer_public/2018/01/05/98-006-3-0109_tn.jpg" width="500px">

```quote
The 1998 ice storm in numbers:

- Up to 1.4 million households without power
- Over three million people affected
- 3,000 km of transmission and distribution lines rebuilt
- 400 km of high-voltage lines rebuilt
- 1,500 towers replaced
- 17,000 poles replaced
- 4,500 transformers replaced
- 88,000 insulators replaced
```
```quote
Changing the transmission system to create loops to deliver power over more than one path:
- Creation of the 735-kV Montérégie loop and the 315-kV downtown Montréal loop
- rearranging the system between Québec and Trois-Rivières to create the Québec-Mauricie loop
- Reinforcing the supply to downtown Québec
- Integration of the new 735-kV Bout-de-l’Île substation to the 735-kV greater Montréal loop
```

<img src="https://i.imgur.com/8A9WCFR.jpg" width="500px">

> The Levis De-Icer is a High voltage direct current (HVDC) system, aimed at de-icing multiple AC power lines in Quebec, Canada. It is the only HVDC system not used for power transmission.
> In the winter of 1998, Québec's power lines were toppled by icing, sometimes up to 75 mm. To prevent such a damage, a de-icing system was developed.[1]
> The Levis De-Icer can use a maximum power of 250 MW; its operation voltage is ±17.4 kV. It can be used on multiple 735 kV AC power lines. An ordinary 735 kV line with a bundle of four 1354 MCM conductors per phase, requires a de-icing current of 7200 A per phase.[4] At −10 °C and wind velocity at 10 km/h, it would take 30 minutes of current injection on a phase to melt 12 mm of radial build-up of ice.

<img src="https://i.imgur.com/XEMmcnU.png" width="500px">
<img src="https://i.ytimg.com/vi/ZPLRwEMASbA/maxresdefault.jpg" width="200px">

---

## Further Reading

### Primary Sources, Press, Reference Material

- https://news.hydroquebec.com/en/press-releases/1313/twenty-years-ago-quebec-was-battered-by-an-ice-storm/
- https://www.compusult.com/html/IWAIS_Proceedings/IWAIS_2005/Papers/IW09.PDF
- http://www.hydroquebec.com/data/transenergie/pdf/2019-12-31-liste-centrales-privees-raccordees-reseau-hydro-quebec.pdf
- https://www.iso-ne.com/about/key-stats/maps-and-diagrams/#system-diagram
- https://www.iso-ne.com/static-assets/documents/2016/07/New-England-Geographic-Diagram-Transmission-Planning-Through-2026.pdf  
- https://electricity.ca/wp-content/uploads/2017/05/CEA_16-086_The_North_American_E_WEB.pdf
- https://gotocon.com/dl/goto-aar-2013/slides/SebastianEgner_ProgrammingLanguagesAndThePowerGrid.pdf
- https://www.jamesbayroad.com/hydro/index.html

### Wikis

- https://en.wikipedia.org/wiki/Hydro-Qu%C3%A9bec
- https://en.wikipedia.org/wiki/History_of_Hydro-Qu%C3%A9bec
- https://en.wikipedia.org/wiki/Hydro-Qu%C3%A9bec%27s_electricity_transmission_system
- https://en.wikipedia.org/wiki/Timeline_of_Quebec_history
- https://en.wikipedia.org/wiki/James_Bay_Project
- https://en.wikipedia.org/wiki/James_Bay_Energy
- https://en.wikipedia.org/wiki/Robert-Bourassa_generating_station
- https://en.wikipedia.org/wiki/List_of_generating_stations_in_Quebec
- https://en.wikipedia.org/wiki/High-voltage_direct_current
- https://en.wikipedia.org/wiki/Quebec_%E2%80%93_New_England_Transmission
- https://en.wikipedia.org/wiki/Saint_Lawrence_River_HVDC_Powerline_Crossing
- https://en.wikipedia.org/wiki/Champlain_Hudson_Power_Express
- https://en.wikipedia.org/wiki/Levis_De-Icer
- https://en.wikipedia.org/wiki/Smart_grid
- https://en.wikipedia.org/wiki/Power-line_communication
- https://en.wikipedia.org/wiki/Hydro-Qu%C3%A9bec%27s_electricity_transmission_system#Electricity_pylons
- https://en.wikipedia.org/wiki/Nationalization_of_electricity_in_Quebec


### Books

- [White Gold: Hydroelectric Power in Canada](https://books.google.ca/books?id=YixStndEudYC) by Karl Froschauer
- [Canadian Power Imports: Update on Electricity Imports in the Northeast ...](https://books.google.ca/books?id=soQGXnzg24QC) by USA Gov. General Accounting Office
- [The Power Grid: Smart, Secure, Green and Reliable](https://books.google.ca/books?id=d48xDQAAQBAJ) edited by Brian D’Andrade
- [The Grid: The Fraying Wires Between Americans and Our Energy Future](https://www.amazon.ca/Grid-Fraying-Between-Americans-Energy/dp/1608196100) by Gretchen Bakke
- [Energy and Civilization: A History](https://www.amazon.ca/Energy-Civilization-History-MIT-Press-ebook/dp/B072FH69YH/) by Vaclav Smil
- [Charging Ahead: Hydro-Québec and the Future of Electricity](https://www.amazon.ca/Charging-Ahead-Hydro-Qu%C3%A9bec-Future-Electricity/dp/1771862017/) by Julie Barlow and Jean-Benoït Nadeau
- [Hydro-Quebec: After 100 Years of Electricity](https://www.amazon.ca/Andre-Clarence-Daniel-Larouche-Bolduc/dp/2891113888/) by Daniel Larouche Bolduc, Andre, Clarence Hogue
- [Power from the North: Territory, Identity, and the Culture of Hydroelectricity in Quebec](https://www.amazon.ca/Power-North-Territory-Identity-Hydroelectricity/dp/0774824174/) by Caroline Desbiens
- [Power Struggles: Hydro Development and First Nations in Manitoba and Quebec](https://www.amazon.ca/Power-Struggles-Development-Nations-Manitoba/dp/0887557058/) by Thibault Martin and Steven M. Hoffman
- [Hydro-Québec and the Great Whale project: Hydroelectric development in northern Québec](https://www.amazon.ca/Hydro-Qu%C3%A9bec-Great-Whale-project-Hydroelectric/dp/1879775158/) by Susan Williams (1994)
- [Power from the North](https://www.amazon.ca/Power-north-Robert-Bourassa/dp/0136883672/) by Robert Bourassa (1985)
- [Social and Environmental Impacts of the James Bay Hydroelectric Project](https://www.amazon.ca/Social-Environmental-Impacts-Hydroelectric-Project/dp/0773518363/) by James F. Hornig (1999)
- [The James Bay Project](https://www.amazon.ca/James-Bay-Project-Jill-Johnston-ebook/dp/B003FSTKIM/) by Jill M. Johnston (2009)
- [ELECTRIC RIVERS](https://www.amazon.ca/ELECTRIC-RIVERS-Sean-McCutcheon/dp/1895431190/) by Sean McCutcheon (1998)
- [More reference books by Hydro Quebec...](https://www.amazon.ca/s?i=stripbooks&rh=p_27%3AHydro-Qu%C3%A9bec&s=relevancerank&text=Hydro-Qu%C3%A9bec&ref=dp_byline_sr_book_1)
- [J’aime Hydro](https://www.theglobeandmail.com/arts/theatre-and-performance/investigative-playwriting-shines-light-on-myths-and-realities-ofhydro-quebec/article38013768/) documentary theatre piece by Christine Beaulieu (2018)

---

<div style="text-align:center">
<img src="https://i.imgur.com/FiXKQ2R.png" width="200px">
<br/>
<i>Contact me on Twiter [@theSquashSH](https://twitter.com/theSquashSH) for corrections or suggestions!  You're welcome to use content or portions of the talk with permission, as long as you give credit to both this talk and the relevant sources I cite.</i>
<br/>
<a rel="license" href="http://creativecommons.org/licenses/by/3.0/us/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/3.0/us/88x31.png" /></a>
</div>
