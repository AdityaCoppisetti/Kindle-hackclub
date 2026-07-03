this is the where i will be journaling my kindle build.
so i had basically made the esp32 for the kindle which would control the entire device.
what i want is to have bluetooth and wifi so i can upload the book wirelessly.

i got the idea from my sony a6000 camera, which has this option to wirelessly and it 
truly is neat because my old camera required me to put it into this giagantic docking system in order to transfer pictures which just annoyed me.

i wanted to get my pcb making skills on a better level so i thought about making my own esp32.
i had alot of trouble with my first design. a total of 71 errors.

here is the list of components i have and their respective footprints. 
althought i do suggest that you do go over them once incase i have done something wrong.

this is the PHASE ONE OF DEVELOPMENT.


**PHASE ONE**
here we will decide how it looks
sketches 
front layout
rear layout
button placement
screen bezels 
thickness
materials
colour

and then phase 2 would be to CAD everthing.

<img width="736" height="682" alt="image" src="https://github.com/user-attachments/assets/62ac1667-f3c0-494e-baea-40b48509bac2" />

 a total of 29 components.
i really want to make junkier and more intresting looking pcb in the future.

i got a ton of the capacitors wrong so make sure you dont get that wrong.
their footprint needs to be exactly as what you want, you should use the ss i have attached above.


<img width="589" height="475" alt="image" src="https://github.com/user-attachments/assets/4fea6bc1-e97d-42a4-8e09-8317176a004c" />

this section of the schematic provides power to the board and enables usb communicatoin via the c type port
between the esp32-c3 and the computer youre using. it handles the usb power input and even protekcs the usb data lines from fluctuation 
and wierd electrocstatic discharge.

why am i using that exact usb type c recepticle-
i have a ton of c type wires lying around and no one has those old micro usb( idek what they were called)
lying around.

whats with the pull down resistors? (R1 & R2)
the usb c requires configuration channel (CC) resistors so that the host recognizes the device correctly
( i lowk really wanna give this board a really funky name bahahaha)

why they are needed-
identify the borad as usb device (sink)
allow the usb host to enable the 5v supply
ensure the compatibility regardless of cable orientation.
without these resistors i dont think the usb-c would provide power.

VBUS ( the 5v)
the vbus line carries the incoming 5v from the usb connector.
it supplies the oboard voltage regulator , supplies the usb 5v header pin.
acts as the primary power source when connected to a computer.

i think that the D10ESD protection diode is very very very important
because the usb connector is exposed to the outside world and is susceptible to electrostatic discharge.
it protects the pcb from static electricity.
diverts voltage spikes safely to ground
helps prevent the damage to the esp32 and usb circuitry.


<img width="385" height="42" alt="image" src="https://github.com/user-attachments/assets/2e263a28-3be5-4c03-b36a-82d46eb767db" />

i actually got these wrong when i did it. so thats why im attaching this picture to make sure the D- and the D+ matches.


the U!-USBLC6-2SC6 protection.
the usb D+ and d- lines are sensitive to voltage spikes 
( which is what i was afraid of happening when i got them wrong
( i accidently reversed their wiring , luckily i spotted it before turning it in)
it protects the the usb data lines form the ESD events
preserves signal integrity.
increases long termreliability of the usb interface.

what are ESD events?

ELECTROSTATIC DISCHARGE events are basically when there are sudden,
momentary flows of electric current betweentwo objects at different electrical potentials, 
occuring via contact electrical short or dielectric berakdowns

(AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA)

C1 and the C2 bulk capatitors-
these capacitors stabalize the incoming supply voltage.
reduce oltage ripple
provide transient current during sudden load charges.

the o ohm resistor-
although it behaves like a wire electrically , the o ohm reisistor provides flexibility in the design.
it allows easy isolation of the usb power rail during testing
can be replaces with a ferrite bead for improved EMI FILTERING
simplifies debugging and future hardware revisings.




next i suggest to do would be the LDO

<img width="514" height="377" alt="image" src="https://github.com/user-attachments/assets/95f7a7cc-0eae-4e5b-a459-d4584d822f7a" />

okay so i have a mistake in my design , the AP2112k-3.3 is a 3.3 V regulator but my VOUT is labeled +5v

it looks like the regulator is outputting 5V which it definitely isnt.
ahhh such a silly mistake.


this is how it should look like- 


<img width="737" height="535" alt="image" src="https://github.com/user-attachments/assets/2e09d4e5-63f4-4be3-ae79-665cafbf449c" />

i even wired it properly in the pcb editor.

<img width="737" height="535" alt="image" src="https://github.com/user-attachments/assets/f9912d4f-7ae3-48f9-bba5-f5759723f7ef" />

i dont know how to add images on silkscreen i really wanna bombard the entire pcb with silly images.
silly cat images to be exact. i love cats , someone get me a cat.


okay so about the LDO-

the 3.3V Voltage regulation
the esp32-c3 operaties at 3.3v ( which is why it shouldnt be the +5v like i had done) 
while the USB-c connector supplies 5v, therefore a voltage regulator is required to safely power the microcontroller and the other 3.3V components.

the U2-AP2112k-3.3 Low dropout regulator (LDO)
it converts the incoing 5V usb supply into a stable 3.3V output
this then protects the microcontroller from overvoltage.


the C3 - Input Capacitor
the input capacitor filters the incoming 5V supply before it enters the regulator.
it reduces the voltage ripple from the usb supply 
provides instantaneous current during sudden load changes
prevent unwanted voltage fluctuations


C4 is the output capacitor.
the output capacitor stabalizes the regulators 3.3 V output.
maintains the steady 3.3 v supply
imporoves transient response when the esp32 draws aton of current.
prevents oscillation of the voltage regulator 

thats the LDO.
 oh and here is the pcb 3d view of the ldo

 <img width="744" height="203" alt="image" src="https://github.com/user-attachments/assets/1df750d2-c06d-4969-b5d5-9fa321be0cf3" />


lets now move onto the the boot and reset!!!!
this is for some reason the funnest part for me idek why.

 I LOVE BUTTONS I LOVE ALL OF EM besides those wierd small metal ones i hate em.

 **BOOT and RESET circuit**
 the boot and reset circuit povides a simple method for resetting the esp32-c3
 and placing it into a bootloader mode for firmware programming. proper control of these pins is very important for debugging, software development and recovery.

 Switch one (SW1)
 this is the reset button.

<img width="655" height="454" alt="image" src="https://github.com/user-attachments/assets/d5b6bf6e-161b-42a8-b541-2ac4a345b835" />

 
 the reset button is connected to the En pin ( enable ) of the esp32-c3

 it restarts the microcontroller
 allows the firmware to reboot without disconnecting power
 usefule during firmware development and debugging.
 when the button is pressed the EN pin is pulled LOW resetting the esp32
 realing the button returns the EN pin high , allowing the microcontroller to start executing the      firmware.

 **the R5**
 - 10 kilo ohm pull up resistor- 
 the en pin must remain high during normal operation
 so it holds the en pin at 3.3v during normal operation.
 it prevents the unintended resets caused by the electrical noise.
 ensures reliable startup of the esp32-c3.
 wihtout this resistor the en pin could float causing random or unreliable resets.


**the R6**
100 ohm series resistor 
a small series resistor is placed between the reset circuitry and th EN pin 
it limits transient current during switching
reduces electrical noise on the en line
provides additional protection for the esp32 input
alhtough i do have to say it not always requiered , it imporves the integrity of th signal.


**The C9- 100 nF Capacitor**
the capacitor connected to the EN pin forms a small RC network.
it filters high frequency electrical noise
generated a breif power on delay during startup
improves reset stability and prevents false triggering.
this ensures the esp32-c3 stars reliably whenever power is applied.

boot circuit- the esp32 enters its serial bootloader when the gpio09 is hel low during reset.


NOW ONTO THE BOOOOOOOOT BUTTON!

**the switch 2 ( SW2) which is our boot button.**

the boot push button is connected to the GPIO09
it forces the esp32-c3 into bootloader mode
allows new firmware to be uploaded through usb
provides a manual recovery method if firmware becomes corrupted 
to enter the bootloader mode the boot button is held while the reset button is pressed.


**The R7 10 ohm pull up resistor**
gpio 9 myust normally remain high 
it keeps the boot pin at a logic HIGH during normal operation
prevents accidental entry into bootloader mode.
imporves reliability by eliminating floating inputs.

C10 100 nF Capacitor
a capacitor is connected to the boot pin
reduces electrical noise , it also improves the signal stability during button operation
helps prevent false boot mode detection.

and with that , thats the end of the boot and reset button circuit.

<img width="337" height="570" alt="image" src="https://github.com/user-attachments/assets/1c14e7cd-dfad-440f-a114-a99ee0adb328" />




 and this is how they look in the pcb editor.

 <img width="469" height="131" alt="image" src="https://github.com/user-attachments/assets/bdb96aeb-67c6-4827-af5c-8d00ae0492d4" />

 and then the 3d view , which doesnt really help much but still i love buttons so imma show everything.

 <img width="744" height="203" alt="image" src="https://github.com/user-attachments/assets/75000738-1ec7-4dc6-86b1-5648816a6c7f" />


**now lets get onto the main esp32 core circuit schematic**

<img width="546" height="624" alt="image" src="https://github.com/user-attachments/assets/9ca8adef-324f-44bb-8bf8-0fa48eee14f8" />

the esp32-c3 WROOM 02 module serves as the primary processing unit of the development board
it is responsible for the executing firmware, controlling components , handling the usb and communication and interfacing with the external devices through the gpio pins.
this seectoin of the entire schematic also includes the supporting circuirty required for stanle operantion including power filtering clock generation and signal conditioning.

**U3 esp320c3 wroom - 02**

this the main microcontroller module used in this project
it executes the application firmware 
handles the usb communication and firmware uploading
provides wifi and bluetooth low energy BLE connectivity
controls all the gpio perpherals connected to the development board.

**C5 bulk supply capacitor(4.7uF)**

the esp32 experiences rapid changes in current consumption especially during wireless communication
it stabilizes the 3.3v supply
provides transient current during high power operations
reduces voltage ripple on the power rail


**the C6 decoupling capacitor (100nF)**

the 100nF capacitor is places close to the esp32 power pin
it filters the high frequency electrical noise
provides a local energy reservoir for fast switching currents
improves
power integrity and overall system stability.


**EN pull up resistor (R8)**
the enable pin controls wether the esp32 is running or held in reset.
it hold the en pin high during normal operation
it prevents accidental entry into bootloader mode
works together with the boot push button to enable firmware uploading.


**crystal oscillator (Y1)**
this in my first attempt at the pcb , i didnt place it close enough which was bad. cause it should be AS close to the esp32 module as it can be.

this generates an accurate clock signal 
ensures reliable execution o firmware
supports accurate usb communication
maintains timing accuracy for wireless communication.

**Crystal load capacitors ( c7 and C8)**
the crystal requires external load capacitors to oscillate correctly
it stabilizes the crystal oscillator 
it improves the frequency accuracy
it reduces startup time
it minimizes frequency dirft caused by electrical noise.

SERIES RESISTOR (R4)
a small resistor is placed in the crystal circuit
it contrls oscillator drive strength , it reduces ringing on the crystal signal and it improves oscillator stability when required.
lowk shouldnt i put a 0 ohm resistor instead??

this is the crystal wiring in the schematic editor.

<img width="260" height="304" alt="image" src="https://github.com/user-attachments/assets/97e125a5-fb61-494a-b7e9-6421b47b5127" />

and here is how it looks in the pcb editor 

<img width="461" height="270" alt="image" src="https://github.com/user-attachments/assets/5f92b65e-6f6e-4ccf-8239-fbc3da108958" />

and here is how it looks in the 3d view

<img width="461" height="270" alt="image" src="https://github.com/user-attachments/assets/511a9704-5811-4b3e-92a1-30958dba7892" />

.
.

**USB DATA LINES (USB D+ and USB D-)**

the esp32 includes a native usb full speed controller
it enables the firmware uploading wihtout an external usb to uart converter
it provides usb serial communication
simplifies development by allowing direct programming through usb-c


now onto the gpio layout-

<img width="752" height="520" alt="image" src="https://github.com/user-attachments/assets/f73b8d62-bf37-4141-b511-6b85eb6cd36e" />

THE MOST IMPORTANT THING HERE IS THAT FOR THE J2 , I.E THE LEFT SIDE GPIO PINS I HAVE REVERSED THE SYMBOL IN THE SCHEMATIC. 

so when youre gonna be wiring do this- 



https://github.com/user-attachments/assets/d0f3d229-0610-4695-a153-af34da82ba7c


which is basically pressing r to rotate it cause yk its upside down.



okay so ive used global label to connect it to the main core , which only makes the schematic neater.

the j2 & 3 and expansion headers 
i did the mistake of accidentally putting the wrong footprint with 9 pins. make sure that doesnt happen.

there are also power pins to supply regulated 3.3v and 5v.
there are also ground pins.

here is how it looks like in the pcb editor.

<img width="1067" height="523" alt="image" src="https://github.com/user-attachments/assets/f5a7513f-990d-498d-b5f9-47cb5ca491ae" />

and then in the 3d viewer it looks like this.

<img width="504" height="342" alt="image" src="https://github.com/user-attachments/assets/299f3855-e1a7-40bb-a9a4-e5175256ee5c" />



 ALL OF THIS PUT TOGETHER AND ROUTED LOOKS LIKE THIS- 

 

https://github.com/user-attachments/assets/d6af7f0d-325b-4ab3-99fa-96ceb57c8545



 AND THEN HERE IT IS IN THE 3D VIEWER 

 

https://github.com/user-attachments/assets/1673bee4-c454-4514-89f8-4a8e1b6599c3





here is the documentation for the tp4056 module i made.
if you want to buy one you can ,
i made it on my own to improve my kicad skills and also because i couldnt find the symbol for it.
( i dont think there is one in the library tho)

<img width="480" height="480" alt="image" src="https://github.com/user-attachments/assets/9deb33cb-1887-4cff-8a1f-b0564b8be187" />

so here is the schematic i made -

<img width="952" height="575" alt="image" src="https://github.com/user-attachments/assets/791e2a3c-9704-411a-9059-d460fc154c22" />

why even use the tp4056 module-
the lion batteries cannot be directly charged. we need a proper charging module to charge those batteries. the battery charging module provides a safe and reliable method of charging a single cell lithium ion battery using a usb type c pin.

my schematic consists of three primary sections
1) the usb c power input
2) the MCP73831 battery charging cicuit
3) and the battery connector.

**the usb c power input-**
we dont need any data communication just for power so we are using the power only port.

<img width="569" height="518" alt="image" src="https://github.com/user-attachments/assets/ae5142da-1a66-40c8-9b3c-ac35e4614db2" />

this is the wiring schematic of the usb port. you can use any port you want its upto you,
do rememeber that we will be soldering pogo pins onto the input part of the usb port so that when we make our dock it works. this is how it'll work. 

the usb type c connector serves as the primary power source for the charging circuit. it receives 5v from an external usb charger and supplies it to the battery charging ic.

actually you know what come to think of it how will i wire this to the main esp32 board.

okay okay ill make another version of this module later on let me just explain the schematic rn.

**the J1- usb type c receptacle**
the usb type c receptacle is responsible for delivering power from an external usb source to the charging circuit
it recieves a regulated 5v input (VBUS)
provides a reversible and modern charging interface
supplies power to the mcp73831 charging controller


**the cc1 and cc2 pull down resistors (5.1 kilo ohm)**
the usb type c specification requires configuration channel (cc) resisitors so that the power source 
can correctly identify the connected device.

it identifies the deive as a usb power sink 
requests the default usb power profile
enables the usb power source to provice the 5v supply
supports correct operation regardless of cable orientation.
without these resistors many usb c charges will not enable the vbus output.

THE BATTERY CHARGING CIRCUIT

<img width="620" height="436" alt="image" src="https://github.com/user-attachments/assets/f1ee57be-79b2-4cf1-a91b-d231d6c8f456" />

the battery charging circuit is built is built around the microchip MCP73831 a dedicated single cell lithium lithium ion battery charging controller. the ic automatically manages the charging process using a constand current constant voltage charging algorith to ensure safe and efficient charging.

**U1-MCP7831 Battery charging controller**
the MCP7831 is the central component responsible for charging the lithium ion battery.

it regulated battery charging current 
it performs contant current charging during the initial stage
automatically transitions to constant voltage charging as the battery aproaches full capacity
terminates charging when the battery is fully charged
protects the battery from the overcharging by limiting the charging voltage to 4.2 V


**C1- INPUT CAPACITOR (4.7uF)**
the input capacitor is connected between the usb supply and ground.
this filters noise from the incoming usb supply.
reduces voltage ripple.
improves stability of the charging controller.
supplies instantaneous current during transient load conditions.

**C2- battery output capacitor (4.7 uF)**
the output capacitor is connected across the battery terminals.
it stabilizes the battery voltage during charging.
reduces voltage fluctuations.
improves transient response.
ensures stable operation of the charging controller.


**R1 Programming resistor ( 2 kilo ohm)**
the charging current of the mcp73831 is determined by the resistor connected to the RPOG pin
it sets the maximum charging current.
controls charging speed.
it prevents excessive charging current that could damage the battery.

A 2 kilo ohm resistor configures the charging contrller for an aproximate 500mA charging current.
making it suitable for charging to medium capacity lithium ion cells while maintaining battery life.

**D1 Charging status led**
this idicates when battery chargin is in progress
provides visual feedback during charging
simplifies debugging and testing
during the charging the STAT pin pulls low , illuminating the lef once charging is complete the led turns off automatically

**Current limiting resistor**
a resistor is connected in series with the status led.
it limits the led current, it protects both the led and the STAT output.
It ensures safe and reliable operation of the status indicator.

**BATTERY CONNECTOR**
the battery connector provides the electrical interface between the charging circuit and the lithium ion battery.

<img width="279" height="433" alt="image" src="https://github.com/user-attachments/assets/a3c7b59d-145b-4b10-aa9d-c3a734c9c636" />


**J3 battery connector-**
a two pin connector is used to connect a single cell rechargable lithium ion battery.
it connects the battery to the charging circuit 
it supplies charging current from the MCP73831
delivers stored enegery to the rest of the system during battery powered operation.


the tp4056 module looks somehting like this in the pcb editor ( do keep in mind that this is the version 1, i will be making improvements if i can)

<img width="609" height="782" alt="image" src="https://github.com/user-attachments/assets/c2c9fce8-a4d3-4466-83f7-60784dba8c19" />


and the 3d view looks like this -

<img width="609" height="782" alt="image" src="https://github.com/user-attachments/assets/ead22138-e9e2-4dc7-b6ef-7df7072fd035" />

i initially did have trouble when i made this w the routing but my skills were below par.

oh and here are the footprints of the components i forgot to add

<img width="705" height="257" alt="image" src="https://github.com/user-attachments/assets/be1b8293-b2f6-493e-8bbd-4624a2f5334a" />








