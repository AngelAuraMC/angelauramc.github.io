# Installing Java runtimes manually

If you for whatever reason decided to install `app-debug-noruntime` or you want to update for whatever reason, here's how you do it. 

## Nightly.link:
1. Download the latest jre's from these links: [jre8](https://nightly.link/AngelAuraMC/angelauramc-openjdk-build/workflows/build/buildjre8/jre8-pojav.zip), [jre17](https://nightly.link/AngelAuraMC/angelauramc-openjdk-build/workflows/build/buildjre17-21/jre17-pojav.zip),  [jre21](https://nightly.link/AngelAuraMC/angelauramc-openjdk-build/workflows/build/buildjre17-21/jre21-pojav.zip)
2. Extract the zip with your file manager. [ZArchiver](https://play.google.com/store/apps/details?id=ru.zdevs.zarchiver) and [MiXplorer](https://mixplorer.com/) are recommended.
3. Open Amethyst and go to Settings → Java Tweaks → Runtime Manager → Add new, then select the .tar.xz file you just extracted from the zip. 

## Github:
1. Go to the [**angelauramc-openjdk-build**](https://github.com/AngelAuraMC/angelauramc-openjdk-build/actions) repo on GitHub, pick the branch you want (e. g. buildjre8 or buildjre17-21.)
2. Log into GitHub, else you won't be able to download the runtime.
3. Click on the name of the action, then download the `pojav` version of the runtime (e. g. `jre17-pojav`). Do not download jdk, your game might crash with it.
4. Extract the zip with your file manager. [ZArchiver](https://play.google.com/store/apps/details?id=ru.zdevs.zarchiver) and [MiXplorer](https://mixplorer.com/) are recommended.
5. Open Amethyst and go to Settings → Java Tweaks → Runtime Manager → Add new, then select the .tar.xz file you just extracted from the zip. 
