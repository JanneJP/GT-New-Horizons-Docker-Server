# GT-New-Horizons-Docker-Server

Dockerized GT: New Horizons 2.3.0 server

Using [itzg/minecraft-server](https://github.com/itzg/docker-minecraft-server/blob/master/README.md)

## New server

> Download ```GT_New_Horizons_2.3.0_Server_Java_17-19.zip``` from [Here](http://downloads.gtnewhorizons.com/ServerPacks/)

> Place it into ```./modpacks```

> Create a ```docker-compose.yml``` according to ```example.docker-compose.yml```

> Start the server and wait for the crash

    docker compose up

> Create empty ```run.sh``` in ```./data``` and give it execution rights

    touch run.sh

    chmod +x ./data/run.sh

> Add [FTB-Utilities](https://github.com/GTNewHorizons/FTB-Utilities) and [FTB-Library](https://github.com/GTNewHorizons/FTB-Library) into ```./data/mods``` to enable backups, chunk claiming and loading

> Start the server

    docker compose up

> After the server is up and done loading, bring it down

    docker exec gtnh rcon-cli stop

> Make adjustments to configs in ```./data/configs``` and ```./data/local```

> Start the server

    docker compose up -d

## Migrating an old server

> Follow above steps until creating the ```run.sh``` file

> Migrate over files and directories from the old server directory into ```./data```

## Restoring from a backup

> Backups are stored in ```./data/backups```

> Delete old ```World``` directory and replace with the one from a backup zip

## Useful commands

In-game

```/admin backup start``` to run a manual backup

RCON

```docker exec gtnh rcon-cli stop``` To stop the server gracefully

## Setting up Client

> Download and install [Java 19](https://www.oracle.com/java/technologies/javase/jdk19-archive-downloads.html)

> Download and install [MultiMC](https://multimc.org/#Download) launcher

> Download [GT_New_Horizons_2.3.0__Java_17-19.zip](http://downloads.gtnewhorizons.com/Multi_mc_downloads/GT_New_Horizons_2.3.0__Java_17-19.zip)

> Create new GT New Horizons instance in MultiMC by dragging the zip into the launcher window

> Right click on instance => Edit Instance => Settings

> Check Java Installation => Auto Detect => Pick java 19 64bit

> Check Java Arguments and paste in the following:

    --illegal-access=warn -Djava.security.manager=allow -Dfile.encoding=UTF-8 --add-opens java.base/jdk.internal.loader=ALL-UNNAMED --add-opens java.base/java.net=ALL-UNNAMED --add-opens java.base/java.nio=ALL-UNNAMED --add-opens java.base/java.io=ALL-UNNAMED --add-opens java.base/java.lang=ALL-UNNAMED --add-opens java.base/java.lang.reflect=ALL-UNNAMED --add-opens java.base/java.text=ALL-UNNAMED --add-opens java.base/java.util=ALL-UNNAMED --add-opens java.base/jdk.internal.reflect=ALL-UNNAMED --add-opens java.base/sun.nio.ch=ALL-UNNAMED --add-opens jdk.naming.dns/com.sun.jndi.dns=ALL-UNNAMED,java.naming --add-opens java.desktop/sun.awt.image=ALL-UNNAMED --add-modules jdk.dynalink --add-opens jdk.dynalink/jdk.dynalink.beans=ALL-UNNAMED --add-modules java.sql.rowset --add-opens java.sql.rowset/javax.sql.rowset.serial=ALL-UNNAMED

> Right click on instance => Minecraft Folder

> Download [FTB-Utilities](https://github.com/GTNewHorizons/FTB-Utilities), [FTB-Library](https://github.com/GTNewHorizons/FTB-Library) and [Journeymap Unlimited](https://www.curseforge.com/minecraft/mc-mods/journeymap/download/2367915/file), and place them inside ```./mods```

> Remove journeymap fairplay

> Download [Better Font](https://drive.google.com/u/0/uc?id=1_9W2Bt2vVh3jXTGP7VJu6VNtcE1yCwh-&export=download) and place the zip inside ```./resourcepacks```. Enable in game options