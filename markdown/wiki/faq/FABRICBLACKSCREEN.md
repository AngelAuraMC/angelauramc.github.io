# Indefinite Black screen while launching Fabric 

Launching Fabric sometimes (usually after adding a mod), gets stuck on indefinite black screen. Usually, it occurs due to incompatible mods, missing dependancies or mod version mismatch. Not everyone who is would get this issue though, as on some devices game simply crashes before fully launching.

 To know what mods are causing the issue, check `latestlog.txt` file as it would show you what mod(s) are on incorrect versions, or what mod dependancies are missing and tells you the solution aswell. 

# Notes: 
-This is not always the case and sometimes black screen might be caused due to other reasons aswell. In any case reading logs should help.
- The 'DEPENDANCY_MOD' mentioned below is name of required dependancies that you did not install while MOD_NAME is name of the mod.

The log text should go something like this. 

```[17:10:03] [main/ERROR]: Incompatible mods found!
net.fabricmc.loader.impl.FormattedException: Some of your mods are incompatible with the game or each other!
A potential solution has been determined, this may resolve your problem:
	 - Install 'DEPENDANCY_MOD', any version between [version]- (inclusive) and [version]- (exclusive).
More details:
	 - Mod 'MOD_NAME' (modname) [version] requires any version between [version]- (inclusive) and [version]- (exclusive) of DEPENDANCY_MOD, which is missing!```

