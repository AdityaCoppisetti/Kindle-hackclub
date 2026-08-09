

<img width="818" height="841" alt="image" src="https://github.com/user-attachments/assets/0dfb9538-91c3-44fd-a7a0-d9cd93187e8b" />

<img width="657" height="555" alt="image" src="https://github.com/user-attachments/assets/3dadb2f7-324c-4716-88c1-66b3fbffdd90" />

( this is the custom pcb i designed) 

i absolutely love e ink displays and have been wanting to build my own kindle from a very long time. 
i dont want something thats too fancy or has too much, a simple kindle type design works aswell.
basically what i have in mind is-
- A sd card slot  and  a micro sd card ( for storing all my book pdf's)

  <img width="1043" height="482" alt="image" src="https://github.com/user-attachments/assets/c39b6c55-e1bf-4e1a-a43f-0afdcf744fac" />


  <img width="1152" height="597" alt="image" src="https://github.com/user-attachments/assets/c33b1ea3-31ef-4c09-b252-f68c8623d484" />

- A on/off switch to turn on the device from from off/sleep.
  
  <img width="1000" height="516" alt="image" src="https://github.com/user-attachments/assets/f97240ee-c292-4b36-b9de-bea42163a23b" />

- 2 button - they can choose which books i need to read and then when the book is opened they can be used to turn pages.
  
  <img width="1144" height="680" alt="image" src="https://github.com/user-attachments/assets/984768fe-8dc8-4986-84a9-df819cc179d9" />

- 1 button to select the book.
  using the same button above
- a microcontroller
  
  <img width="1181" height="625" alt="image" src="https://github.com/user-attachments/assets/e9aa8078-4e3b-4f5b-8cbb-f393aa396fdd" />

- a e ink display.
  i was going to use the 7 inch one but i prefer the 4.2 inch one

<img width="1190" height="540" alt="image" src="https://github.com/user-attachments/assets/0cb6f9ad-9de6-481b-b6a8-80b2e9baeda9" />

this one comes with the drivers

- filament to 3d print case and housing ( my friend has a 3d printer and filament so i will be using that to save costs)
  gonna be using PLA i think 
- lipo batteries
  ,gonna be using these ones because they are cheap and in a pack of 2
  
  <img width="1108" height="572" alt="image" src="https://github.com/user-attachments/assets/3d63c309-1455-4815-b0cc-b0234ee8c704" />

- a battery charging module to charge the lipo batteries.
  You could use the tp4056 module and its just plug and play but i wanted to learn kicad further so i made my own module.
  i made this lil board-

  <img width="733" height="628" alt="image" src="https://github.com/user-attachments/assets/8eb1670f-0074-44c7-9c3a-6c6f2d42172b" />


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


