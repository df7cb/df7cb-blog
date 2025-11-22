---
title: "Setting up a Minecraft server with mods on a remote Linux box"
date: 2025-11-22T23:47:26+01:00
tags:
- notes
---

Information on this is sparse, so here's a few notes in case I need this again:

To use mods on a Minecraft server, a patched server with a mod loader is
required. There are about 4 different ones, but CurseForge seems to be the most
popular one.

Go to https://files.minecraftforge.net/ (redirects to https://files.minecraftforge.net/net/minecraftforge/forge/)
and download the installer for the desired Minecraft version.

Copy that to the server and run

```
java -jar forge-1.21.10-60.1.0-installer.jar --installServer .
```

This creates the directory structure for a Minecraft server. Start it:

```
./run.sh
```

On the first run, it will refuse to run. Edit `eula.txt` and accept the license:

```
eula=true
```

If any mods are desired, copy the .jar files into the `mods/` folder.

Start it again and configure the whitelist:

```
screen ./run
[19:36:07] [main/INFO] [cp.mo.mo.Launcher/MODLAUNCHER]: ModLauncher running: args [--launchTarget, forge_server]
[19:36:07] [main/INFO] [cp.mo.mo.Launcher/MODLAUNCHER]: JVM identified as Debian OpenJDK 64-Bit Server VM 25.0.1+8-Debian-1deb13u1
[19:36:07] [main/INFO] [cp.mo.mo.Launcher/MODLAUNCHER]: ModLauncher 10.2.4 starting: java version 25.0.1 by Debian; OS Linux arch aarch64 version 6.12.48+deb13-arm64
...
> whitelist on
> whitelist add swordfish
> op swordfish
[19:37:55] [Server thread/INFO] [minecraft/MinecraftServer]: Made swordfish a server operator
```

