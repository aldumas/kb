1. The built-in console (show with an empty project).
2. Args debug output.
3. Labels and meaning of the point wrt alignment. Default alignment is right-aligned, and the point is the top-left of the bounding box for the text.
4. Defining a scene manager which selects specialized tick functions. e.g. if you game is on the loading screen, your main tick function will tell the scene manager to do a tick, and the scene manager will see that the current scene is the loading screen, so it will call a function like tick_loading to run all the logic for the loading screen.
5. How to require other ruby files.