---
layout: post
title:  "SM250 Teardown and Fix"
date:   2020-06-17 17:45:00 -0400
categories: teardown
---

![Assembled Machine](/assets/images/snow_full.jpg)

This year I was Hoping to spice up my yearly Christmas lights display show by adding some new DMX enabled effects. The idea is to get items in the form of mass-produced stage equipment,  which can be cheaper than purpose built “Holiday Lighting” products, while also being more robust and configurable. 
Living in the Southern U.S. where white Christmases do not exist, a snow machine was a great first choice. If you do not know how one of these machines work, the YouTube channel bigclivedotcom has an excellent short video on how they work [here](https://www.youtube.com/watch?v=s_gkSbQXKH8). I opted to purchase a used [Chauvet DJ SM250 Snow Machine](https://www.chauvetdj.com/products/sm-250/). 
Unfortunately, because I did not buy this product new, this teardown must be taken with a grain of salt (However unlikely, I do not know what modifications the previous owner could have made). It is a good look though at how a lightly used machine looks a year after it’s manufacturing date. 

If this machine had worked right out of the box, I would have been happy to not take the machine apart, but the general lack of online information on this snow machine, and the flawed design pushed me to make this. The machine I received was manufactured in June 2019 and was in okay shape. All the external screw heads were rusted, and there was still a little fluid in the line. This leads me to believe the machine was outside, only for one season, and was only moderately looked after. 

After first plugging in the machine, I was not able to get the machine to work at all, I later learned this is because of its low fluid sensor. When the internal blue and red LEDs are flashing, this means the machine thinks it has no fluid, and will refuse to start. The way this sensor works is by detecting light passing through the tube, so when a bubble is in the sensor, the reflection/refraction of the light causes it to trigger the low fluid shutoff. This poses a problem when the machine is not primed, since sometimes it will not even attempt to prime itself. The solution I found is to hold the manual on button as you are turning on the machine. This causes the pump to start and prime before the machine has a chance to detect there is a bubble in the line. 

![Back of Machine](/assets/images/snow_back.jpg)

This was not the only Issue I had though. Once the machine was able to start pumping, the blower motor was clearly not turning on. All It was doing was pumping fluid into the sock with no air coming out. There is a switch on the back of the machine for “Min” and “Max” blower speeds. This switch felt stuck and mushy, and did not seem to be working, so I suspected that to be my issue. I ultimately decided to open the machine and see if I could diagnose the issue rather than immediately return it 

Disassembly of the machine is very straightforward. All the screws are Phillips head, and most are M4 thread. The screws are a cheap steel, and the ones on mine were all rusted, which shouldn’t cause any issues besides aesthetics though. The machine is also very clearly rated for indoor use only, but something to keep in mind if it will be in a humid environment. I opted to replace most of the screws with stainless steel hex screws, so that is what you will see in most of my pictures. 


![front fluid dispenser](/assets/images/snow_sock_removed.jpg)

![fluid dispenser detailed](/assets/images/snow_bubbler.jpg)

First, I took off the sock to reveal the sintered bronze “filter” that is used to dispense the fluid into the airstream. This is a neat little device with the push-to-connect fitting integrated into the body. I wonder if this improves fluid dispersion compared to just ending the tube in the airstream, like the machine in bigclive’s video above. 

![Machine with metal cover removed](/assets/images/snow_top_off.jpg)

The machine opens and does not have much to it. Every part is metal, thanks to the case being clearly a reused fog machine platform, which would need to have the higher heat tolerances. I pulled out the switch, which I initially thought had black silicone on it, but was just the switch housing being melted. (unfortunately, I did not take a good picture of this before misplacing the switch, but you can see the melted plastic on the rightmost terminal).  This was very concerning considering the machine is fused, and the fuse should blow before any other component fails. I checked the fuse and it was properly rated for what was printed on the machine (The fuse holder also includes a second replaceable fuse, big plus!). The melted switch on my machine was a 10A @125V SPDT rocker switch. All this switch does is route the electricity going to the blower through a resistor or not to change the speed of the motor. 

![Melted Speed Switch](/assets/images/snow_melted_switch.jpg)

I bypassed this switch and the blower turned on as expected and seemed to be working perfect with no burning smell or weird sounds. I was still worried about what caused the switch to melt though so I decided to open the blower casing and inspect the motor.

![Snow blower Enclosure](/assets/images/snow_blower_enclosure.jpg)

![Snow blower Motor](/assets/images/snow_motor.jpg)

It was immediately obvious what the problem was, the blower motor was rated for 1400W or ~12.7A @110V. This means the switch was grossly underrated for the current that it was switching! I do not know if this is a design mistake by Chauvet DJ, or their manufacturer swapped in an inferior part without them knowing, but this is a serious flaw for the product to ship like this. Because my unit was used, it is conceivable though that the previous owner put in this underrated switch (however I find this highly unlikely). I also later saw the Amazon reviews for the product, and it seems at least [one other person has had issues with the blower switch](https://www.amazon.com/CHAUVET-DJ-Snow-Machine-SM250/dp/B01KHQLTB0) at the time of writing. Note: This motor is rated for 50Hz use, however this should not be a problem as this is a [brushed universal motor](https://en.wikipedia.org/wiki/Universal_motor) and should not majorly be impacted by 60Hz power in the US. 

To fix the issue I sourced a new [15A @125V switch from DigiKey](https://www.digikey.com/product-detail/en/e-switch/R1966CBLKBLKFF/R1966CBLKBLKFF-ND/1805110) and I would suggest anyone with issues or an improper switch to pick one of these up. It is a drop-in replacement with no soldering required, and just 3 spade terminals that are easy to pull off and put back on. The only tricky part is pushing out the original switch as it is a tight press fit. But with a little persuasion it should come out. 

I was also able to find a source for the blower motor. It is just a standard off-the-shelf vacuum cleaner motor, which is not unexpected. This [product on Alibaba](https://www.alibaba.com/product-detail/Carbon-Brushed-Vacuum-Cleaner-Motor-1400W_60373713336.html) seems to match it perfectly. 

![Snow blower Interior](/assets/images/snow_blower_interior.jpg)

![Snow blower Assembly](/assets/images/snow_blower_halves.jpg)

![Snow blower Housing Detailed](/assets/images/snow_blower_cut.jpg)

Something interesting I found was the design of their blower motor housing. It is two plastic halves with the motor suspended in the middle by a rubber ring. It is a simple but elegant design that should keep the machine quieter by dampening the motor vibrations. The two halves of the housing are identical, but the half for the intake just has its protrusion (which is where the sock attaches on the output) look like it was haphazardly cut off with a reciprocating saw. This is not a huge deal, but it looks very sloppy and creates the potential of bits of plastic getting sucked up by the blower motor. 

![Snow fluid pump](/assets/images/snow_pump.jpg)

The fluid pump also looks to be a standard part, and replacements with the same specifications look to be readily available. The motor is rated for one minute on, and then one minute off, however you can easily set the machine to be continuously on and is not discouraged in the documentation. This could cause the motor to die prematurely, but it is possible Chauvet DJ did the necessary validation to prove this pump is capable of continuous use in this situation. 

![Main PCB](/assets/images/snow_main_PCB.jpg)

The main circuit board is a reuse of a fog machine controller, as indicated by its part number and the unused thermometer connections. The microcontroller is a nuvoton [NUC029LAN](https://www.nuvoton.com/products/microcontrollers/arm-cortex-m0-mcus/nuc029-series/nuc029lan/?__locale=en) ARM microcontroller, and there seems to be adequate isolation on the board. Thankfully, the relay used to switch the blower motor on and off is rated above what is necessary (16A @125V), probably due to it originally needing to switch a high-powered fog machine heater, and they didn’t change it for this design. Being an indoor only product there is no waterproofing of any kind on any of the PCBs. A DIY conformal coating might be a good addition in the future if you are hoping to use this in a high humidity environment. Something good see is the red "glue" affixing all of the inter-PCB connectors to their sockets. This means you're less likely to run into an issue with wires disconnecting due to vibration from operation or shipping.

![Snow Fluid Sensor](/assets/images/snow_fluid_sensor_2.jpg)

![Snow Fluid Sensor](/assets/images/snow_fluid_sensor.jpg)

This is the simple optical sensor that is being used to detect fluid runout. I did not do any probing on this, but I suspect it would be simple to bypass if you were having issues with it. 

I have also included pictures of the DMX and display breakout boards if they are of interest to anyone. 

![Display PCB](/assets/images/snow_display_PCB.jpg)

![DMX PVB](/assets/images/snow_dmx_PCB.jpg)

Overall, I feel confident in the safety of the machine now. It is also nice to know how simple the insides are, allowing me to replace every part that could fail with relative ease. Even designing a new DMX control board would be trivial if it came down to it. I hope this helps anyone on the fence purchasing one of these machines and can help anyone having issues. 

I am still experimenting with DIY snow fluids, as well as the DMX control. I will most likely post an update in the future with a review more from a user’s point of view now that I have the machine up and running perfectly. 