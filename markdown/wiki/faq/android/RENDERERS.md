# Renderers <!-- TODO: Add screenshots -->
Minecraft runs on OpenGL, and mobile devices generally only support OpenGL ES (GLES). And since Minecraft won't run on GLES, we have to use renderers as compatibility layers between OpenGL ES and OpenGL.
> All of the following renderers were tested using the same environment; Minecraft 1.21.1 with Optifine, 8 chunks, running on a Snapdragon 888 at 100% resolution scale, with Fast graphics and smooth lighting.

## Holy GL4ES
- Optimized for performance, Holy GL4ES is the default renderer in PojavLauncher and should be used in almost all scenrarios. 
- Supports OpenGL 2.1 and has shader converting capabilities, thus makes up for about 1/8 of the OpenGL 3.x standard.
- Only works on Minecraft 1.21.4 and below
### A screenshot of Holy GL4ES running Minecraft 1.21.4
![holygl4es]()

## MobileGlues 
- Fast. Supports shaders and mods that cannot run with GL4ES.
- Supports OpenGL 4.0.
- In video and renderer settings, there's an "Extra Renderer" option where you can change MobileGlues's configurations (eg. Enable ANGLE as ES driver for better performance)


### A screenshot of MobileGlues running Minecraft 1.21.4
![mobileglues with angle]()
![mobileglues with native]()

## Zink
- Mid/Slow(*). It's only useful for mods that don't run due to missing OpenGL extensions and for running shaders.
- Supports OpenGL 4.5 on Adreno GPUs with Turnip, OpenGL 2.1 on some PowerVR GPUs, and OpenGL 3.1/3.2(*) on Mali GPUs. Adreno GPUs without Turnip
**will** face crashes when using Zink.
- Works on all vanilla versions of Minecraft.

> Zink can be run with Xclipse GPU and supports up to OpenGL 4.6. However, there are some graphical issues (vertex explosion). No fix for now.

> (*) Zink's performance is depends on your device. Though, it could be fast on some scenarios. (eg. decreasing resolution improve zink performance)

> (*) Most Mali GPUs can only run OpenGL 3.1. Notes that 1.17+ might crash on Mali GPU because 1.17+ does not support OpenGL 3.1- anymore. To fix, you must create a custom_env.txt and put "MESA_GL_VERSION_OVERRIDE=<x.x>" enviroment variables into custom_env.txt that you just created. (Join our discord server for further supports about this)

### A screenshot of Zink running Minecraft 1.21.4
![Zink](https://raw.githubusercontent.com/whal-whales/random-imgs-repo-for-stuff/refs/heads/main/2024-09-22_12.38.14.png)
