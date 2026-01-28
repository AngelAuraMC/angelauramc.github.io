# Renderers 
Minecraft runs on OpenGL, and mobile devices generally only support OpenGL ES (GLES). And since Minecraft won't run on GLES, we have to use renderers as compatibility layers between OpenGL ES and OpenGL.
> All of the following renderers were tested using the same environment; Minecraft 1.21.4 with Optifine, 8 chunks, running on a Snapdragon 888 at 100% resolution scale, with Fast graphics and smooth lighting.

## Holy GL4ES
- Optimized for performance, Holy GL4ES is the default renderer in PojavLauncher and should be used in almost all scenrarios. 
- Supports OpenGL 2.1 and has shader converting capabilities, thus makes up for about 1/8 of the OpenGL 3.x standard.
- Only works on Minecraft 1.21.4 and below
### A screenshot of Holy GL4ES running Minecraft 1.21.4
![holygl4es](https://cdn.discordapp.com/attachments/1227252213508739195/1433130162626756728/2025-10-29_23.37.50.jpg?ex=690391f9&is=69024079&hm=2cefa1d729231886e6a1574dd835f0781d203c371e1d6db6bbb45c10e4f41344&)

## MobileGlues 
- Fast. Supports shaders and mods that cannot run with GL4ES.
- Supports OpenGL 4.0.
- In video and renderer settings, there's an "Extra Renderer" option where you can change MobileGlues's configurations (eg. Enable ANGLE as ES driver for better performance)


### A screenshot of MobileGlues running Minecraft 1.21.4

## MobileGlues + ANGLE as GLES driver
![mobileglues with angle](https://cdn.discordapp.com/attachments/1227252213508739195/1433130161179459594/2025-10-29_23.44.39.jpg?ex=690391f8&is=69024078&hm=fd6b269f96c07854cd1bf6ea40b3d9cdbd5f22d2b8fe6a86ae2405106898c043&)
## MobileGlues without ANGLE (native)
![mobileglues with native](https://cdn.discordapp.com/attachments/1227252213508739195/1433130161712267345/2025-10-29_23.40.32.jpg?ex=690391f8&is=69024078&hm=8fcbcfc785beda6a70f12fb4bccd5a802439343e4534af0d1a3abcf97682390d&)

## Zink
- Mid/Slow(*). It's only useful for mods that don't run due to missing OpenGL extensions and for running shaders.
- Supports OpenGL 4.5 on Adreno GPUs with Turnip, OpenGL 2.1 on some PowerVR GPUs, and OpenGL 3.1/3.2(*) on Mali GPUs. Adreno GPUs without Turnip
**will** face crashes when using Zink.
- Works on all vanilla versions of Minecraft.

> Zink can be run with Xclipse GPU and supports up to OpenGL 4.6. However, there are some graphical issues (vertex explosion). No fix for now.

> (*) Zink's performance is depends on your device. Though, it could be fast on some scenarios. (eg. decreasing resolution improve zink performance)

> (*) Most Mali GPUs can only run OpenGL 3.1. Notes that 1.17+ might crash on Mali GPU because 1.17+ does not support OpenGL 3.1- anymore. To fix, you must create a custom_env.txt and put "MESA_GL_VERSION_OVERRIDE=<x.x>" enviroment variables into custom_env.txt that you just created. (Join our discord server for further supports about this)

### A screenshot of Zink running Minecraft 1.21.4
![Zink](https://cdn.discordapp.com/attachments/1227252213508739195/1433130162190286928/2025-10-29_23.39.11.jpg?ex=690391f8&is=69024078&hm=6bf907042d2c164303e44ba2219c1f3efe11dbe55e919690cf67e659fff0de00&)
