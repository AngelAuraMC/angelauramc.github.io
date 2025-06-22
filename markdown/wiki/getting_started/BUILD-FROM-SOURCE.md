# Building from source
* Even though it is well-explained, building from source requires skill, internet and time.

* You can try building on Android with [Termux](https://termux.dev), but no support will be included for it.

* It is recommended to clone the Amethyst repository before starting [Setting Up JRE](BUILD_FROM_SOURCE.html#setting-up-jre)

```bash
git clone https://github.com/AngelAuraMC/Amethyst-Android --recurse-submodules
```

## Setting up JRE

* You can download it from [CI Auto Builds](https://github.com/AngelAuraMC/Amethyst-Android/actions) if you don't want to/can't build.

* Source: [AngelAuraMC/angelauramc-openjdk-build](https://github.com/AngelAuraMC/angelauramc-openjdk-build)

### Android

* Clone the git repository of `AngelAuraMC/angelauramc-openjdk-build`

```bash
git clone https://github.com/AngelAuraMC/angelauramc-openjdk-build
```

* Change the directory to the cloned repository

```bash
cd angelauramc-openjdk-build
```

* Download Android NDK r10e from [here](https://github.com/android/ndk/wiki/Unsupported-Downloads#r10e) and place it in this directory with a file explorer. (Can't automatically download because of EULA)

::: **WARNING!!** Do not attempt to build using a newer or older NDK, it will lead to compilation errors.

### iOS

* Get the latest [Xcode](https://developer.apple.com/xcode/) (tested with Xcode 12).

#### Platform and architecture specific environment variables

| Platform | Architecture | Target | Target_JDK |
| --------- | ---------- | ---------- | --------- |
| Android | armv8/aarch64 | aarch64-linux-android | aarch64 |
| Android | armv7/aarch32 | arm-linux-androideabi | arm |
| Android | x86/i686 | i686-linux-android | x86 |
| Android | x86_64/amd64 | x86_64-linux-android | x86_64 |
| iOS/iPadOS | armv8/aarch64 | aarch64-macos-ios | aarch64 |

#### Building JRE (Java Runtime Environment)

<CodeSwitcher :languages="{android:'Android',ios:'iOS'}">
<template v-slot:android>

```android
export BUILD_IOS=0
```

</template>
<template v-slot:ios>

```bash
export BUILD_IOS=1
```

</template>
</CodeSwitcher>

```bash
export BUILD_FREETYPE_VERSION=[2.10.4]
```

::: tip
You can use versions **between 2.6.2 and 2.10.4** but **2.10.4** is preferred.
:::

```bash
export JDK_DEBUG_LEVEL=[release]
```

::: tip
You can use **release**, **fastdebug** and **debug**, but **release** is preferred
:::

```bash
export JVM_VARIANTS=[client]
```

::: tip
 You can use **client** and **server** variants, **Client** is for **aarch32** and **server** is for **other architectures**
:::

(Android only)

```bash
./extractndk.sh
./maketoolchain.sh
```

##### Get CUPS, Freetype and build Freetype

```bash
./getlibs.sh
./buildlibs.sh
```

##### Clone JDK, run once

```bash
./clonejdk.sh
```

##### Configure JDK and build

```bash
./buildjdk.sh
```

::: tip
If no configuration is changed, run `sh makejdkwithoutconfigure.sh` instead
:::

##### Pack the built JDK

```bash
./removejdkdebuginfo.sh
./tarjdk.sh
```

## LWJGL

* Coming soon

## Building the Launcher

### Updating translations

* Updating translations is easier thanks to language list updater scripts

* Just run this command and it'll be automatically updated from Crowdin.

<CodeSwitcher :languages="{win:'Windows',linuxmac:'Linux/MacOS'}">
<template v-slot:win>

```win
scripts\languagelist_updater.bat
```

</template>
<template v-slot:linuxmac>

```linuxmac
chmod +x scripts/languagelist_updater.sh
bash scripts/languagelist_updater.sh
```

</template>
</CodeSwitcher>

### Build GLFW Stub

<CodeSwitcher :languages="{win:'Windows',linuxmac:'Linux/MacOS'}">
<template v-slot:win>

```win
./gradlew :jre_lwjgl3glfw:build
```

</template>
<template v-slot:linuxmac>

```linuxmac
gradle :jre_lwjgl3glfw:build
```

</template>
</CodeSwitcher>

### Build the Launcher

<CodeSwitcher :languages="{win:'Windows',linuxmac:'Linux/MacOS'}">
<template v-slot:win>

```win
./gradlew.bat :app_amethyst:assembleDebug
```

</template>
<template v-slot:linuxmac>

```linuxmac
./gradlew :app_amethyst:assembleDebug
```

</template>
</CodeSwitcher>
