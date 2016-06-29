
# Nanoshooter — [![Build Status](https://travis-ci.org/ChaseMoskal/Nanoshooter.svg?branch=master)](https://travis-ci.org/ChaseMoskal/Nanoshooter) — [***PLAY NOW***](http://chasemoskal.github.io/Nanoshooter/) — [![Join the chat at https://gitter.im/ChaseMoskal/Nanoshooter](https://badges.gitter.im/ChaseMoskal/Nanoshooter.svg)](https://gitter.im/ChaseMoskal/Nanoshooter?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

***Nanoshooter is a free 3D open source online multiplayer action web game and framework, built on [BabylonJS](http://www.babylonjs.com/).***

The primary goals of the Nanoshooter project are to:
  - Create a robust framework for building 3D online multiplayer action web games on [BabylonJS](https://github.com/BabylonJS/Babylon.js).
  - Make an awesome tank game.

Eventually, the framework that is underneath the Nanoshooter game will move out into its own open source repository, and be given a legendary name that is worthy of a platform on which members the BabylonJS community build their own online multiplayer games with.

Nanoshooter is a revival of our old highschool project. This is familiar territory for us, as we're basically recreating the framework and gameplay functionality that we once had running back in the Blender Game Engine. We want to bring this game to the same level of accomplishment, including a collaborative online map edtior. This time around, years later, we're doing Nanoshooter the right way, at a professional caliber, and running smoothly on the web.

Reading around the web, it looks like most people are trying to use WebSockets and node servers to power their online games. I knew that would never be viable for the level of realtime action we'd need to achieve for a game like this, so I didn't even consider it — until WebRTC came along, and more specifically —

  - [***RTCDataChannel***](https://www.w3.org/TR/webrtc/#rtcdatachannel) — *The Holy Grail of Web Multiplayer*

It's what I've been waiting for all this time, and it's still in the process of descending from the heavens (it's only supported by Chrome and Firefox at the moment). I won't gush about the details for why `RTCDataChannel` is such a beautiful gem *(the `unreliable` transfer functionality is necessary)*, but it really is the key for smooth responsive fast-paced realtime action.

### Help us out!

Are you an aspiring young programmer, eager to contribute to something open source *and* fun? Or maybe you're an ambitious and fully-bearded artist, inspired to unleash your full creativity which the world has been waiting for? Perhaps you have no skills whatsoever, and just want to feel like you're a part of something. *You've definitely come to the right place!*

Say hi in the [***Gitter chat.***](https://gitter.im/ChaseMoskal/Nanoshooter)

## Software you need

  - [**Git**](https://git-scm.com/) — version control, teamwork.

  - [**Node.js**](https://nodejs.org/en/) — development environment runtime (runs build scripts and stuff).

  - **Code editor** — [**Visual Studio Code**](https://code.visualstudio.com/) is the editor of choice for this project. It's an open-source cross-platform full TypeScript IDE, and this project is preconfigured for it.

      - When you install VSCode, you'll definitely want to enable that *Open Code from Right-click Context Menu* option that the installer has. Handy.

  - **Command-line utility**

    - *On Linux/Mac* — just use the Terminal that came with your system.

    - *On Windows* — install [**Cmder**](http://cmder.net/).

      - Also with Cmder, follow [these lame instructions](https://github.com/cmderdev/cmder/wiki/%5BWindows%5D-%22Open-Cmder-Here%22-in-context-menu) to gain the lovely ability to *Open Cmder Here* into any folder from the right-click context menu.

## How to start tinkering with the project

  1. Clone this repo.

  2. Run these commands in the project directory, and run them again every time you pull down new changes *(after every `git pull`):*

    1. `npm install` — install all project dependencies locally (in the project folder, in `node_modules`).

    2. `npm run build` — build all of the project's TypeScript source code.

  3. Run the dev server so you can launch the game locally *(do this whenever you start working):*

    1. `npm run server` — start running the project's internal web server. Hit `CTRL-C` when you want to stop the server process.

    2. Visit [http://localhost:8080/](http://localhost:8080/) to launch the game. I put this dev server on port 8080 because port 80 was giving Lonnie issues (probably firewall related). You can change this port in the `package.json` *(try not to commit it though).*

## Some development notes

  - Art asset paths and filenames must be all lowercase, at least for now, as it seems to be some weird bug or limitation with the Babylon loaders.

  - `npm run watch` — start a compile-on-save process, which will rebuild TypeScript files on the fly as you save changes.

    - You might want to run this watch process in a separate Cmder tab (`CTRL-T` for new tab).

  - [Travis CI will build each commit](https://travis-ci.org/ChaseMoskal/Nanoshooter), and email me when you break the build :P

  - Later on, loading performance will be optimized via Almond module bundling.

## Art viewer mode for previewing any OBJ file

You can preview individual art assets in the Nanoshooter framework, by simply adding their path to the URL after a question mark. This feature, the "Art Viewer" allows you to view any `.obj` file in-game without the need to code up a new corresponding Entity in TypeScript.

So, if the game's link is normally this *(it'll be 'localhost' if you're working locally):*
  - http://chasemoskal.github.io/Nanoshooter/

Activate the Art Viewer by adding a question mark followed by the `.obj` file path:
  - [http://chasemoskal.github.io/Nanoshooter/**?art/tanks/alpha/tank-alpha.obj**](http://chasemoskal.github.io/Nanoshooter/?art/tanks/alpha/tank-alpha.obj)
  - [http://chasemoskal.github.io/Nanoshooter/**?art/tanks/bravo/tank-bravo.obj**](http://chasemoskal.github.io/Nanoshooter/?art/tanks/bravo/tank-bravo.obj)

For now at least, only `.obj` files will be loaded. If the file isn't found, or there's an error loading the file, nothing will appear, and the error will be reported to the javascript developer console (F12). Interestingly, we've discovered that any full URL to a remotely hosted OBJ on the internet will load up fine.

The art viewer might be really handy while working on art assets in Blender. You can point the game at an `.obj` file to preview it, then tweak it in Blender, re-export the `.obj`, and then hit refresh in the browser to see results instantly. You can do this over and over again, no build step required.

## Licensing

**Nanoshooter is an open source project under the MIT License.**

This means:
  - All Nanoshooter collaborator contributions — source code, art assets, and otherwise — are free open source contributions.
  - You are free to reuse any of Nanoshooter's components (any art assets, source code) for your own purposes (commercial or otherwise).
  - You are free to fork the Nanoshooter project, and totally make your own game based on it (commercial or otherwise).

*Note:* Third party libraries are included in the this repository with their own license files.
