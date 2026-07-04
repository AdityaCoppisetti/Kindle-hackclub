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


