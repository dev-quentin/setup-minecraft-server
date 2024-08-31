
# Paper

## Installation Steps

### Prerequisites

Two applications are required to use BuildTools: Git and Java.

- To install Git, run the following command:
```bash
sudo apt install git
```

- To install Java, run the following command:
```bash
sudo apt install openjdk-8-jdk-headless
```

> **Note:**  
> If this doesn't work, you can follow the installation steps [here](Java.md).

### Download Paper

Go to the [Paper website](https://papermc.io/downloads/paper) and download your desired version.

### Configuration

Create a `start.sh` file to run your server.

```bash
echo "java -Xms1024M -Xmx2048M -jar paper-XX.jar" >> start.sh
sudo chmod a+x start.sh
```

> **Note:**  
> `-Xms` and `-Xmx` depend on your configuration.  
> For example, if you have 4GB of RAM: `-Xms512M -Xmx2048M`.

> **Important:**  
> It is highly recommended to configure your swap. The size should be at least the size of your RAM + 1GB.  
> For example, for 4GB of RAM, your swap should be 5GB.

### Initialization

To initialize your server, run the following command:

```bash
./start.sh
```

You will receive a message asking you to accept the EULA.  
To do so, edit the `eula.txt` file and change `eula=false` to `eula=true`.

### Server Configuration

To configure your server, there are several files to edit:

- [server.properties](Spigot.md#serverproperties)
- [spigot.yml](Spigot.md#spigotyml)
- [bukkit.yml](Spigot.md#bukkityml)
- paper-world-default.yml

#### paper-world-default.yml

- **delay-chunk-unloads-by**

A good starting value: `10s`

This option allows you to configure how long chunks will stay loaded after a player leaves. This helps avoid constantly loading and unloading the same chunks when a player moves back and forth. Too high values can result in too many chunks being loaded at once. In frequently visited areas, consider keeping the area permanently loaded, as this will be lighter for your server than constantly loading and unloading chunks.

- **max-auto-save-chunks-per-tick**

A good starting value: `8`

This lets you slow down incremental world saving by spreading the task over time for better average performance. If you have more than 20-30 players, you might want to set this higher than 8. If the incremental save doesn't finish in time, Bukkit will automatically save leftover chunks all at once and restart the process.

- **prevent-moving-into-unloaded-chunks**

A good starting value: `true`

When enabled, this prevents players from moving into unloaded chunks, which can cause sync loads that slow down the main thread, leading to lag. The probability of players stumbling into an unloaded chunk increases with a lower view-distance setting.

- **entity-per-chunk-save-limit**

A good starting configuration:
```yaml
entity-per-chunk-save-limit:
    area_effect_cloud: 8
    arrow: 16
    breeze_wind_charge: 8
    dragon_fireball: 3
    egg: 8
    ender_pearl: 8
    experience_bottle: 3
    experience_orb: 16
    eye_of_ender: 8
    fireball: 8
    firework_rocket: 8
    llama_spit: 3
    potion: 8
    shulker_bullet: 8
    small_fireball: 8
    snowball: 8
    spectral_arrow: 16
    trident: 16
    wind_charge: 8
    wither_skull: 4
```

This entry allows you to set limits on how many entities of a specified type can be saved. You should provide a limit for each projectile to avoid issues with large amounts of projectiles being saved, which could cause your server to crash during loading. You can add any entity ID here—see the Minecraft wiki for entity IDs. Please adjust the limits according to your preferences. A suggested value for all projectiles is around 10. You can also add other entities by their type names to this list. This config option is not intended to prevent players from building large mob farms.

### Additional Configuration

Follow the optimization settings provided in this [GitHub repository](https://github.com/YouHaveTrouble/minecraft-optimization).
