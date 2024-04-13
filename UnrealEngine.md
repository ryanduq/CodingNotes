

# UNREAL ENGINE 5

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

[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
```
** SteamDevAppId, 480, is the ID for Steam's sample project Space War.\
https://docs.unrealengine.com/4.26/en-US/ProgrammingAndScripting/Online/Steam/


# Troubleshooting

## Generate Visual Studio project files
Delete /Binaries, /Build, /Intermediate, /Saved folders in project folder.\
Right click on the uproject file and "Generate Visual Studio project files"\
Double click on the uproject file and rebuild missing modules when prompted
