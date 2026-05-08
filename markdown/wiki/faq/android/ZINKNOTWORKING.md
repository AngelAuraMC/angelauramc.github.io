# Zink doesn't work
On some devices zink can work but it doesn't. Im such cases this might get it running on your device. It doesn't help on devices which don't fulfill the base Zink requirements.

**/storage/emulated/0/Android/data/org.angelauramc.amethyst/files/custom_env.txt**
	(if this file does not exist, create it)

```
MESA_GL_VERSION_OVERRIDE=4.6
MESA_GLSL_VERSION_OVERRIDE=460
```
