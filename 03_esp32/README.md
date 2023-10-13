# 03_esp32

## Introduction

In this tutorial, I will show you how to use a Docker Dev Container to develop a program for an ESP32.

See here for documentation on how to use PlatformIO in a Docker container and via the command line: https://docs.platformio.org/en/stable/core/index.html. 

## Installation

Here, I have installed the PlatformIO Command Line (CLI). I used the recommended installation script, which created a virtual environment in `/home/vscode/.platformio/penv``.

To activate the virtual environment, type the following into a terminal:

```console
source /home/vscode/.platformio/penv/bin/activate
```

To deactivate the virtual environment, type the following into a terminal:

```console
deactivate
```

Once the virtual environment is activated, the PlatformIO CLI commands can be used.

## Get boards

Type the following into a terminal to get a list of available boards:

```console
pio boards esp32
```

Afterwards, a list of available boards will be displayed.

## Initialise project

Type the following into a terminal to create a new project in the current directory:

```console
pio project init --board esp32dev
```

Afterwards, a new PlatformIO project will be created. Required build tools will be automatically downloaded.

## Install platforms

Type the following into the terminal to install the appropriate platforms for the board:

```console
pio pkg install --platform atmelavr --platform espressif32
```

Afterwards, the platforms for the ESP32 will be installed. Required build tools will be automatically downloaded.

## Add a source file

Add a file `main.cpp` to the `src/` subdirectory. 

Type the following into `main.cpp`:

```c++
#include <Arduino>

void setup()
{
    Serial.begin(115200);
    delay(100);

    Serial.println("Hello World!");
}

void loop()
{

}
```

## Build project

Type the following into a terminal to build the project:

```console
pio run
```

Afterwards, something similar to the following will be displayed:

```console
...
Building in release mode
Retrieving maximum program size .pio/build/esp32dev/firmware.elf
Checking size .pio/build/esp32dev/firmware.elf
Advanced Memory Usage is available via "PlatformIO Home > Project Inspect"
RAM:   [=         ]   6.4% (used 21068 bytes from 327680 bytes)
Flash: [==        ]  17.7% (used 232577 bytes from 1310720 bytes)
============================== [SUCCESS] Took 71.17 seconds=============================
```

## Credit

Dr Frazer K. Noble
@drfknoble
