i absolutely love e ink displays and have been wanting to build my own kindle from a very long time. 
i dont want something thats too fancy or has too much, a simple kindle type design works aswell.
basically what i have in mind is-
- A sd card slot ( for storing all my book pdf's)
- A on/off switch to turn on the device from from off/sleep.
- 2 buttons that are multifunctional, i.e - they can choose which books i need to read and then when the book is opened they can be used to turn pages.
- 1 button to select the book.
- a microcontroller as the motherboard
- a e ink display.
- filament to 3d print case and housing ( my friend has a 3d printer and filament so i will be using that to save costs)
- lipo batteries
- a battery charging module to charge the lipo batteries.
- pogo pins ( why? youll find out in a bit)
- a small oled display that tells me the power and then the page number aswell and how much portion of the book ive read.
- a micro sd card
 so thasts the components for the kindle.

Before i start plotting i need to answer some questions that i need to answer
this is whats called as 
**PHASE 0**

1) why am i making this?
  this is a device for students and avid readers like me who want a distraction free reading device     with a long battery life and its open sourced.

2) what makes it different from a kindle?
  its fully open sourced hardware and firmware , its extremely repairable , expandable with a microsd card with customizable software and a secondary oled status display for battery , page nuber and reading progress.

 3) display size - 7.5 inch e ink display ( 640 x 384 resolution)
 4) battery life- target of 3 to 6 weeks of normal reading with aggressive deep sleep and infrequent    e ink refreshes
 5) linux or bare metal?
    bare metal sice im using an esp32-c3 ( arduino framework with platformIO) this provides much
    lower power consumption and faster startup than linux
6) touchscreen? no physical buttons only for a distraction free reading
experience and improved battery life.

   

  


  here are pictures of the exact components ill be using-


this is the sd card module im using (im unsure of the module im using but any one works ig) 
  
<img width="999" height="569" alt="image" src="https://github.com/user-attachments/assets/7984a584-413f-40e7-b1b9-be4d2f1f838c" />



this is the on/off switch that ill be using (4mm SPDT 1P2T Slide Switch) -

.
.
<img width="1083" height="569" alt="image" src="https://github.com/user-attachments/assets/b06e6e28-da33-4172-b64c-b9e8a63c34b6" />



and then this is what i decided to use for the page turning/selecting the book -



<img width="1367" height="587" alt="image" src="https://github.com/user-attachments/assets/b4f8c674-9c7f-4a56-95b4-913423306737" />


ill be using this button for the selecting of the books aswell.


for the motherboard that will handle everything , ill be using the esp32 , you can use any esp32 you want 
but for myself i decided to make my own esp32 , why?
because i wanted to have some progress in learning kicad and i wanted to learn alot more than there is to offer 
and i think stuff like this is one of the best ways to learn. i also wanted my microcontrller to have wifi and bluetooth so i can upload books easily.

so im attaching a pic of a esp32 you could use-

<img width="1103" height="696" alt="image" src="https://github.com/user-attachments/assets/14123a83-7ab5-49d2-a3d7-1579024e795f" />



and then this is my design of the esp32, i had a ton of trouble with making it and i learnt alot , so for that check journal.md




<img width="582" height="806" alt="image" src="https://github.com/user-attachments/assets/64187e6d-bd8b-4766-b64a-fbce08e5f974" />



you dont have to make it so compact as we are using it for a kindle so it can be stretched out, it doesnt really matter. this design was just for my own practice.
also i have a ton of error rn so ill fix my pcb then. 




and as for the e-ink display i found this one on amazon because it had the dsplay driver along w it.


<img width="1036" height="657" alt="image" src="https://github.com/user-attachments/assets/2d74a1b9-9466-4bb2-ae4f-d47a846aeb04" />

i have absolutely no clue why it says "operating system- ios/windows" in the listing its just funny and questionative.

and for the 3d printing filament you can choose anything you want
im going with what my friend has.



for the lipo batteries im going with these ( cause they come in a pack of 2 , no i wont be using 2 batteries , just one is enough)


<img width="1036" height="657" alt="image" src="https://github.com/user-attachments/assets/127973ab-51e4-41b4-8d7d-2153ee950798" />

we cant just connect the lipo batteries with the microcontroller so you have to use the tp4056 module 
but for me once again i needed the practice so i made my own tp4056 module.

<img width="528" height="670" alt="image" src="https://github.com/user-attachments/assets/d48a265d-e4e7-4917-b6c1-befd9146fa7c" />




for more info about this check journal.md


so ill be making a dock later on so for that i thought pogo pins might be a good idea cause ive had the urge to use pogo pins in  my project for a while now.

<img width="1045" height="538" alt="image" src="https://github.com/user-attachments/assets/7820f197-878b-464d-8393-7d061b59aa87" />

you can buy this or you can repurpose some from an old non working wireless airpods case or smth.
i have many lying around.


for the oled display to show the battery percentage and the page number and allat im using this 

<img width="1045" height="538" alt="image" src="https://github.com/user-attachments/assets/858eafe5-640e-467e-8a81-951c65a1b21c" />


i have seen this display 
on a ton of projects and so i wanted to use this and it also doesnt seem to use much power

now im a photographer so i always have sd cards laying around but here is a picture of the type of sd card im using
( micro sd card)

<img width="1065" height="241" alt="image" src="https://github.com/user-attachments/assets/0ec3bd09-99ac-40b1-97c5-7be6368f94b8" />



any sd card works, i suggest you pick one that has a ton of storage so you can store many books.




## Hardware Completed

### ESP32-C3 Motherboard

Designed a reusable ESP32-C3 development platform consisting of:

- USB-C interface
- USB ESD protection
- 3.3 V LDO regulator
- ESP32-C3-WROOM-02
- Crystal oscillator
- Boot and Reset circuitry
- GPIO expansion headers
- Complete PCB layout
- Passed Design Rule Check (DRC)
- Custom KiCad symbol and footprint
- Full engineering documentation

---

### Battery Charging Module

Designed a standalone Lithium-Ion charging module based on the MCP73831.

Features include:

- USB Type-C power input
- USB-C CC configuration resistors
- MCP73831 battery charging IC
- Programmable charging current
- Charge status LED
- Battery connector
- System output connector
- Complete PCB layout
- Full engineering documentation



