# WHIMC Local Server
A stripped down copy of the WHIMC Server intended to be run locally with or without a database, for more information see [https://whimcproject.web.illinois.edu/downloads/](https://whimcproject.web.illinois.edu/downloads/) 

Download and unpack the ZIP to a directory.

## Prerequisites
This configuration assumes over 16gb of RAM available for the server, adjust the maximums below (Aikar's flags) to match your system capabilities (e.g. change -Xms8G -Xmx16G).

### Java
Java 21 or newer required. We recommend [Java 21 for Windows](https://www.oracle.com/java/technologies/javase/jdk21-archive-downloads.html) or [Azul Java 21 for MacOS](https://www.azul.com/downloads/?version=java-21-lts&package=jdk#zulu)

### MySQL Database
This local server uses **mysql 8.4.x** for the WHIMC plugins, you can use something like [MySQL Community server](https://dev.mysql.com/downloads/mysql/8.4.html) to run the database. Core Protect, WorldGuard and Luckperms are set to use local files so you can remove any plugins with the WHIMC-prefix if you do not wish to have a database. Create a MySQL database table schema with the **whimc-blank.sql** file included in the ZIP. WHIMC plugins will be configured to use the following:
```
host: localhost
port: 3306
database: whimc
username: mc134680
password: mc134680
```

## Launching the Server
Run via that .bat file on Windows:
```
@echo off
title WHIMC Standalone
"C:\Program Files\java\jdk-21\bin\java.exe" -Xms8G -Xmx16G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar paper-1.21.11-132.jar --nogui

PAUSE
```
or command line via MacOS Terminal:
```
/Library/Java/JavaVirtualMachines/zulu-21.jdk/Contents/Home/bin/java -Xms8G -Xmx16G -XX:+UseG1GC -XX:+ParallelRefProcEnabled -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions -XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 -XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 -XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 -XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 -XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem -XX:MaxTenuringThreshold=1 -Dusing.aikars.flags=https://mcflags.emc.gs -Daikars.new.flags=true -jar paper-1.21.11-132.jar --nogui

