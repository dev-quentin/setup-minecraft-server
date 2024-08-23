
# Fast Chunk Pregenerator

## Installation Steps

### Prerequisites

- Ensure your server is running Spigot or Paper compatible with the plugin.
- Java 8 or higher is recommended for better performance.

### Download JAR

Download the `.jar` file compatible with your version [here](https://www.spigotmc.org/resources/fast-chunk-pregenerator.74429/).  
Once downloaded, place the `.jar` file into the `plugins` folder.

### Configuration (Optional)

Check the `config.yml` file inside the plugin's folder for additional settings (if applicable).

## Running

To start Fast Chunk Pregenerator, launch your server. Once it’s running, you have access to several commands.

To pre-generate chunks, use the following command: 

```bash
/fcp fillvanilla <chunkbuffer> [world]
```

- `<chunkbuffer>`: Sets the number of chunks to be loaded into memory at once. Example: `32`.
- `[world]`: Optional. Specifies the world where the chunks should be generated. Default is the current world.

> [!NOTE]
> It is recommended to set a world border to prevent excessive chunk generation.
> Example:
> ```bash
> /worldborder set 50000
> ```

If you want to stop chunk generation, use the following command:

```bash
/fcp cancel
```

### Logs

Check your server logs to confirm that the chunk generation has started correctly. Look for messages indicating progress, errors, or completion.

## Performance Tips

- Adjust the `<chunkbuffer>` size based on your server's available RAM. A lower value reduces memory usage but may take longer to complete.
- Ensure that your world border is correctly configured to avoid generating unnecessary chunks.
