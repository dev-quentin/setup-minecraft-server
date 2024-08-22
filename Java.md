
# Java

# Installation Steps

## Update the System

Before installing Java, make sure your system is up to date with the latest package versions.

```bash
sudo apt update
sudo apt upgrade -y
```

## Download Oracle JDK

Go to the [Oracle Java SE](https://www.oracle.com/java/technologies/downloads/) website to download the desired version.

> [!NOTE]
> If you have a Raspberry Pi, download the ARM 64-bit version of Java.

> [!TIP]
> You can also use `wget` to download the file directly from the terminal.
> Example: 
> ```bash
> wget https://download.oracle.com/java/XX/latest/jdk-XX_linux-aarch64_bin.tar.gz
> ```

## Extract the Downloaded File

Extract the downloaded archive into a temporary directory.

```bash
tar -xvzf jdk-XX_linux-aarch64_bin.tar.gz
```

## Configuration

Move the contents of the extracted folder to `/usr/local/` for centralized management of binaries and libraries.

```bash
sudo mv jdk-XX /usr/local/
```

Next, create a symbolic link for the `java` binary in `/usr/local/bin` so that it is easily accessible from any terminal without specifying the full path.

```bash
sudo ln -s /usr/local/jdk-XX/bin/java /usr/local/bin/java
```

> [!NOTE]
> This command makes the `java` binary globally available as a command. You can now use it directly.

### Environment Variables

Although the symbolic link makes Java accessible, it's often useful to define the `JAVA_HOME` variable.

```bash
export JAVA_HOME=/usr/local/jdk-21
export PATH=$JAVA_HOME/bin:$PATH
```

Then, reload the configuration file with:
```bash
source ~/.bashrc
```

## Verify the Installation

To verify that Java is correctly installed and that version 21 is used by default, run the following command:

```bash
java -version
```

> [!NOTE]
> This should display something similar to:
> ```
> java version "XX"
> Java(TM) SE Runtime Environment (build XX+XX-XXXX)
> Java HotSpot(TM) 64-Bit Server VM (build XX+XX-XXXX, mixed mode)
> ```
