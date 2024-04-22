# UNREAL ENGINE 5


## DL Project Repo
 - Clone proj
 - Will be missing solution(.sln)
 - Generate Visual Studio project files and rebuild missing modules
 - Test by right-clicking uproject and selecting "Launch Game"


## Steam Setup
Enable plugin, Online Subsystem Steam\
In build file, ...Build.cs, add ```"OnlineSubsystemSteam"``` to PublicDependencyModuleNames\
Open Game/Config/DefaultEngine.ini and paste the following at the bottom
```
[/Script/Engine.GameEngine]
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="OnlineSubsystemSteam.SteamNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")

[OnlineSubsystem]
DefaultPlatformService=Steam

[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480
bInitServerOnClient=true

[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
```
** SteamDevAppId, 480, is the ID for Steam's sample project Space War.\
https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/Online/Steam/


## Retargeting
https://www.youtube.com/watch?v=_sLnCqBaElI&t=5s

# Troubleshooting

## Generate Visual Studio project files
Delete /Binaries, /Build, /Intermediate, /Saved folders in project folder. Do the same with plugins (Plugin/Game/..)\
Right click on the uproject file and "Generate Visual Studio project files"\
Double click on the uproject file and rebuild missing modules when prompted

## Which files to delete
The following folders can take up a lot of data and be needed:\
`ProgramData\Epic\EpicGamesLauncher\VaultCache` - downloads from Epic Marketplace\
`...\Documents\Megascans Library\Downloaded\UAssets` - downloads from Quixel Bridge, etc..


## When migrating files, it must be done in the /Content folder.
