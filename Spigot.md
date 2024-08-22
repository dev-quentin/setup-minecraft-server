
# Spigot

# Installation Steps

## Prerequisites

Two applications are required to use BuildTools: Git and Java.

- To install Git, run the following command:
```bash
sudo apt install git
```

- To install Java, run the following command:
```bash
sudo apt install openjdk-8-jdk-headless
```

> [!NOTE]
> If this doesn't work, you can follow the installation steps [here](Java.md).

## BuildTools Installation

Once all the applications are downloaded and installed, it is recommended to create a folder where BuildTools will run. BuildTools works best in an empty directory.

For example, create an empty folder `~/Downloads/BuildTools`.

### Download BuildTools

Go to the [Spigot](https://www.spigotmc.org/wiki/buildtools/) website to download BuildTools.

> [!TIP]
> You can also use `wget` to download the file directly from the terminal.
> Example:
> ```bash
> wget -O BuildTools.jar https://hub.spigotmc.org/jenkins/job/BuildTools/lastSuccessfulBuild/artifact/target/BuildTools.jar
> ```

### Running BuildTools (CLI)

To run `BuildTools.jar` in your terminal, execute the following command:

```bash
java -jar BuildTools.jar
```

> [!IMPORTANT]
> Please note that BuildTools #35 or newer is required; older versions will not work.

The installation may take several minutes. Once finished, retrieve the `spigot-XX.jar` file.

## Configuration

Create a `start.sh` file to run your server.

```bash
echo "java Xmx1024M -Xmx2048M -jar spigot-XX.jar" >> start.sh
sudo chmod a+x start.sh
```

> [!NOTE]
> `-Xms` and `-Xmx` depend on your configuration.
> Example, if you have 4GB of RAM: `-Xms512M -Xmx2048M`.

> [!IMPORTANT]
> It is highly recommended to configure your swap. The size should be at least the size of your RAM + 1GB.
> For example, for 4GB of RAM, your swap should be 5GB.

### Initialization

To initialize your server, run the following command:

```bash
./start.sh
```

You will then get a message asking you to accept the EULA.
To do this, edit the `eula.txt` file and replace `eula=false` with `eula=true`.

## Server Configuration

To configure your server, there are several files to edit:

- server.properties
- spigot.yml
- bukkit.yml

### server.properties

- **network-compression-threshold**

A good starting value: `256`

This allows you to set the maximum size of a packet before the server attempts to compress it. Increasing this can save some CPU resources at the expense of bandwidth, while setting it to -1 disables it. A higher value may also negatively affect clients with slower network connections. If your server is in a network with a proxy or on the same machine (with a ping less than 2ms), disabling this parameter (-1) is beneficial, as internal network speeds can usually handle the extra uncompressed traffic.

- **use-native-transport**

Default value: `true`

Enable this option to optimize network performance if your system supports it.

- **view-distance**

Default value: `10`

This allows you to set the render distance of chunks around players. The higher the value, the more chunks the server has to load. You can reduce this value to lower the server load.

> [!TIP]
> On a Raspberry Pi or low-performance systems, reduce this value to `6` or `8`.

- **simulation-distance**

Default value: `10`

This allows you to set the distance at which entities (mobs, animals, redstone, etc.) continue to behave normally. You can reduce this value to lower the server load.

> [!TIP]
> On a Raspberry Pi or low-performance systems, reduce this value to `6`.

- **max-players**

Default value: `20`

This allows you to set the maximum number of players allowed on the server.

> [!TIP]
> On a Raspberry Pi or low-performance systems, reduce this value to `5` for better performance.

### spigot.yml

- **mob-spawn-range**

A good starting value: `3`

This sets the range at which mobs spawn around players.

- **entity-activation-range**

A good starting value:
```
entity-activation-range:
    animals: 16
    monsters: 24
    raiders: 48
    misc: 8
    water: 8
    villagers: 16
    flying-monsters: 48
```

- **tick-inactive-villagers**

A good starting value: `false`

This option allows villagers to proceed normally and ignore the activation range.

> [!WARNING]
> This may cause issues with iron farms and trade restocking.

- **view-distance**

A good starting value: `default`

This value overrides the one in the `server.properties` file if not set to default. It is recommended to leave it at default so that simulation and view distance are handled in one place, making management easier.

### bukkit.yml

- **spawn-limits**

A good starting value:
```
spawn-limits:
    monsters: 20
    animals: 5
    water-animals: 2
    water-ambient: 2
    water-underground-creature: 3
    axolotls: 3
    ambient: 1
```

This sets the number of mobs that can spawn, reducing the server load.

- **ticks-per**

```
ticks-per:
    monster-spawns: 10
    animal-spawns: 400
    water-spawns: 400
    water-ambient-spawns: 400
    water-underground-creature-spawns: 400
    axolotl-spawns: 400
    ambient-spawns: 400
```
