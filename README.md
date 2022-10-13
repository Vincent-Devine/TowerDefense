# Project Tower Defense
## Presentation
---------------
Tower defense project for ISART.\
This project aims at recreating a tower defense game in C++ language with Raylib library for the visuals.\
The second goal of this project is to become more familiar with code structuring and math applied to video games and POO.

## How to play
---------------
**In-game** : Drag and drop tower on the enemies's path to prevent them from reaching the end of the path.

**Level Editor** : Select an element at the right of the screen to put it on the map with left click. 
                    Remove elements on the map with right click.
                    Select a theme at the top right of the screen.

**Path Editor** :   Select a path at the bottom right of the screen and use right and left click to add / remove point for enemies's path. A path must begin and finish outside the map.

**Enemy's Wave Editor** : Click on "Add Enemy" to add an enemy in the current wave. Click on the enemy's sprite to change the enemy's type. You can also modify the path it will take and the time before the next enemy's apparition.


                    

## Infomation about the project
---------------
Project start : 11/23/2021\
Project end : 12/17/2021\
Version : 1.0 - GOLD\
Date last version : 12/17/2021\
Development team :
- DEVINE Vincent
- MAZURIE Florestan
- ZALLIO Liam

## Dependencies
---------------
- Raylib

## Building
---------------
### Create an executable
```sh
$ make
```
### Run
```sh
$ ./tower
```
### Clean the project
```sh
$ make clean
```
## Project structure
---------------
```sh
.
├── assets
│   ├── Animations
│   ├── Backgrounds
│   ├── Buttons
│   ├── Enemies
│   ├── Map
│   ├── Menu
│   └── Sounds
│       └── MenuSounds
├── Makefile
├── memoryleak
├── README.md
├── save
├── src
│   ├── gameManager
│   │   ├── gameEnemies.cpp
│   │   ├── gameEnemies.hpp
│   │   ├── gamePlayer.cpp
│   │   ├── gamePlayer.hpp
│   │   ├── gameSounds.cpp
│   │   ├── gameSounds.hpp
│   │   ├── gameTextures.cpp
│   │   ├── gameTextures.hpp
│   │   ├── gameTowerManager.cpp
│   │   ├── gameTowers.cpp
│   │   ├── gameTowers.hpp
│   │   ├── gameWaves.cpp
│   │   └── gameWaves.hpp
│   │
│   ├── gameScenes
│   │   ├── game.cpp
│   │   ├── gameCredits.cpp
│   │   ├── gameCredits.hpp
│   │   ├── gameHowToPlay.cpp
│   │   ├── gameHowToPlay.hpp
│   │   ├── game.hpp
│   │   ├── gameOver.cpp
│   │   ├── gameOver.hpp
│   │   ├── gameSelector.cpp
│   │   ├── gameSelector.hpp
│   │   ├── gameWinner.cpp
│   │   ├── gameWinner.hpp
│   │   ├── menu.cpp
│   │   └── menu.hpp
│   │
│   ├── levelEditor
│   │   ├── levelEditor.cpp
│   │   └── levelEditor.hpp
│   │
│   ├── libs
│   │   ├── myList.hpp
│   │   └── myMathLib.hpp
│   │
│   ├── main.cpp
│   │
│   └── System
│       ├── gameAnimator.cpp
│       ├── gameAnimator.hpp
│       ├── scene.cpp
│       ├── scene.hpp
│       ├── UIElement.cpp
│       └── UIElement.hpp
│
└── third_party
```

## Asset Credits
---------------
- Asset tower : Kenney https://www.kenney.nl/assets/tower-defense-top-down
- Asset sprite and enemy : Pixel Boy https://pixel-boy.itch.io/ninja-adventure-asset-pack 
- Sound : Pixel Boy https://pixel-boy.itch.io/ninja-adventure-asset-pack
- FX : Pixel Boy https://pixel-boy.itch.io/ninja-adventure-asset-pack

## Contact
---------------
mail : f.mazurie@student.isartdigital.com\
mail : l.zallio@student.isartdigital.com\
mail : v.devine@student.isartdigital.com