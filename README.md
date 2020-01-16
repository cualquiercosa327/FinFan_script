# FinFan (script) #

This project is a remake of the game Final Fantasy.

The object scripts that I originally wrote in C++ are replaced with scripts written in a Lisp-like language that I wrote.

### Summary ###

The repository is split into a game project and two tools. The tools extract resources from the original game and put them in a format usable by the game code.

The game is written in C++ and links with the Allegro library. The tools are written in C#.

Despite Allegro being a cross-platform library, all of the code is built with Visual Studio tools. Feel free to port all of this to other operating systems. Please let me know if you do.

The ExtractNsf project uses the Game Music Emu library.

### Gemini script ###

I originally wrote the functions that handle object interaction events in C++ in the file Game\FinFan\ObjEvents.cpp. These functions were based on the disassembly.

After reading about the Lisp-like scripting systems used by Naughty Dog, I was inspired to implement something similar in this project.

I wrote a compiler and bytecode interpreter for Gemini, a language I wrote that works like Lisp. Then I replaced the C++ functions with Gemini ones that can be found at Tools\ExtractRes\Data\ObjEvents.gem.

Compared to Naughty Dog's tools, the Gemini language aren't as complete. In particular, the integration of the script into the content generation system is missing; and there's limited runtime patching.

But, I did implement a feature that's useful for making complex scenarios: coroutines.

### How do I get set up? ###

The subprojects build with Visual Studio 2010 and depend on the Allegro library (5.2) that is automatically downloaded using Nuget. You’ll also need a copy of the original ROM and NSF for each game.

The remake is divided in two parts: the remade game in the Game folder, and the extractor in the Tools folder. The extractor pulls resources like graphics and data tables out of the original ROM and puts them into a format suitable for the remade game. Build and run the extractor before building and running the remade game.

The extractor takes some arguments. For example:

```
#!cmd

ExtractRes <RomPath> <Function> -nsf <NsfFile> -out <OutputPath>
```

You can build all resources with the all function. Set OutputPath to the path where the remade game will go.

Once the resources are built, build and run the program in the bin folder.

### History ###

Even though I had been interested in remaking the The Legend of Zelda a long time ago, Final Fantasy was the first that I did.

Much of the code is based on [Disch's disassembly](http://www.romhacking.net/documents/401/). I also disassembled other parts, or observed and inferred how they work.

I've enhanced the game to look and feel more like others in the series; in particular the following ways:

* Fades are done by fading in or out of black or white, not with color cycling.
* All menus are different and are easier to use and more informative.
* The user interface of Battle Mode is like in other games in the series.
* I implemented Active Time Battle.
    * You turn it on at build time.
* Treasure chests are shown as open or closed.

### Who do I talk to? ###

This software is written by Aldo Nunez (aldonunez1@gmail.com).

Feel free to reach out to me, if you'd like to learn more about the project.
