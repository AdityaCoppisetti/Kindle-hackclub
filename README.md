hey im dhruv coppisetti and i built my own kindle from scratch using a e ink display and my own custom pcb i designed!
i absolutely love e ink displays and have been wanting to build my own kindle from a very long time. 
i dont want something thats too fancy or has too much, a simple kindle type design works aswell.


i love reading books and with all the travelling that im doing, i havent been able to carry my books and i know i could 
just download books on my phone and read them that way but i am just a sucker for single purpose technology. 
and its just so amazing building your own devices and with the hackclub's macondo program i thought i should make this and so i did. 
before this i havent really made much without using what was in my arduino kit. so in this project, i learnt along the way whatever it took me to make this 
and you can learn aswell from my journal.md in this project , i go over almost everything



<img width="903" height="728" alt="Screenshot From 2026-08-15 14-37-48" src="https://github.com/user-attachments/assets/ec3fd5d3-a5d4-4128-8741-8e710bf4f212" />





<img width="818" height="841" alt="image" src="https://github.com/user-attachments/assets/0dfb9538-91c3-44fd-a7a0-d9cd93187e8b" />

<img width="657" height="555" alt="image" src="https://github.com/user-attachments/assets/3dadb2f7-324c-4716-88c1-66b3fbffdd90" />

( this is the custom pcb i designed) 


Before i start plotting i need to answer some questions that i need to answer

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

   




