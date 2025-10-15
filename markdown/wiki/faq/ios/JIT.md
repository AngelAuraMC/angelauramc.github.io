# iOS and "JIT"

## What is JIT and why do I care?
JIT stands for **just-in-time compilation**, and (although not specific to Java), it serves as a method of executing Java code quicker then its alternatives, by compiling *essential instructions* at runtime, rather than its slower alternatives that compile *all* code at runtime repeatedly or writing in a less portable, hardware-level format. It is the fastest™ method to running Minecraft: Java Edition on mobile devices, essentially required for a more pleasant gaming experience.

On Apple's mobile platforms (iOS, iPadOS, and _tvOS*_ in our case), a security feature known as **code-signing** is deeply rooted in the operating system. It serves to verify that applications haven't been tampered with after they were installed by a user, done so that malicious payload cannot be installed after-the-fact by a malicious user(e.g. hackers). However, due to the process in which code-signing works, this prevents JIT from functioning properly as it mainly requires reading code, modifying it, and then executing it in some fashion (whether that be by copying the code to a new location in memory, executing directly, or mirroring it).

(*) - tvOS support coming soon!

## What does this mean for Amethyst?

### Jailbroken devices
Users with Jailbroken devices don't need to worry about JIT requirements, as Amethyst is specially built to detect jailbreaks and automatically enable JIT. This is the preferred installation method.

### Unjailbroken devices
Users with Unjailbroken devices can see two different outcomes, depending on what they used to sideload Amethyst.

#### TrollStore
If you used TrollStore to sideload Amethyst, good news: Amethyst takes advantage of the extended entitlements granted by TrollStore and automatically enables JIT when launched.

Do note, however that you **must** turn on URL Schemes in TrollStore to grant JIT to Amethyst.

#### Normal sideload
If you sideload normally, you will need to enable JIT in some way. Depending on your version of iOS, your method of enabling JIT will differ, due to Apple's changes to their operating systems.

## What are the methods to enable JIT?

Methods to enable JIT for each iOS version can be found [here](https://github.com/C4ndyF1sh/iOS-JIT-Enablers).

Methods not listed are not confirmed nor recommended by us for use with Amethyst.

## So how do I enable JIT?

- [TrollStore](https://ios.cfw.guide/installing-trollstore) (!)

- [SideStore](https://docs.sidestore.io/docs/faq/#can-i-activate-jit) (@)

- [SideJITServer](https://github.com/nythepegasus/SideJITServer) (#)

- [StikDebug](https://apps.apple.com/us/app/stikdebug/id6744045754) (App Store App) ($)

- [JankJIT](https://gist.github.com/JJTech0130/142aee0f7bda9c61a421140d17afbdeb) (%)

(!) - Limited to devices with the CoreTrust bug. (iOS 14.0 - iOS 16.7 RC & iOS 17.0)

(@) - This method is mainly recommended for iOS 16.7.x
- if on iPhone 8/8 Plus/X it is heavily recommended to install Amethyst via Trollstore Lite.

(#) - Does not work for iOS 16.x or below. This method is meant for iOS 17.0.1 - 17.3.1 ONLY.

($) - iOS 17.4+ only, iOS 18.4b1 excluded.

(%) - JankJIT only works on devices running iOS 18.4b1
- if on iPad 7 it is heavily recommended to jailbreak and install Amethyst via TrollStore Lite.
