# Using environment variables

To add a custom environment variables, you need to create a ``custom_env.txt`` file in the amethyst folder, and then add the variables into it.

## Commonly used variables

### MESA_GL_VERSION_OVERRIDE 
Used to basically spoof the OpenGL version that Zink reports.    
Example: MESA_GL_VERSION_OVERRIDE=4.6

This can be useful in some cases(this can fix mc 1.17 and newer crashing on mali gpus running Zink), but it can also cause crashes when a mod/shader attempts to use a feature/ext that it think Zink has, but doesn't actually have.   
[More details about this variable can be found here](https://docs.mesa3d.org/envvars.html#envvar-MESA_GL_VERSION_OVERRIDE)

###  MESA_GLSL_VERSION_OVERRIDE
Used to basically spoof the GLSL version that Zink reports.      
Example: MESA_GLSL_VERSION_OVERRIDE=460

[More details about this variable can be found here](https://docs.mesa3d.org/envvars.html#envvar-MESA_GLSL_VERSION_OVERRIDE)
