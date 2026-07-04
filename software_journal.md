this is where ill be journaling the software side of things.

i am diving and planning how ill be tackling the firmware into phases.

## **PHASE 0**
i need to install-
1) vs code
2) Cmake
3) Cmake tools 
4) sdl2
5) git

this will basically be my firmware development stack. each tool has a different job and together they let me write code, build it and 
simulate my kindle on my computer before i flash it onto my esp32 board.

**the vs code**
- i will use to write c++, browse project files, bebug, run builds , use git, preview errors.

**CMake**
-it is a system generator 
-my project would contain a file called cmakelists.txt which tells it that they are source files , tell it to use sdl, compile everything , create an executable 


instead of manually typing code everytime, 
i would just need to run cmake --buil build

**CMake tool**
- this is a vs code extension
- instead of opening the terminal and typing commands it adds buttons like configure , build run and debug, directly inside vs code which is pretty handy.

  and then the most important of all-

  **SDL2**
  this lets my computer pretend to be my kindle.
  instead of waiting until ive soldered and made everyhting i can just open a window an dpreview my code.


  **GIT**
  git remembers every version of my project.
 - it syncs with github
 - keeps backups
 - experiment safely
 - track every change


## **PHASE 1**
this is building the simulator 
basically i have to learn how everything works which is fun ig.

## **PHASE 2**
this is when ill have to build the ui.
i wont use any book yet ill fake everything.

# ill have to make
- library screen. where all the book will be for selection.
- reader screen, the actual reading , chapters pages and allat.
- menu- return to library, battery and theme

  ## **PHASE 3**
  this where ill be defining the application architecture.
  
  # ill create the following folders
  - shared/
  - app/
  - renderer/
  - books/
  - filesystem/
  - util/


    ## **PHASE 4**
    here ill build functions like
    - drawParagraph()
    - drawheading()
    - drawImage()
    - drawFooter()
    - drawPage()

  i dont think any epub related work will be there , it would just be renedering.

  ## **PHASE 5**

  ill just firgure out how tinyxml2 works
  so that i can read xml files
  and miniz can read zip files.

 it would then be able to read title , author and chapters.

 ## **phase 6**
 XHTML PARSER
 the parser acts like a translator 
 it converts the raw html data into readable output like you would see on a website. 
 wait ill show.

 it takes the code like this-

 
 <img width="265" height="255" alt="image" src="https://github.com/user-attachments/assets/3985660e-ab13-4f32-956a-599f9a15e313" />

 
 and then shows it like this-

 
 <img width="265" height="255" alt="image" src="https://github.com/user-attachments/assets/149ebaa5-8457-482e-9d51-2725390591c5" />

## **PHASE 7**
this is where the kindle becomes a kindle
like suppose take the text -
this is what a kindle is  this is my kindle...

# it 
turns it into this 
