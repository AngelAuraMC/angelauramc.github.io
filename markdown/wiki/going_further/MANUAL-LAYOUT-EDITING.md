# Advanced Layout Editing
While editing layout in the editor is typically satisfactory, editing your layout in a text editor is an available option.

::: danger Advanced Section
This section contains advanced concepts.
# Support _will not_ be provided if you encounter an issue here.
If you're not looking to edit JSON, design build tools, or do basic arithmetic and/or algebra, please see [Customizing the on-screen controls](../getting_started/CUSTOM-CONTROLS).

Furthermore, while editing the JSON directly on mobile is possible, it is recommended to __use a laptop or desktop PC__ when editing, and an __Android device__ to test.

This document assumes you are using Android.
:::

## Recommended Tooling
###### Help using these tools is not provided.
::: warning External Sources
Proceed with caution when downloading any external files, and be sure to validate sources (and file hashes) when possible.

Caution is also advised when using commands, __if you don't understand it, don't run it.__
:::

### Editors
For text editors, there are many options, however some good ones include:
- Visual Studio Code ([Website](https://vscode.dev/) or [Desktop](https://code.visualstudio.com/) version) - Standard chromium based editor.
- [Kate](https://apps.kde.org/kate/) - Multi-platform QT editor.
- [Vim](https://www.vim.org/) - Advanced terminal (and lesser known GUI) editor.

### CLI Tools
While editing the file, you may find yourself needing additional toolings:
- [Git](https://git-scm.com/) - Versioning tool, useful for tracking changes and reverting to known working configurations.
- [Android Debug Bridge](https://developer.android.com/tools/adb) - Also known as `adb`, allows further control over your Android phone. This is useful for automatically loading the JSON on to your device, changing resolutions, and more.
- [Python](https://www.python.org/) - A well known scripting language, useful for building advanced tooling quickly.
- [Desmos](https://www.desmos.com/calculator) - Useful for calculating curves and diagnosing brain-dead math.

### Helpful Command Dictionary
Transferring your JSON from PC to Amethyst:
```sh
adb push <PATH-TO-JSON> /storage/emulated/0/Android/data/org.angelauramc.amethyst/files/controlmap/<NAME>.json
```

Getting/Changing/Resetting your device's resolution and pixel density:
```sh
# Getting your device's resolution and density:
adb shell wm size
adb shell wm density

# Changing it:
adb shell wm size <H>x<W>
adb shell wm density <dpi>

# Resetting them to your phone's defaults:
adb shell wm size reset
adb shell wm density reset
```

## Editing the JSON
::: warning App Crashes
Crashes can occur when the default controlmap is set to invalid JSON, or if the valid JSON contains invalid expressions. 
:::
Here is where you learn the basics of editing Amethyst's json.

### Button Types
There are three types of buttons in Amethyst: Regular, Joysticks, and Drawers.
All separated as follows:
```json
{
    "mControlDataList": [...], // Normal Buttons
    "mDrawerDataList": [...], // Drawers
    "mJoystickDataList": [...], // Joysticks
    ...
}
```

#### Regular Buttons
Regular buttons are buttons that are not linked, organized, or are unable to be hidden via a drawer button.
They are structured like so, inside of the `mControlDataList` array:
```json
{
    "bgColor": 1291845632, // Background color of button, the set color here is default from Amethyst.
    "cornerRadius": 100.0, // How round the corners are, in precent. Stops rounding at the half-way point of the smallest side.
    "displayInGame": true, // If the button displays in game.
    "displayInMenu": false, // If the button displays in a menu.
    "dynamicX": "0 * ${screen_width}", // Distance from left.
    "dynamicY": " 0 * ${screen_height}", // Distance from top.
    "height": 69.6, // Height of the button in DP.
    "isSwipeable": false, // If the button can be activated by swiping from another.
    "isToggle": false, // If the button is held down on tap, and released on second tap.
    "keycodes": [
    32,
    0,
    0,
    0
    ], // List of keycodes
    "name": "Jump", // Displayed name of the button. Also useful in combination with your editor's FIND tool.
    "opacity": 1.0, // How opaque the button as a whole is.
    "passThruEnabled": false, // If a mouse passes through this button.
    "strokeColor": -1, // Border color.
    "strokeWidth": 0.0, // Border width.
    "width": 69.6 // Width of the button in DP.
}
```
::: warning Emojis in Button Names
Emojis in button names have been found to sometimes cause JSON parse errors.
It is not recommended to use them here.
:::

#### Drawer Buttons
Drawer buttons are button groups capable of automatically organizing, showing, and hiding buttons inside of them.
They are useful for putting less used, or less conventional, buttons in to clear up screen space. They are formatted like so, inside of the `mDrawerDataList` array:
```json
{
    "buttonProperties": [...], // Array of regular buttons effected by the drawer. Same as "mControlDataList" but for drawers.
    "orientation": "FREE", // Arrangement and positioning type of the drawer.
    "properties": {...} // Same as Regular Button object.
}
```

#### Joystick Buttons
Joystick buttons are joysticks. The objects are almost identical to regular buttons, but share some differences:
```json
{
    "absolute": false, // If absolute positioning is on.
    "forwardLock": false, // If forward lock is on.
    "cornerRadius": 0.0, // Serves no purpose on joystick.
    "name": "", // No name displays on the joystick, ever.
    ...
}
```

### On-Screen Positioning
::: warning iOS Differences
The iOS version of the app uses a **much stricter parser** than Android.
Simple mistakes such as doubling up signs (ex. "+ +", "- -") might not be a problem on Android, but **will cause evaluation errors on iOS**.
Read your math carefully, keep it clean, and use build scripts when it gets complex.
:::
Button positions are special, they get full support for math equations, along with some substitutions.
Also note that **every button has a position field** named `dynamicX` and `dynamicY`. Some basic examples of positions include:
```
0.5 * ${screen_width}  (From now on, first line in equation block is dynamicX)
0.5 * ${screen_height}  (From now on, second line in equation block is dynamicY)
```
The above places the **top-left** corner of the button in the center of the screen.
To shift 50px to the left, simply add `- 50` to the end of dynamicX:
```
0.5 * ${screen_width} - 50
0.5 * ${screen_height}
```
To instead move 50dp, replace `- 50` with `- px(50)`:
```
0.5 * ${screen_width} - px(50)
0.5 * ${screen_height}
```

### Variables and Supported Operations
| Variable/Operation | Description |
|---|---|
| __BASIC__ | |
| + | Addition. |
| - | Subtraction. |
| * | Multiplication. |
| / | Division. |
| ^ | Power. |
| % | Modulo. |
| __TRIG__ | |
| sin(x) | Sine. |
| cos(x) | Cosine. |
| tan(x) | Tangent. |
| cot(x) | Cotangent. |
| sec(x) | Secant. |
| csc(x) | Cosecant. |
| __INVERSE TRIG__ | |
| asin(x) | Arc sine. |
| acos(x) | Arc cosine. |
| atan(x) | Arc tangent. |
| __HYPERBOLIC__ | |
| sinh(x) | Hyperbolic sine. |
| cosh(x) | Hyperbolic cosine. |
| tanh(x) | Hyperbolic tangent. |
| csch(x) | Hyperbolic cosecant. |
| sech(x) | Hyperbolic secant. |
| coth(x) | Hyperbolic cotangent. |
| __POWER/ROOT__ | |
| sqrt(x) | Square root. |
| cbrt(x) | Cube root. |
| pow(x, y) | x^y |
| __LOG__ | |
| log(x) | Natural logarithm. |
| log10(x) | Log base 10. |
| log2(x) | Log base 2. |
| log1p(x) | log(1 + x) |
| logb(x, y) | ln(y)/ln(x) |
| __EXPO__ | |
| exp(x) | e^x |
| expm1(x) | e^x-1 |
| __ROUNDING/SIGN__ | |
| abs(x) | Absolute value. |
| ceil(x) | Ceiling. |
| floor(x) | Floor. |
| signum(x) | Fake signum. |
| __ANGLE CONVERSION__ | |
| toradian(x) | Degrees to radians. |
| todegree(x) | Radians to degrees. |
| __AMETHYST__ | |
| dp(x) | Pixels to display pixels. |
| px(x) | Display pixels to pixels. |
| ${top} ${left} | Both constant 0. |
| ${right} | Rightmost side of screen, minus button width.|
| ${bottom} | Bottom of screen, minus button height.|
| ${width} | The width of the button (px). |
| ${height} | The height of the button (px). |
| ${screen_width} | Screen width in px. |
| ${screen_height} | Screen height in px. |
| ${margin} | Same as px(2). |
| ${preferred_scale} | User's preferred scale. 100% is 100. |

### Clamping and Conditionals
::: warning Readability Warning
Please use a build script with these. Your brain will thank you. These equations become complicated and unmaintainable after a certain point.
:::
| Type | Equation | Output |
|---|---|---|
| __CLAMPING__ | | |
| min(a, b) | `(a + b - abs(a - b)) / 2` | If A is higher than B, B is returned. |
| max(a, b) | `(a + b + abs(a - b)) / 2` | If A is lower than B, B is returned. |
| clamp(a, b, c) | `(((a + c - abs(a - c)) / 2) + b + abs(((a + c - abs(a - c)) / 2) - b)) / 2` | Clamp A between B and C |
| __CONDITIONALS__ | RETURNS 1 IF TRUE | |
| Less Than | `((((y-x)*1000+1-abs((y-x)*1000-1))/2)+abs(((y-x)*1000+1-abs((y-x)*1000-1))/2))/2` | |
| Greater Than | `((((x-y)*1000+1-abs((x-y)*1000-1))/2)+abs(((x-y)*1000+1-abs((x-y)*1000-1))/2))/2` | |
| Equal | `1-ceil(abs(x-y)/(abs(x-y)+1))` | |
| Not Equal | `ceil(abs(x-y)/(abs(x-y)+1))` | |
| Less Than or Equal | `((((y-x)*1000+1-abs((y-x)*1000-1))/2)+abs(((y-x)*1000+1-abs((y-x)*1000-1))/2))/2+1-ceil(abs(x-y)/(abs(x-y)+1))` | |
| Greater Than or Equal | `((((x-y)*1000+1-abs((x-y)*1000-1))/2)+abs(((x-y)*1000+1-abs((x-y)*1000-1))/2))/2+1-ceil(abs(x-y)/(abs(x-y)+1))` | |

## Going Beyond Far
These documents, and Amethyst, are influenced by the community. That includes you. If you want even more flexability in these controls, consider [contributing](https://github.com/AngelAuraMC) by joining the community (here: [![Discord](https://img.shields.io/discord/724163890803638273.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.gg/5ptqkyZxEy)), or opening a PR.
