

<img width="818" height="841" alt="image" src="https://github.com/user-attachments/assets/0dfb9538-91c3-44fd-a7a0-d9cd93187e8b" />

<img width="657" height="555" alt="image" src="https://github.com/user-attachments/assets/3dadb2f7-324c-4716-88c1-66b3fbffdd90" />

( this is the custom pcb i designed) 

i absolutely love e ink displays and have been wanting to build my own kindle from a very long time. 
i dont want something thats too fancy or has too much, a simple kindle type design works aswell.
basically what i have in mind is-
- A sd card slot ( for storing all my book pdf's)

  <img width="1152" height="597" alt="image" src="https://github.com/user-attachments/assets/c33b1ea3-31ef-4c09-b252-f68c8623d484" />

- A on/off switch to turn on the device from from off/sleep.
  r
- 2 button - they can choose which books i need to read and then when the book is opened they can be used to turn pages.
- 1 button to select the book.
- a microcontroller 
- a e ink display.
- filament to 3d print case and housing ( my friend has a 3d printer and filament so i will be using that to save costs)
- lipo batteries
- a battery charging module to charge the lipo batteries.
- a micro sd card
 so thasts the components for the kindle.

Before i start plotting i need to answer some questions that i need to answer
this is whats called as 
**PHASE 0**

1) why am i making this?
  this is a device for students and avid readers like me who want a distraction free reading device     with a long battery life and its open sourced.

2) what makes it different from a kindle?
  its fully open sourced hardware and firmware , its extremely repairable , expandable with a microsd card with customizable software and a secondary oled status display for battery , page nuber and reading progress.

 3) display size - 4.2 inch e ink display 
 4) battery life- target of 3 to 6 weeks of normal reading with aggressive deep sleep and infrequent e ink refreshes
 5) linux or bare metal?
    bare metal sice im using an esp32-c3 ( arduino framework with platformIO) this provides much
    lower power consumption and faster startup than linux
6) touchscreen? no physical buttons only for a distraction free reading
experience and improved battery life.

   
here are pictures of the exact components ill be using-


