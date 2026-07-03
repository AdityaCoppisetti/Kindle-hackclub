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



