# Angel Aura Amethyst (Android)

## 1.1.7 (31st July 2026)


- New Features:
  - 26.3-snapshot4+ now runs!
  - LWJGL3ify will now run OOTB (when the GTNH devs fix their side)
    - This is a bit weird as it will change the version of your instance, this is needed to get it to run
  - Physical mouse back and forward buttons should now work! (Although depending on the mouse it can be broken, please open a bug report if your mouse side buttons are wrong)
  -Better loading bar when importing packs (its still crap but its an improvement)

- Changes:
  - SDL bumped to 3.4.12 (I don't know if we had gyro on controllers before but we definitely do now!)
  - Stop forcibly setting people's default controls to the new one (I may have been a bit overzealous)

- Bugfixes:
  - Reworked SDL detection because it used to break if SDL was opened via JNI
  - Actually fix forge not loading #310
  - Fix hotbar taps sometimes not registering if you swap slots using other methods (kb/controllayout) #37
  - Some devices not being able to update because we changed the version string?? (I don't know either, this is not normal android)
  - Recompressed modpack zips taking forever to import

- Known Issues:
  - MobileGlues and Krypton Wrapper will crash on 26.3-snapshot4 and above due to changes in how SDL creates EGL window.
  - Krypton Wrapper does not work on 26.3-snapshot3 and above
  - MobileGlues will crash on 26.3-snapshot3 and above if error filtering is set to Don't ignore
  - SDL Controller integrations currently broken


## 1.1.6 (19th July 2026)


- New Features:
  - New default controls by @rkxspace in #299
  - Show device memory and memory allocation to Minecraft in the log by @Jokypond in #276
  - Versions using SDL (lwjgl3ify and 26.3-snapshot4+) and Touchcontroller will have automatic keyboard popup #69 #279
  - Added -release/-debug to logs by @Jokypond in #301
  - Forward and backward mouse buttons added

- Bugfixes:
  - Remove check against Java 17+ for the "Execute a .jar" option in the launcher by @rock3tsprocket in #288
  - Delete security manager by @Jokypond in #304
  - Fix drop item button incorrectly not bound to q by @rkxspace in #307
  - fix: handle NumberFormatException in mg cache setting by @Yarpopcat08 in #305
  - 26.2+ should now work
  - Used incorrect natives for LWJGL 3.4.1 (not aware of this breaking anything)
  - Crash upon modpack import of packs using no-installer forge versions
  - Incorrect lwjglx jar handling borking some versions of forgemodloader
  - Minimap mods having a yellow tint in MobileGlues
  - Some forge installer versions not working
  - Some forge versions not working
  - Crash if you deleted your default control map
  - Controlify crashing on newer versions
  - Sometimes being logged into Demo.Player if auth server has connection issues

- Removed:
  - SDL switch. It is now automatic!

- Known issues:
  - 26.2+ will only work using Kopper Zink on non-Adreno devices
  - Forward and back buttons on physical mice still won't work
  - If using SDL input, mouse forward and backward side buttons will be reversed


## 1.1.5 (28th May 2026)


- Bugfixes:
  - Fixed artifact classifiers being ignored/deleted by @unilock
  - Fixed Krypton Wrapper crashing on older versions due to invalid `LIBGL_ES` variable set (`1` is dropped)
  - Fixed crash on launch on 26.2-snapshot-4 and above due to `pojavexec` not loading in time for GLFW module init
  - Partially fixed floating window triggering a crash on 26.2-snapshots (26.1.x and below not affected)
    - If ASR is disabled, you will crash if you trigger floating window after Minecraft starts with the Vulkan backend. Starting with floating window will cause no crashes.
    - If ASR is enabled, you will crash if the game ever goes off screen on the Vulkan backend (tabbing out, toggle floating window, minimize floating window, etc,)
    - OpenGL backend is completely free of crashes related to windowing (hopefully)
  - Fixed navigation and status bar appearing when toggling floating window mode off
  - Updated to [MobileGL-Dev/MobileGlues@961777c](https://github.com/MobileGL-Dev/MobileGlues/commit/961777c2f7868a58ba179db22299aa10329e267d) to fix grey screen when using Angelica in 1.7.10
  - Now reads JVM args from version.json instead of ignoring them if no `inheritedFrom` field is found
    - This was a hacky fix for Forge 1.17.1-37.0.12 and below crashing on any launcher that wasn't the official one. Forge 1.17.1-37.0.13 has the fix. This may have been also masking some other crashes so we need more testing. FCL and ZL adapted this as their fix though.
    - The hacky fix stopped LWJGL3ify from reading the JVM args from the JSON properly.
  - Angelica is now properly accounted for in autorenderer selection.
  - High poll rate/hz input devices now work properly (they were glitchy before)
  - Fixed Forge on very old MCJE (older than 1.6.x) and below crashing because one of the packages in `methods_injector_agent` starts with mod_`


## 1.1.4 (21st April 2026)


- Bugfixes:
  - [OpenGL fallback for 26.2-snapshot-x (versions with the new Vulkan backend) should now work properly](https://github.com/AngelAuraMC/Amethyst-Android/pull/248/changes/b86fe17c82f03b0334ead0758f3dff6ebe0be786)
  - [Fixed mods using Veil 3.1.0 or lower crashing on arm/arm64 architectures](https://github.com/AngelAuraMC/Amethyst-Android/pull/248/changes/8bf571735c54df85b40e9ce9cd16ba89a3eadb91)


## 1.1.3 (17th April 2026, 6:28 PM UTC)


- Bugfix:
  - [Fix babric crash](https://github.com/AngelAuraMC/Amethyst-Android/pull/242/changes/c944c8e5b0427b2ca18a062b0dfcc3455b367e31)
  - [Fix some forge versions crashing](https://github.com/AngelAuraMC/Amethyst-Android/pull/242/changes/fe12700fd7aa3cabf90d81229b533212f9c189aa)


## 1.1.2 (17th April 2026, 7:06 AM UTC)


- Bugfix:
  - [[FIXME]regression: Execute .jar non-functional](https://github.com/AngelAuraMC/Amethyst-Android/pull/239)
  - [fix(GLFW): Incorrect logic for gl version select](https://github.com/AngelAuraMC/Amethyst-Android/pull/240)
- Changes:
  - [bump(krypton_wrapper): 0.4.4 to 0.4.5](https://github.com/AngelAuraMC/Amethyst-Android/pull/241)

## Where is 1.1.1?
Gone. Obliterated.


## 1.1.0 (11th April 2026)


- Bugfix:
  - [Incorrect shortname for release variant](https://github.com/AngelAuraMC/Amethyst-Android/pull/221)
  - [Crash when using any mod or modloader that creates early loading screens](https://github.com/AngelAuraMC/Amethyst-Android/pull/225)
  - [Use correct LWJGL version for 26.1+](https://github.com/AngelAuraMC/Amethyst-Android/pull/229)
- QoL:
  - [JREs are now downloadable using the JRE manager. Requires internet. JRE17-21-25 have been removed from the APK.](https://github.com/AngelAuraMC/Amethyst-Android/pull/227)
  - [Sodium switch now also changes settings to maximize performance and compat](https://github.com/AngelAuraMC/Amethyst-Android/pull/226)


## 1.0 (1st April 2026)


- Why is stable only just coming now?

After ages of studying and familiarizing the old codebase, I am happy to announce that I am confident this version of the launcher definitely won't crash the second you launch the game.

- What did we change since the last pojav release?

A lot! So here's a hopefully complete list of it all!

- Launcher Changes:
  - [MRPACK and Curseforge ZIP import support!](https://github.com/AngelAuraMC/Amethyst-Android/pull/155)
    - Now you can have your friends send you the modpack for your letsplay! (I have no friends so I don't use this)
  - [You can type in chat with the custom control buttons!](https://github.com/AngelAuraMC/Amethyst-Android/pull/70)
    - This wasn't a thing before! Now all the people who put a whole keyboard in their control layouts get even more use out of it!
  - [We fixed a bug mojang wouldn't](https://github.com/AngelAuraMC/Amethyst-Android/pull/86)
    - <https://bugs.mojang.com/browse/MCL/issues/MCL-3732>
    - No, this is not fixed mojang. Even [prism had to fix it](https://github.com/PrismLauncher/PrismLauncher/blob/5480ce6b4418819ee0465fd96919167150a07c43/launcher/minecraft/MinecraftInstance.cpp#L1100).
  - [The force close button was added back!](https://github.com/PojavLauncherTeam/PojavLauncher/pull/6823)
    - This was removed for some reason. It's back now!
  - [Demo mode was implemented!](https://github.com/AngelAuraMC/Amethyst-Android/pull/16)
    - [redacted]
- Renderer changes:
  - [Downgraded Zink!](https://github.com/PojavLauncherTeam/PojavLauncher/pull/6752)
    - While this may seem stupid, it was needed so Xclipse and Mali users can actually use zink without their fps going into single digits. Going into future versions would only diminish performance for little gain.
  - [Swapped HolyGL4ES with Krypton Wrapper!](https://github.com/AngelAuraMC/Amethyst-Android/pull/163)
    - More mod compat! At no cost!!
  - [Swapped OSMesa Zink with Kopper Zink!](https://github.com/AngelAuraMC/Amethyst-Android/pull/124)
    - This is basically just a free 2x fps boost. Thanks @Swung0x48 for making it!
  - [Replaced LTW with MobileGlues!](https://github.com/AngelAuraMC/Amethyst-Android/pull/1)
    - In our testing, Xclipse and Mali users were able to get more stable and higher framerates while Adrenos kept fairly high framerates under MobileGlues. In order to serve everyone as best we can, we swapped the renderers.

- Mod-specific Changes:
  - [TouchController Integration!](https://github.com/AngelAuraMC/Amethyst-Android/pull/42) (Thanks @fifth-light!)
    - [fifth-light's mod](https://modrinth.com/mod/touchcontroller) brings bedrock-like touch controls to Java Edition so you don't have to struggle with our janky custom controls UI!
  - [SDL Support!](https://github.com/AngelAuraMC/Amethyst-Android/pull/71)
    - This makes pretty much every relevant mod that has controller support function properly, with controller identification and everything! (Personally would suggest playing Legacy4J or with Controlify)
  - [Neoforge support!](https://github.com/AngelAuraMC/Amethyst-Android/pull/17)
    - It used to just crash. Now we even have a button for it!

- General Fixes:
  - [OpenAL Fixes!](https://github.com/AngelAuraMC/Amethyst-Android/pull/125)
    - This should fix multiple old version mods like PolyPatcher, SoundPhysics, etc.
    - We switched to the `oboe` backend so everyone should be getting even lower audio latency now!
  - [Arcmetica for 1.21+!](https://github.com/AngelAuraMC/Amethyst-Android/pull/23)
    - Our arcmetica implementation broke for 1.21+ due to the swap to Java 21. This is now fixed! Capes galore once more!
  - Herobrine was added

These are all the notable changes. Everything else is a bit too specific to be added here or was just part of supporting newer Minecraft.

Have fun!

# PojavLauncher Android (DISCONTINUED)

## "Gladiolus" release (17th January 2025)


- Fully fixed a bug when 1.21.1+ did not show anything with GL4ES
- Other minor launcher crash fixes
- Technical changes:
- Refactored screen size management for better screen dimension changing support
- Improved ReplayMod support (available by installing the FFMpeg plugin)
- Additions:
- Added new renderer: LTW
   - Supports incomplete OpenGL 3.2, based on OpenGL ES 3.0 (with optional features from 3.1 and 3.2)
   - Allows you to run Sodium, Iris (note that shader support is limited), Immersive Portals (GL_EXT_clip_cull_distance required), Create and most other mods for new versions of the game which previously only worked on Zink
   - Known bugs: colors may not be right in Xaero's map mods.
- Added the new "Quick Settings" menu to the in-game sidebar
   - Allows you to adjust resolution, gesture settings and gyroscope settings while the game is running.
UX changes
- Improved default settings
- Improved download progress display for game installation



## "Foxglove" release (20th June 2024)


- Launcher Features:
  - Support for versions requiring Java 21
Custom profile icons !
  - Login screen improvement
  - small UI changes to keep things consistent
  - better modrinth search results
  - A lot of fixes !
  - Support for 1.6.X assets sounds

- Custom control changes:
  - Better notch handling for notches taller than wider
  - Switch controller support
  - small fixes and improvements

- Input changes:
  - Refactored to make crafting easier than ever !

- Renderer changes:
  - More compatibility with server resource packs. A lot of time has been spent on tricky cases for this feature.
  - small optimizations



## "Edelweiss" Release (27th September 2023)


- New launcher features: 
   - Added automatic Forge/Fabric/Quilt/OptiFine installation
   - Added modpack search and installation from CurseForge or Modrinth
   - Added 1.20.2 support

- New Custom Controls features:
   - Added customizable on-screen joystick
   - Now sub-buttons in "FREE" orientation drawers can be resized independently
   - Now buttons can be configured to be hidden or shown when you are in the game or in a menu.

- Custom Controls changes:  
   - Control button border thickness is now independent from button size
   - The highlight for rounded buttons does not show outside of the button border

- Input changes:
   - Refactored the input system for higher efficiency
 
- Renderer changes: 
   - GL4ES 1.1.4 was replaced with a fork of GL4ES 1.1.5 with fixes and extended shader support
   - Removed the VirGL renderer
   - Re-added Zink renderer (supports Mali-Gx7+, Adreno 6xx, Adreno 7xx)
   - Upgraded LWJGL from 3.2.3 to 3.3.1
   - Added support for VulkanMod (requires patching)



## "Dahlia" GPlay update (28th May 2022)


- New launcher features:
   - Added automatic Forge/Fabric/Quilt/OptiFine installation
   - Added modpack search and installation from CurseForge or Modrinth
   - Added 1.20.2 support
     
- New Custom Controls features:   
   - Added customizable on-screen joystick
   - Now sub-buttons in "FREE" orientation drawers can be resized independently
   - Now buttons can be configured to be hidden or shown when you are in the game or in a menu.
     
- Custom Controls changes:
   - Control button border thickness is now independent from button size
   - The highlight for rounded buttons does not show outside of the button border
 
- Input changes:
   - Refactored the input system for higher efficiency

- Renderer changes: 
   - GL4ES 1.1.4 was replaced with a fork of GL4ES 1.1.5 with fixes and extended shader support
   - Removed the VirGL renderer
   - Re-added Zink renderer (supports Mali-Gx7+, Adreno 6xx, Adreno 7xx)
   - Upgraded LWJGL from 3.2.3 to 3.3.1
   - Added support for VulkanMod (requires patching)



## "Crocus" gplay release (31st August 2021)


- Resolver changes

  - Modified ResConfHack to read resolv data from the Java property
  - Added auto-unpacking of premade resolv.conf and setting the Java property
(Now SRV resolving should work on Java 17 by default)
