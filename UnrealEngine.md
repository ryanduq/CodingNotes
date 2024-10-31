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

## Simulating lag
in DefaultEngine.ini, add the following
```
[PacketSimulationSettings]
PktLag = 100
```
Only clients will notice the effects. Can compare lag compensation between listen server and client.\
Ping calcs/code:  \
--UNetConnection::ReadPacketInfo(FBitReader& Reader, bool bHasPacketInfoPayload)\
--APlayerController::UpdatePing(float InPing)\
--APlayerState::UpdatePing(float InPing)

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


## Live coding hotkey: Ctrl-Alt-F11


## UE5 animation trim leaves the first frame in (as the last frame??) when triming around a position
Need to create animation from current pose.


## UE5 project unable to launch game with Ctrl-F5 from VS Studio due to some  debugger error
Open solution explorer, find ../Games/Game, rt click on Game, and select "Set as Startup Project". Now try to launch with Ctrl-F5.


## Level not loading on packaged build?
Make sure it is being packaged at 'Edit/Project Settings/Packaging/List of maps to include in a packaged build'.\
e.g. /Game/Maps/Lobby, /Game/Maps/GameStartupMap


## Need to roll back an altered and unsaved asset?
Right click asset -> Asset Actions -> Reload
