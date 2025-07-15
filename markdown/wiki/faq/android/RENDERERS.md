# Renderers <!-- TODO: Add mobileglues -->
Minecraft runs on OpenGL, and mobile devices generally only support OpenGL ES (GLES). And since Minecraft won't run on GLES, we have to use renderers as compatibility layers between OpenGL ES and OpenGL.
> All of the following renderers were tested using the same environment; Minecraft 1.21.1 with Optifine, 8 chunks, running on a Snapdragon 778g at 80% resolution scale, with Fast graphics and smooth lighting.

## Holy GL4ES
- Optimized for performance, Holy GL4ES is the default renderer in PojavLauncher and should be used in almost all scenrarios. 
- Supports OpenGL 2.1 and has shader converting capabilities, thus makes up for about 1/8 of the OpenGL 3.x standard.
- Only works on version 1.21.4 and below.
### A screenshot of Holy GL4ES running Minecraft 1.21.1
![holygl4es](https://raw.githubusercontent.com/whal-whales/random-imgs-repo-for-stuff/refs/heads/main/2024-09-22_12.32.23.png)

## MobileGlues
- Fast/Mid, faster than ANGLE and a bit slower than GL4ES. Runs on OpenGLES 3.0+ (3.2 is recommended).
- Export OpenGL 4.0 (confirmed by MG Dev).
- Supports some shaders mods and resource packs that won't work with GL4ES/ANGLE
- Only works on version 1.17+

### A screenshot of MobileGlues running Minecraft 1.21.1

## Zink
- Mid. It's only useful for mods that don't run due to missing OpenGL extensions and for running shaders.
- Supports OpenGL 4.5/4.6 on Adreno GPUs with Turnip, and OpenGL 3.1/3.2 on Mali GPUs and Adreno GPUs with proprietary driver(*). Adreno GPUs without Turnip
**will** face crashes when using Zink.
- Works on all vanilla versions of Minecraft.

> (*) 
> * Zink theoretically can run on Adreno GPUs with Qualcomm proprietary driver and it can supports up to 3.2 as same as Mali GPUs.
> * Some Mali GPUs cannot run zink, this was caused by a broken driver. Sadly, there's no solution for this case.

### A screenshot of Zink running Minecraft 1.21.1
![Zink](https://raw.githubusercontent.com/whal-whales/random-imgs-repo-for-stuff/refs/heads/main/2024-09-22_12.38.14.png)
